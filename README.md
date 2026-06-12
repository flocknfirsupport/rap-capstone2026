# Responsible AI Intake & Decision Framework

**Melisa DiPietro | RAP Capstone | June 2026**

---

## The Problem

SMB HR / people leadership stakeholders are adopting AI tools faster than they have frameworks to evaluate them. Unlike enterprise organizations with dedicated legal and compliance teams, smaller business people leaders are left to make their own vendor and deployment decisions. Existing AI governance resources assume dedicated compliance staff and enterprise tooling. This tool helps fill that gap: a structured, plain-language intake that any people talent stakeholder can complete before a tool touches a people process.

---

## Responsible AI Lens Applied

The tool addresses five intersecting principles grounded in OPC guidance (2023), the CHRC AI Framework, and NIST AI RMF 1.0:

- **Bias & fairness.** AI trained on historical HR data encodes historical inequities. A formal bias audit is flagged as strongly recommended to implement regularly before any consequential use to reduce harm risk, citing Obermeyer et al. (2019) and Buolamwini & Gebru (2018).
- **Privacy.** PIPEDA requires informed consent for personal data processing. The tool separates current law (PIPEDA, in force) from proposed regulations (i.e. Bill C-27/AIDA, not in force as of June 2026).
- **Agency & recourse.** Employees and candidates whose employment outcomes are shaped by AI must be able to understand and contest these decisions. No override path is treated as a critical gap.
- **Transparency.** Affected people cannot participate in a process they do not know much about. The tool flags non-disclosure as a critical issue and treats written process notice as the minimum standard.
- **Decision power.** The tool distinguishes AI as a binding decision-maker from AI as a drafting aid. That distinction carries the most weight in the risk scoring because it determines whether a human retains real authority or nominal authority.

---

## Key Design Choices

The intake covers use case, data, vendor model, AI role in decisions, disclosure status, bias evaluation, and human override. Each question maps to a distinct responsible AI dimension. The sequence moves from what the tool does to how it is governed, which mirrors how an HR leader would naturally think through a deployment decision.

- **Weighted risks with visible scoring logic.** Answers feed a numeric scoring model that produces a risk tier (high, medium, lower). The weights are visible to users via a collapsible "How this tool scores risk" panel. Users who disagree with a weight can adjust their approach accordingly.
- **Employee-facing row.** The summary table includes a line showing what an affected person can access or contest, built from the disclosure and override answers. Most governance tools are written entirely from the employer perspective.
- **Self-report caveat.** Lower-risk results include "based on your self-reported answers." A clean result reflects what was entered, not what was verified.
- **Phased deployment framing.** Medium-risk results recommend a pilot before full rollout, with specific criteria for what a quarterly review should examine.

---

## Tradeoffs & Open Questions

- **Scoring is heuristic.** Weights are calibrated against OPC, CHRC, and NIST guidance but have not been independently validated against compliance outcomes.
- **Self-report limits.** All inputs are self-reported with no verification mechanism. The value depends on honesty.
- **Coverage gaps.** Environmental impact and francophone workforce considerations are not covered by the eight questions. Employers have a duty to inquire and follow through, i.e. on accommodation process, where coverage gaps may exist.
- **Legal currency.** The legal references section includes a last reviewed date and can be updated whenever new legislation passes.

---

## Picking It Up and Using It

Open `flocknfir-ai-intake.html` in any browser. No install, no login, no data stored. Works offline. To share with a client, attach the HTML file directly — it is self-contained at 45kb.

- **Update legal references.** Open in a text editor, search `June 2026` and `Last reviewed` to find all date references. When Bill C-27 passes, change the "proposed" status badge to "in force" and revise the associated flag text.
- **Adjust scoring.** The `getRiskTier()` function contains all weights and thresholds. The visible scoring table in `renderIntro()` must be updated to match any changes made to the logic.
- **Add a question.** Each question is an object in the `STEPS` array. Copy an existing object, update the `id`, `q`, and `options`, then add scoring conditions to `getRiskTier()` and flag text to `getFlags()`.

---

*This tool is a structured starting point, not a legal compliance sign-off. For consequential AI deployments, consult employment counsel and a qualified privacy advisor.*
