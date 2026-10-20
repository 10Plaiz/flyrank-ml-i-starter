# Graph Report - flyrank-ml-i-starter  (2026-10-20)

## Corpus Check
- Corpus is ~33,766 words - fits in a single context window. You may not need a graph.

## Summary
- 353 nodes · 676 edges · 9 communities (8 shown, 1 thin omitted)
- Extraction: 83% EXTRACTED · 17% INFERRED · 0% AMBIGUOUS · INFERRED: 113 edges (avg confidence: 0.85)
- Token cost: 288,942 input · 0 output

## Community Hubs (Navigation)
- CI Guards & Repo Rules
- Pipeline Design & Leakage
- SEO Research Findings
- Feature Prep & Baseline Scripts
- Signal Audit & Baselines
- Warehouse Data Rules
- PDF Report Builder
- Model Training & Selection
- AI Assistant Workflow

## God Nodes (most connected - your core abstractions)
1. `Dataset and lane guide` - 28 edges
2. `The State of AI-Driven SEO (March 2026)` - 23 edges
3. `ML core foundation framework` - 22 edges
4. `Skills Router (skills/README.md)` - 18 edges
5. `GUIDE.md operating manual` - 17 edges
6. `build_pdf()` - 16 edges
7. `FlyRank Data Skill` - 14 edges
8. `main()` - 12 edges
9. `README.md starter repo front door` - 12 edges
10. `Refresh Opportunity Model Report` - 12 edges

## Surprising Connections (you probably didn't know these)
- `precision@K Evaluation` --semantically_similar_to--> `precision_at_k()`  [INFERRED] [semantically similar]
  skills/building-baselines/SKILL.md → scripts/ml_utils.py
- `Active-Content Feature-Vector Subset` --semantically_similar_to--> `Scored Population Summary`  [INFERRED] [semantically similar]
  docs/flyrank-seo-research-march-2026.pdf → outputs/model_report.md
- `Growth vs Decline Logistic Regression` --semantically_similar_to--> `Model Comparison Table`  [INFERRED] [semantically similar]
  docs/flyrank-seo-research-march-2026.pdf → outputs/model_report.md
- `Content Refresh Playbook` --semantically_similar_to--> `Final Ranked Refresh Queue`  [INFERRED] [semantically similar]
  docs/flyrank-seo-research-march-2026.pdf → outputs/model_report.md
- `Finding 5: Engagement and Visibility Consistency` --semantically_similar_to--> `Top Model Feature Importances`  [INFERRED] [semantically similar]
  docs/flyrank-seo-research-march-2026.pdf → outputs/model_report.md

## Import Cycles
- None detected.

## Hyperedges (group relationships)
- **Decisions encoded in the starter pipeline** — docs_data_dictionary_is_declining_label, claude_population_filter, claude_leakage_boundary, claude_client_holdout_split, claude_random_state_seed, claude_precision_at_50_model_selection [EXTRACTED 1.00]
- **CI guards that keep the repo safe and runnable** — _github_workflows_smoke_test_run_pipeline, _github_workflows_smoke_test_data_leak_check, _github_workflows_smoke_test_notebook_outputs_guard, _github_workflows_smoke_test_paper_url_check, _github_workflows_data_path_smoke_run_notebook_03 [INFERRED 0.85]
- **Internship analysis lanes and freestyle directions** — docs_ml_intern_dataset_and_lane_guide_lane_ranking_signal_analysis, docs_ml_intern_dataset_and_lane_guide_lane_refresh_opportunity_scoring, docs_ml_intern_dataset_and_lane_guide_lane_archetype_clustering, docs_ml_intern_dataset_and_lane_guide_lane_ctr_engagement_scoring, docs_ml_intern_dataset_and_lane_guide_freestyle_ai_referral, docs_ml_intern_dataset_and_lane_guide_freestyle_growth_recovery [EXTRACTED 1.00]
- **Grain Guard for Repeated Context Columns** — skills_querying_big_datasets_skill_grain_guards, skills_writing_data_contracts_skill_verify_with_query, skills_flyrank_flyrank_data_skill_fact_content_query_90d, skills_writing_data_contracts_skill_contract_sections [INFERRED 0.85]
- **Label and Decision Leakage Guard** — skills_flyrank_flyrank_data_skill_label_trap, skills_hunting_leakage_and_validating_skill_label_derived_features, skills_hunting_leakage_and_validating_skill_decision_derived_features, skills_flyrank_flyrank_context_skill_product_flags_are_outputs, skills_writing_data_contracts_skill_field_classification [INFERRED 0.85]
- **Honest Claim Discipline** — skills_writing_honest_claims_skill_claim_ladder, skills_flyrank_flyrank_context_skill_honest_claim_language, work_capstone_report_template_claims_checklist, skills_writing_honest_claims_skill_banned_phrasings [INFERRED 0.85]
- **Stage 04 Evaluate-and-Export Artifacts** — outputs_model_report, outputs_charts_action_mix, outputs_charts_confidence_mix, outputs_charts_top_feature_importance, outputs_charts_top_reason_codes, outputs_charts_trend_distribution, scripts_04_evaluate_and_export [INFERRED 0.95]
- **Refresh Queue Decision-Support Layer** — outputs_model_report_refresh_queue, outputs_model_report_confidence_tiers, outputs_model_report_suggested_actions, outputs_model_report_reason_codes, flyrank_refresh_model_results_final_priority_score [INFERRED 0.85]
- **Refresh-Timing Evidence Behind the Refresh Playbook** — docs_flyrank_seo_research_march_2026_content_performance_curve, docs_flyrank_seo_research_march_2026_freshness_multiplier, docs_flyrank_seo_research_march_2026_age_freshness_matrix, docs_flyrank_seo_research_march_2026_content_refresh_playbook [EXTRACTED 1.00]

