# APS failure intelligence: cost-sensitive decisions for Scania trucks

**Work in progress.** Status, phases and integrity invariants are tracked in [docs/PROJECT_STATE.md](docs/PROJECT_STATE.md).

**Question.** Which trucks should go to the workshop for an Air Pressure System check, given that a missed APS failure costs 500 and an unnecessary check costs 10? These are the official costs that Scania published with the data.

| | |
|---|---|
| **Data** | 76,000 real Scania truck records (60,000 training, plus 16,000 in the official test set), 170 anonymised operational features, 1.7 % APS failures ([intake and audit](docs/01_data_intake_and_audit.md)) |
| **Decision** | Flag or do not flag each truck for an APS check |
| **Metric** | Official cost: 10 × false positives + 500 × false negatives ([problem contract](docs/02_problem_contract.md)) |
| **Holdout** | The official test set, sealed in code until a single final evaluation |
| **Reference** | Flag none costs 500,000; flag all costs 590,000 (training scale) |

## Reproduce

```bash
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements-dev.txt
PYTHONPATH=src python -B -m aps_intel.audit
python -B -m pytest -q
```

## License

Code: [Apache-2.0](LICENSE). Data: Scania CV AB via the UCI Machine Learning Repository, [doi:10.24432/C51S51](https://doi.org/10.24432/C51S51). UCI lists CC BY 4.0; the files carry a GPL-3.0 notice. Both are kept, see [NOTICE](NOTICE).

---

**Jesús R. L. González** · Data Scientist · Manufacturing operations and quality
