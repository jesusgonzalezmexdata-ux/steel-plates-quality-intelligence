# Project state

```text
LAST_COMPLETED_PHASE = 4_CANDIDATES
NEXT_PHASE = 5_CONTROLLED_TUNING
VALIDITY_SCOPE = APS_COMPONENT_FAILURE_CLASSIFICATION
PRIMARY_METRIC = OFFICIAL_COST (FP=10, FN=500)
CV_PROTOCOL = StratifiedKFold(n_splits=5, shuffle=True, random_state=42)
HOLDOUT = official test set, 16,000 rows, SHA256 2cdf6f7661c7b4c63333c93cdec36a3a82350176b604a2312cf82799fb2712f3
HOLDOUT_STATUS = SEALED
HOLDOUT_LABEL_COUNTS_SEEN_AT_INTAKE = TRUE (disclosed; not used for any decision)
HOLDOUT_USED_FOR_DECISIONS = FALSE
POST_HOLDOUT_TUNING = FALSE
```

## Ledger

| Phase | Status | Evidence |
|---|---|---|
| 0 · Repository and licensing | Done | LICENSE (Apache-2.0), NOTICE (data CC BY 4.0 per UCI, GPL-3.0 per file headers) |
| 1 · Data intake and audit | Done | [01](01_data_intake_and_audit.md), [train_audit.json](../reports/audit/train_audit.json), `tests/test_data.py` |
| 2 · Problem contract | Done | [02](02_problem_contract.md) |
| 3 · Baseline and CV protocol | Done | [03](03_baseline.md): logistic regression 52,100 vs 500,000 trivial |
| 4 · Candidates and missingness strategy | Done | [04](04_candidates.md): LightGBM + indicators 34,600 (weak edge, within fold spread) |
| 5 · Controlled tuning and threshold | Next | 12 pre-declared configurations |
| 6 · Single final evaluation | Rules pre-registered | `src/aps_intel/final.py` committed before tuning finished; reservation file blocks re-runs |
| 7 · Errors, uncertainty, cost economics | Pending | — |
| 8 · Model Card, artifacts, release | Pending | — |