## Communities (9 total, 1 thin omitted)

### Community 0 - "CI Guards & Repo Rules"
Cohesion: 0.06
Nodes (37): data-path-smoke workflow, run-notebook-03 job, personalize workflow, point-badges-at-this-copy job, smoke-test workflow, data-leak-check job, Deliverable notebooks must carry outputs check, paper_url.txt format and data-credit check (+29 more)

### Community 1 - "Pipeline Design & Leakage"
Cohesion: 0.06
Nodes (42): Five-stage batch pipeline, dim_clients table, dim_content table, fact_content_daily_performance table, fact_content_query_90d table, is_declining_label target, trend_direction bucket, trend_pct (+34 more)

### Community 2 - "SEO Research Findings"
Cohesion: 0.07
Nodes (42): The State of AI-Driven SEO (March 2026), Active-Content Feature-Vector Subset, Finding 8: Age-Freshness Matrix, Finding 10: Age-Controlled AI Model Cohorts, Finding 6: AI Referral Traffic Signal, Finding 1: Anatomy of Growing Content, Finding 9: Captured Click-Equivalent Value, Finding 3: Click Capture by Position Tier (+34 more)

### Community 3 - "Feature Prep & Baseline Scripts"
Cohesion: 0.12
Nodes (25): Population filter (impressions_90d > 0, age >= 90, dedup content_id), main(), parse_args(), main(), parse_args(), reason_codes(), suggested_action(), confidence_label() (+17 more)

### Community 4 - "Signal Audit & Baselines"
Cohesion: 0.06
Nodes (7): Auditing Signals Skill, Building Baselines Skill, FlyRank Context Skill, Framing ML Problems Skill, Writing Honest Claims Skill, Writing Research Papers Skill, Capstone Report Template

### Community 5 - "Warehouse Data Rules"
Cohesion: 0.06
Nodes (11): FlyRank Data Skill, dim_clients table, dim_content table, fact_content_daily_performance table, fact_content_daily_performance_sample table (final month), fact_content_query_90d table, Warehouse Release (~79M rows, gated Hugging Face), Hunting Leakage and Validating Skill (+3 more)

### Community 6 - "PDF Report Builder"
Cohesion: 0.09
Nodes (17): action_label(), build_pdf(), card_grid(), chunks(), footer(), format_float(), format_int(), format_score() (+9 more)

### Community 7 - "Model Training & Selection"
Cohesion: 0.09
Nodes (15): Client group holdout split, RANDOM_STATE = 42 seed, Ranking metrics (precision@K, recall@K, NDCG, MAP), Statistical confidence of metric differences, Starter model results (baseline P@50 0.240 vs RF 0.740), build_feature_matrix(), build_models(), main() (+7 more)

## Ambiguous Edges - Review These
- `Iterate Mid-Panel, Seal Final Month` → `Iterate on Sample, Finish on Full Table`  [AMBIGUOUS]
  skills/querying-big-datasets/SKILL.md · relation: conceptually_related_to
- `Scored Population Summary` → `Finding 2: Content Performance Curve`  [AMBIGUOUS]
  docs/flyrank-seo-research-march-2026.pdf · relation: conceptually_related_to

## Knowledge Gaps
- **20 isolated node(s):** `Population filter (impressions_90d > 0, age >= 90, dedup content_id)`, `RANDOM_STATE = 42 seed`, `Upstream sync for template copies`, `avg_position 0 means no data`, `dim_content table` (+15 more)
  These have ≤1 connection - possible missing edges or undocumented components. (Counts symbols only; 79 node(s) total have ≤1 connection when file, concept and rationale nodes are included.)
- **1 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Skills Router (skills/README.md)` connect `CI Guards & Repo Rules` to `AI Assistant Workflow`, `Signal Audit & Baselines`, `Warehouse Data Rules`, `Model Training & Selection`?**
  _High betweenness centrality (0.246) - this node is a cross-community bridge._
- **What connects `Population filter (impressions_90d > 0, age >= 90, dedup content_id)`, `RANDOM_STATE = 42 seed`, `Upstream sync for template copies` to the rest of the system?**
  _20 weakly-connected nodes found - possible documentation gaps or missing edges._
- **Should `CI Guards & Repo Rules` be split into smaller, more focused modules?**
  _Cohesion score 0.0573025856044724 - nodes in this community are weakly interconnected._
- **Why does `Five-stage batch pipeline` connect `Pipeline Design & Leakage` to `CI Guards & Repo Rules`, `Feature Prep & Baseline Scripts`, `PDF Report Builder`, `Model Training & Selection`?**
  _High betweenness centrality (0.166) - this node is a cross-community bridge._
- **Should `Pipeline Design & Leakage` be split into smaller, more focused modules?**
  _Cohesion score 0.058069381598793365 - nodes in this community are weakly interconnected._

### Low-confidence Hints
_AMBIGUOUS edges — the extractor was unsure. Verify before acting on these._

- **What is the exact relationship between `Iterate Mid-Panel, Seal Final Month` and `Iterate on Sample, Finish on Full Table`?**
  _Edge tagged AMBIGUOUS (relation: conceptually_related_to) - confidence is low._
- **What is the exact relationship between `Scored Population Summary` and `Finding 2: Content Performance Curve`?**
  _Edge tagged AMBIGUOUS (relation: conceptually_related_to) - confidence is low._