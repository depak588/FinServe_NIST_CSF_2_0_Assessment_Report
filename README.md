# NIST CSF 2.0 Cybersecurity Assessment — FinServe India (Fictional)

A portfolio project demonstrating a NIST Cybersecurity Framework (CSF) 2.0 assessment for a fictional FinTech company, from asset inventory and risk register through Current/Target Profiles, gap analysis, framework mapping, and a 90-day remediation roadmap.

> **Disclaimer:** FinServe India Pvt. Ltd. is fictional. This is a scenario-based learning exercise, not a certification or compliance audit. No technical testing was performed, and controls not described in the scenario are not assumed to exist.

## Highlights

| Measure | Result |
|---|---|
| Assets in scope | 9 (7 Critical, 2 High) |
| Risks registered | 5 (3 Critical, 2 High) |
| Security areas assessed | 10 (5 Weak, 5 Partial) |
| Remediation actions | 10 (4 Critical, 4 High, 2 Medium) |
| Remediation timeline | 90 days, in 3 phases |

**Top findings:** missing MFA for administrators and excessive access, irregular vulnerability management, weak segmentation around the customer database, no centralized security monitoring, no incident-response plan, and unverified backup protection.

## Read the Report

**[Full assessment report](report/FinServe_NIST_CSF_2_0_Assessment_Report.md)**

1. Executive Summary
2. Organization Overview
3. Assessment Scope
4. Methodology
5. Asset Inventory
6. Risk Assessment
7. Current Profile
8. Target Profile
9. Gap Analysis
10. NIST CSF 2.0 Mapping
11. Top Security Findings
12. Remediation Roadmap
13. Conclusion

## Repository Structure

```
finserve-nist-csf-2-0-assessment/
├── README.md
├── LICENSE
├── report/
│   └── FinServe_NIST_CSF_2_0_Assessment_Report.md
```

## The Workbook

The Excel workbook is the working data behind the report. Follow the numbered tabs in order:

| Tab | Purpose |
|---|---|
| 00_Read Me | Purpose, scope, assumptions, and risk method |
| 01_Asset Inventory | Nine in-scope assets with criticality |
| 02_Risk Register | Threats, vulnerabilities, and scored risks (formulas calculate score and rating) |
| 03_Current Profile | Current status across 10 security areas |
| 04_Target & Gap | Target state and gap for each area |
| 05_Action Plan | Prioritized remediation with owners and timelines |
| 06_NIST CSF Mapping | Findings mapped to CSF 2.0 Functions, Categories, and Subcategories |
| 07_NIST Functions | Plain-language summary of the six CSF Functions |
| 08_Risk Matrix | Scoring scales and rating bands |

## Methodology

```
Asset Inventory → Threats & Vulnerabilities → Risk Register → Current Profile
→ Target Profile → Gap Analysis → Action Plan → NIST CSF Mapping
```

- **Risk score** = Likelihood (1–3) × Impact (1–4)
- **Ratings:** 1–3 Low, 4–6 Medium, 7–9 High, 10–12 Critical
- **Framework:** NIST CSF 2.0 (February 26, 2024), using the Organizational Profile approach (Current Profile, Target Profile, gap analysis, action plan)

## Skills Demonstrated

- Applying NIST CSF 2.0 Functions, Categories, and Subcategories to real-world findings
- Asset-based risk assessment and risk scoring
- Current/Target Profile development and gap analysis
- Prioritized remediation planning and risk-to-action traceability
- Clear, structured security reporting

## Limitations

- Scenario-based; no interviews, evidence review, or technical testing
- The risk register covers five of nine in-scope assets
- Some Partial/Weak ratings reflect missing evidence rather than confirmed failures

## References

- [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
- [NIST CSF 2.0 Reference Tool](https://csrc.nist.gov/projects/cybersecurity-framework/filters#/csf/filters)

## Author

**Deepak Chaudhary** — [LinkedIn](https://www.linkedin.com/in/depak588/)) 

## License

Released under the [MIT License](LICENSE). Educational use; this fictional assessment is not professional security advice.
