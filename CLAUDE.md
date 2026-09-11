# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Start here: the skill router

Before any task in this repo: **read `skills/README.md`** — it is the router.
Find the task in its table and load exactly **one** skill (plus `skills/flyrank/flyrank-data/SKILL.md`
whenever the task touches the data). Do not load every skill; keep context small.

Ground rules:
- Search the repo before assuming something is missing or not implemented.
- One task per conversation; finish and verify before starting the next.
- Never commit datasets (CI blocks them). Never print private data, client names, or raw queries.
- The intern validates your output — end each task by running the notebook top to bottom.

## Commands

```bash
pip install -r requirements.txt
python scripts/run_all.py          # full pipeline on the bundled sample (~1 min)
```

There is no test suite and no linter. The verification gate is the pipeline itself — `run_all.py`
must exit 0 and produce `outputs/model_results.json`, `outputs/refresh_queue.csv`,
`outputs/model_report.md` (exactly what `.github/workflows/smoke-test.yml` asserts).

Run one stage in isolation — `01`–`04` take argparse path flags that default to the shared
locations, so you can redirect a stage's inputs/outputs without touching the others (`05` takes
no flags and always reads `outputs/`):

```bash
python scripts/01_prepare_features.py --input <csv> --output <csv>    # 02: --input/--output
python scripts/03_train_model.py --features <csv> --results /tmp/my_results.json
# 03: --features --baseline --predictions --results
# 04: --features --baseline --predictions --model-results --queue --report
```

Scripts import `ml_utils` as a top-level module, so run them from the repo root (or with
`scripts/` on `sys.path`); all paths resolve from `ROOT` in `ml_utils.py`, not the cwd.

Executing a notebook headlessly needs `jupyter`/`nbconvert`, which are **not** in
`requirements.txt` — install them separately or run the notebook in Colab (its badges point at
whichever repo copy you are in, rewritten by `.github/workflows/personalize.yml`).

## Architecture

A five-stage batch pipeline. Stages communicate only through files on disk, so any stage can be
re-run alone once its inputs exist:

```
data/raw/content_refresh_anonymized.csv
  01_prepare_features  → data/processed/refresh_feature_vector.csv + feature_metadata.json
  02_baseline_score    → data/processed/baseline_refresh_queue.csv   (hand rule, no model)
  03_train_model       → data/processed/model_predictions.csv + outputs/model_results.json
  04_evaluate_and_export → outputs/refresh_queue.csv, model_report.md, summary.json, charts/*.svg
  05_build_pdf_report  → outputs/flyrank_refresh_model_results.pdf
```

`scripts/ml_utils.py` is the single source of truth the whole pipeline reads from — path
constants, the column groups used for cleaning (`NUMERIC_/CATEGORICAL_COLUMNS`), the model's
feature lists (`MODEL_NUMERIC_FEATURES`, `MODEL_CATEGORICAL_FEATURES`), and shared scoring
helpers (`precision_at_k`, `normalize`, `percentile_rank`) plus a dependency-free SVG bar chart.
**Changing which features the model sees means editing those two lists here, not the trainers.**

Decisions encoded in the pipeline that anything downstream inherits:

- **Label** (`01`): `is_declining_label = trend_direction == "down"` — derived, not observed.
- **Population** (`01`): rows kept only where `impressions_90d > 0 and content_age_days >= 90`,
  deduped on `content_id`. Counts in reports are post-filter.
- **Leakage boundary**: `trend_pct` and `trend_direction` are cleaned and kept in the feature
  vector CSV but deliberately excluded from `MODEL_*_FEATURES` — they are the label. Notebook 02
  demonstrates the failure by re-adding `trend_pct` on purpose. Anything derived from the 30d
  trend pair is in the same family; check `MODEL_*_FEATURES` before adding a feature.
- **Split** (`03`): group holdout by `client_id` (20% of clients), falling back to a stratified
  row split only if there are <5 clients or a fold loses a class. The strategy actually used is
  recorded in `outputs/model_results.json` and the report — never assume, read it.
- **Seed**: `RANDOM_STATE = 42` in `03_train_model.py`, used for the split and every estimator.
- **Model selection** (`03`/`04`): three candidates (logistic regression, decision tree, random
  forest) are compared against the rule baseline and the winner is chosen by **precision@50** —
  a top-of-queue metric, because the deliverable is a ranked review queue, not a classifier.
  Exact numbers drift with library versions; the baseline-vs-model gap is the claim, not the digit.

## Where work goes

- `scripts/` is the **reference pipeline and stays pristine** — it is the baseline reviewers
  compare against. To change it, copy into `work/scripts/` (see `work/README.md`).
- `work/` is the intern's space: `work/notebooks/` holds one pre-named skeleton per assignment
  card (ML-02 → `w01_research_question.ipynb`, … ML-11 → `capstone.ipynb`); the mapping table is
  in `work/README.md`. `notebooks/01–03` are the shared teaching notebooks, filled in place.
- `outputs/` in git holds small *example* artifacts showing the target shape; regenerated CSVs,
  JSONs and the PDF are gitignored. Under `work/`, the opposite: commit `work/outputs/*.json`
  metrics as the receipts your report's numbers trace back to.
- `submission/paper_url.txt` must end up holding exactly one line, the deployed paper URL.

## Guards that will fail the build

`.github/workflows/smoke-test.yml` blocks any committed `.parquet/.zip/.tar/.feather` and any
CSV other than `data/raw/content_refresh_anonymized.csv` and `outputs/refresh_queue_sample.csv`.
It also scans `work/notebooks/*.ipynb`: a notebook with filled code cells but **zero outputs**
warns while the track is in progress and becomes a hard error once `submission/paper_url.txt`
holds a real `https://` URL. Save notebooks executed, with outputs.

Weeks 3+ read the ~79M-row release from `hf://datasets/FlyRank/internship-warehouse` through
DuckDB without downloading it (gated; see `skills/flyrank/flyrank-data/SKILL.md` and notebook 03).
`.github/workflows/data-path-smoke.yml` exercises that path weekly and needs the `HF_TOKEN` secret.

## Language in anything that ships

Results are **observed / measured / directional / decision-support**. No causal claims without a
design, no "predicted Google's algorithm", no client-identifying details — `DATA_USE.md` governs,
and everything in `work/` may become public with the submission.
