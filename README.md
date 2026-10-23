VMValue — Transparent, Risk-Aware VM Rightsizing Prototype
What this is
VMValue is a spreadsheet-first, rule-based decision-support prototype for documenting candidate VM CPU/RAM rightsizing, evidence sufficiency, hard safety gates, and modeled allocation-cost differences.
Files
`VMValue\_Technical\_Research\_Report.docx` — working technical report.
`VMValue\_Revised\_Reproducible\_Workbook.xlsx` — formulas, synthetic inventory, evidence rubric, gates, and scenario assumptions.
`VMValue\_Figures/` — figures used in the manuscript.
Critical limitations
All twelve VM records and all telemetry/counter values are synthetic. Cost rates are illustrative assumptions. Outputs are not measured savings, production recommendations, a validated optimizer, or evidence of novelty. `Risk-adjusted priority proxy` is a heuristic ranking score, not an expected-value estimate. Any real resize requires workload-owner approval, representative telemetry, platform-specific review, rollback planning, and post-change validation.
Reproducing the demonstration
Open the workbook in Excel or LibreOffice and allow formulas to recalculate.
Review the `Assumptions` and `VM Inventory` sheets.
Change scenario cost rates and targets only when you can justify them.
Inspect E1–E4, final evidence score, confidence label, and hard-gate status.
Rebuild figures from the calculated output if you change assumptions.
Do not describe synthetic values as production observations.
Current illustrative results
Gross modeled difference across all 12 rows: 672 cost units/month.
Positive gross differences across all rows: 678 cost units/month.
Review-candidate gross difference: 525 cost units/month.
Risk-adjusted priority proxy across all rows: 616.80 cost units/month.
These figures are arithmetic outputs from synthetic data and are not realized savings.
Research status
Working technical report; not peer-reviewed. The literature review is selective, novelty is unestablished, and empirical validation is not complete. Read and verify each cited source before formal submission.
Additional synthetic comparisons (see report Sections 5.3-5.4)
A utilization-only rule (P95 CPU < 70% and positive difference) flags 11 rows (678 cost units/month); VMValue marks 6 as review candidates (525) and holds 5 with stated reasons.
Review-candidate total ranges from 450 to 606 cost units/month across CPU targets 0.6-0.8 and memory targets 0.7-0.9.
