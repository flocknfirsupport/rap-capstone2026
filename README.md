# Responsible AI Intake & Decision Framework

**Melisa DiPietro | RAP Capstone | June 2026**

---

## The Problem

SMB HR leaders are adopting AI tools faster than they have frameworks to evaluate them. Unlike enterprise organizations with legal and compliance teams, most HR practitioners in small businesses make vendor and deployment decisions alone. Existing AI governance resources assume dedicated staff and enterprise tooling — none of which is present where most Canadian HR work actually happens. This tool fills that gap: a structured, plain-language intake that any HR practitioner can complete before a tool touches a people process.

---

## Responsible AI Lens Applied

The tool addresses five intersecting principles grounded in OPC guidance (2023), the OHRC Human Rights AI Impact Assessment, Ontario ESA Bill 149 (in force January 1, 2026), and NIST AI RMF 1.0:

- **Bias & fairness.** AI trained on historical HR data encodes historical inequities. A formal bias audit is flagged as strongly recommended before any consequential use, citing Obermeyer et al. (2019) and Buolamwini & Gebru (2018).
- **Privacy.** PIPEDA requires informed consent. The tool separates current law (PIPEDA, in force) from proposed regulation (Bill C-27/AIDA, not yet in force as of June 2026).
- **Agency & recourse.** Employees and candidates must be able to contest AI-influenced decisions. No override path is treated as a critical gap.
- **Transparency.** Non-disclosure to affected people is flagged as critical. Written pre-process notice is the minimum standard.
- **Decision power.** Binding AI decisions carry the highest risk weight. The tool distinguishes real human authority from nominal human authority.

---

## Key Design Choices

- **Visible scoring logic.** Risk tier is produced by a weighted algorithm — and the weights are shown to users in a collapsible panel. Hiding the scoring would replicate the opacity the tool is designed to surface in AI products.
- **Employee-facing row.** The summary table includes a line showing what an affected person can access or contest, built from the disclosure and override answers. Most governance tools are written entirely from the organizational perspective.
- **Accessibility question.** Question 8 asks whether the AI tool has been accessibility-tested and whether an accommodation process is documented. The Ontario Human Rights Code applies to all private employers in Ontario including tech startups — the duty to accommodate does not disappear because a vendor's algorithm is making the call.
- **Self-report caveat.** Lower-risk results include "based on your self-reported answers." A clean result reflects what was entered, not what was verified.

---

## Tradeoffs & Open Questions

- **Scoring is heuristic.** Weights are calibrated against OPC, OHRC, and NIST guidance but have not been independently validated against compliance outcomes.
- **Self-report limits.** There is no verification mechanism. A user who wants a clean result can get one.
- **Coverage gaps.** Environmental impact, labor displacement, and francophone workforce considerations are not covered by the eight questions.
- **Legal currency.** Update the file when Bill C-27/AIDA passes. Search "June 2026" to locate all date references.

---

## Picking It Up and Using It

Open `flocknfir-ai-intake.html` in any browser. No install, no login, no data stored. Works offline. To embed in a website, wrap in an `<iframe>`. To share with a client, attach the HTML file directly — it is self-contained at 50kb.

- **Update legal references.** Open in a text editor, search `June 2026` to find all date references. When Bill C-27 passes, change the "proposed" status badge to "in force" and revise the associated flag text.
- **Adjust scoring.** The `getRiskTier()` function contains all weights and thresholds. The visible scoring table in `renderIntro()` must be updated to match any changes to the logic.
- **Add a question.** Each question is an object in the `STEPS` array. Copy an existing object, update the `id`, `q`, and `options`, then add scoring conditions to `getRiskTier()` and flag text to `getFlags()`.

---

*This tool is a structured starting point, not a legal compliance sign-off. For consequential AI deployments, consult employment counsel and a qualified privacy advisor. Legal references reflect Canadian law as of June 2026.*
