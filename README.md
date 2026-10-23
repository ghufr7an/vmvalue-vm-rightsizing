# VMValue: Transparent, Risk-Aware VM Rightsizing

A rule-based, spreadsheet-first decision-support prototype for reviewing virtual machine (VM) CPU/RAM rightsizing candidates.

> **Status:** technical report on a **synthetic** scenario. Not peer-reviewed. All data is invented, and outputs are modeled cost proxies, not measured savings.

## What it does

Low average utilization alone does not prove a VM is safe to shrink. VMValue keeps four things separate and visible for each VM:

1. **Candidate sizing**: CPU and RAM estimates from stated target utilizations
2. **Evidence score (E1-E4)**: coverage, stability, pressure signals, context
3. **Hard safety gates**: critical workloads, incomplete telemetry, high CPU, pressure, unresolved context
4. **Cost proxy**: an illustrative allocation-cost difference

A VM that passes the gates is a *review candidate*, not an approval to resize.

## Files

| File | Description |
|---|---|
| `VMValue_Technical_Research_Report.pdf` | Full technical report (PDF) |
| `VMValue_Technical_Research_Report.docx` | Editable version of the report |
| `VMValue_Revised_Reproducible_Workbook.xlsx` | Live formulas, synthetic inventory, evidence rubric, assumptions |
| `VMValue_Figures/` | Figures used in the report |

## Key results

- 12 synthetic VMs; gross modeled difference across all rows: **672** cost units/month
- Sum of positive differences across all rows: **678** cost units/month
- Review candidates (pass all gates): **6**, with a gross difference of **525** cost units/month
- A utilization-only rule flags 11 rows (678 units); VMValue holds 5 of them with stated reasons
- Review-candidate total ranges from **450 to 606** units/month across CPU targets 0.6-0.8 and memory targets 0.7-0.9
- Risk-adjusted priority proxy across all rows: 616.80 (a ranking heuristic, not an expected value)

These are arithmetic outputs from synthetic data and are not realized savings.

## Reproducing the demonstration

1. Open the workbook in Excel or LibreOffice and allow formulas to recalculate.
2. Review the `Assumptions` and `VM Inventory` sheets.
3. Change cost rates and targets only when you can justify them.
4. Inspect E1-E4, the evidence score, the confidence label, and the gate status.
5. Rebuild the figures if you change assumptions.
6. Do not describe synthetic values as production observations.

## Limitations

- All VM records and telemetry values are synthetic.
- Thresholds and multipliers are heuristic and uncalibrated.
- Sizing uses only P95 CPU and active memory; it ignores latency, NUMA, reservations, I/O, licensing, and dependencies.
- Candidate sizes can be odd vCPU counts; platform-valid VM shapes are not yet enforced.
- The literature review is selective and novelty is not claimed.
- Any real resize requires workload-owner approval, representative telemetry, rollback planning, and post-change validation.

## Next steps

Validate on public or de-identified VM traces, calibrate thresholds on a held-out split, and compare against threshold-only and platform baselines.

## Citation

Ghufran Shakeel. *Beyond Utilization Thresholds: A Transparent, Risk-Aware Framework for Virtual Machine Rightsizing* (technical report v1.0), 2026.

## License

MIT
