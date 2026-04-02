# CLARA — Critical Literacy and Reasoning Assistant

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
![Version: 3.2](https://img.shields.io/badge/Version-3.2-blue)
![Status: Active Development](https://img.shields.io/badge/Status-Active%20Development-orange)
![Domain: Health Literacy](https://img.shields.io/badge/Domain-Health%20Literacy-green)
![Context: Singapore](https://img.shields.io/badge/Context-Singapore-red)

> ⚠️ **CLARA is an AI health literacy tool, not a doctor. Do not use CLARA as a substitute for professional medical advice. Verify all outputs with a qualified healthcare professional before making any health decisions.**

---

## 📖 Read the User Guide Before Your First Session

**[CLARA\_User\_Guide\_v3.2.pdf](./CLARA_User_Guide_v3.2.pdf)** — Part One takes approximately 15 minutes and will make every interaction significantly more useful. It covers:

- The Five Moves for spotting health misinformation before it works
- How health evidence actually establishes causation (and the two errors this prevents)
- The Intervention Hierarchy — why Tier 1 foundations matter before any supplement
- How to recognise when you are cognitively vulnerable to misinformation
- How to use CLARA effectively, including how to ask better questions

> You do not need to read Part Two before starting. Come to it when you are ready to go deeper into the science behind CLARA's frameworks.

---

## What is CLARA?

CLARA (Critical Literacy and Reasoning Assistant) is an AI health literacy tool that applies structured, evidence-based frameworks to health and wellness claims. It helps users evaluate the quality of health information — not by telling them what to believe, but by giving them the tools to evaluate claims themselves.

CLARA applies the GRADE evidence framework across nutrition, supplementation, metabolic health, cardiovascular health, and adjacent domains. It operationalises a four-tier intervention hierarchy, a structured source quality audit, a claim type classifier, and a Clinical Bridge function that prepares users for clinical conversations.

**CLARA is not a diagnostic tool.** It does not diagnose conditions, recommend initiating or changing medications, or replace the clinical judgment of a qualified healthcare professional.

---

## Repository Contents

| File | Version | Description |
|---|---|---|
| `CLARA_system_prompt_v3.md` | v3.0 | Core system prompt — defines CLARA's behaviour, constraints, evidence standards, and Clinical Bridge function |
| `CLARA_Knowledge_File_v3_2.md` | v3.2 | Reference tables, evidence hierarchies, manipulation playbook, GRADE framework, intervention hierarchy (13 health goals), source quality audit, glossary, and confidence map |
| `CLARA_User_Guide_v3_2.pdf` | v3.2 | User guide and pre-reading — essential before first use |
| `INSTRUCTIONS.md` | — | Step-by-step setup guide — how to configure CLARA in Claude.ai and run your first session |
| `ROADMAP.md` | — | Current limitations, planned enhancements, and collaboration opportunities |
| `DISCLAIMER.md` | — | Full legal disclaimer and limitation of liability |
| `CONTRIBUTING.md` | — | Contribution guidelines and contributor licence agreement |
| `LICENSE` | — | CC BY-NC-SA 4.0 full licence text |

> **Compatibility note:** Knowledge File v3.2 is compatible with System Prompt v3.0. The System Prompt governs CLARA's behaviour; the Knowledge File provides the reference frameworks it draws on.

---

## How to Use CLARA

CLARA is a **system prompt** designed to be used with a Large Language Model (LLM).

### Setup

1. **Read the User Guide first** — [`CLARA_User_Guide_v3.2.pdf`](./CLARA_User_Guide_v3.2.pdf). Part One (15 minutes) will substantially improve the quality of your interactions.
2. Copy the contents of [`CLARA_system_prompt_v3.md`](./CLARA_system_prompt_v3.md) into the system prompt field of your LLM interface or API call.
3. Optionally, also load [`CLARA_Knowledge_File_v3_2.md`](./CLARA_Knowledge_File_v3_2.md) as context — this provides the full reference framework CLARA draws on. Without it, CLARA operates from the LLM's training knowledge, which may be less precise.

### Starting a Session

When you submit your first message, CLARA will:
1. Display a one-sentence disclaimer
2. Ask whether you prefer **Lay Mode** (plain language) or **Expert Mode** (technical depth)

CLARA does not answer your question until mode is confirmed. You can switch modes at any time by saying *"explain this more simply"* or *"switch to expert mode."*

> CLARA has been developed and tested primarily with **Claude (Anthropic)**. Behaviour may vary across other LLM providers.

---

## What CLARA Does

| Function | Description |
|---|---|
| **Evidence grading** | Rates evidence A–D using the GRADE framework, with direction indicators (Strengthening / Stable / Weakening / Contested) |
| **Hierarchy placement** | Places any intervention in a four-tier priority hierarchy before evaluating its specific evidence |
| **Claim type classification** | Classifies claims as mechanism, association, causation, or magnitude — preventing category errors |
| **Source quality audit** | Eight-question audit including lateral reading, source actor analysis, and evidence network check |
| **Manipulation detection** | Identifies the Five Manipulation Techniques in health content |
| **Clinical Bridge** | Produces structured questions, background to gather, and evidence summaries for clinical conversations |
| **Drug interaction facts** | Provides factual information on known interactions from clinical reference databases |
| **Absolute risk presentation** | Always presents absolute risk figures alongside relative figures |

---

## Knowledge File — What's Inside

The **CLARA Knowledge File v3.2** contains 14 sections:

- Preamble and mode selection framework
- Manipulation Playbook — the Five Techniques with detection questions
- Evidence Grading — full GRADE framework with second-order uncertainty and Bayesian direction indicators
- Claim Type Classifier
- Source Quality Audit with lateral reading and evidence network check
- Evidence Expansion Protocol (v3.2) — lateral evidence expansion with domain-specific structural research problems
- Intervention Hierarchy — 13 health goal reference tables
- Genuine vs. Manufactured Controversy Protocol
- Benefit-Harm Balance framework (NNT:NNH, opportunity cost)
- Clinical Bridge function specification
- Cognitive Vulnerability Awareness
- Population Applicability — including Singapore-specific context
- Glossary
- Confidence Map with domain confidence ratings, section stability ratings, and fast-moving topic flags

---

## Evidence Framework

CLARA uses the **GRADE framework** — the internationally adopted standard used by WHO, Cochrane, NICE, MOH Singapore, CDC, and most major clinical guideline bodies.

Primary reference authorities: WHO, Cochrane Collaboration, MOH Singapore, CDC, NICE, ESC, USPSTF, and HSA Singapore (for regulatory status of compounds).

Where guideline bodies diverge, CLARA notes the divergence explicitly.

---

## Scope and Confidence

| Confidence Level | Domains |
|---|---|
| **High** | Nutrition, dietary patterns, supplementation, exercise, metabolic health, cardiovascular health |
| **Moderate** | Mental health interventions, longevity interventions, gut health, hormonal health lifestyle approaches, environmental health claims *(flagged explicitly when operating here)* |
| **Defers to Clinical Bridge** | Pharmaceutical recommendations, medication management, individual treatment decisions for diagnosed conditions |

**Fast-moving topics** — outputs treated as provisional, always verify against current systematic reviews:

Longevity interventions · GLP-1 agonists · CGM in non-diabetic populations · Microbiome products · Personalised nutrition · Time-restricted eating · Omega-3 formulations · Photobiomodulation · Peptide therapies · Cognitive enhancement supplements

---

## Geographic Context

CLARA v3.2 is contextualised for **Singapore as its primary geographic context** while remaining applicable globally. Singapore-specific considerations include:

- Asian-appropriate BMI thresholds (overweight: ≥23, obese: ≥27.5)
- MOH Singapore guidelines cited as primary alongside WHO, NICE, CDC
- HSA (Health Sciences Authority) referenced for compound regulatory status
- Asian population cardiovascular and metabolic risk data where available
- CYP450 enzyme variant prevalence in Asian populations noted where clinically relevant

For users outside Singapore: replace MOH Singapore references with your national health authority and apply the Population Applicability framework for ethnicity and geography mismatches.

---

## Version History

| Version | Key Changes |
|---|---|
| v1.0 | Initial release — basic evidence grading and source quality framework |
| v2.0 | Intervention hierarchy, expanded glossary, statistical red flag table, benefit-harm balance, population applicability |
| v3.0 | Major revision — dual-mode operation, system prompt formalised, manipulation playbook, claim type classifier, clinical bridge, cognitive vulnerability awareness |
| v3.1 | Evidence methodology expansion — Bradford Hill framework, evidence triangulation, Mendelian randomisation, replication crisis framework, absence vs. evidence of absence protocol |
| v3.2 *(current)* | Evidence Expansion Protocol, lateral evidence expansion, domain-specific structural research problems, updated risk framing effects, pre-registration audit protocol |
| v3.3 *(pending)* | Precautionary Principle addition, natural experiments as named evidence category |

---

## Licensing

This work is licensed under [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/).

You are free to **share** and **adapt** this material for **non-commercial purposes only**, provided you:
- Give appropriate credit to the original author
- Link to the licence
- Indicate if changes were made
- Distribute any adapted material under the same licence

**Commercial use is prohibited without explicit written permission from the author.**

> Note: This licence applies to the prompt and documentation files in this repository. If you build software or applications using CLARA as a component, the code you write should be licensed separately under an appropriate software licence (e.g. MIT, Apache 2.0).

---

## Legal Disclaimer

See [`DISCLAIMER.md`](./DISCLAIMER.md) for the full disclaimer and limitation of liability.

By using, copying, adapting, or deploying any material in this repository, you agree to the terms set out in `DISCLAIMER.md`.

---

## Contributing

See [`CONTRIBUTING.md`](./CONTRIBUTING.md) for contribution guidelines, scope, and the contributor licence agreement.

---

## Roadmap & Current Limitations

CLARA is functional and useful as-is. It also has real limitations — primarily the absence of live database connectivity — that are documented honestly in [`ROADMAP.md`](./ROADMAP.md).

The roadmap covers: current limitations and their practical impact, planned database integrations (PubMed, Semantic Scholar, ClinicalTrials.gov, Cochrane, UpToDate Connect), medium and longer-term enhancements, and an open call for contributors, data providers, and potential partners.

If you are a developer, clinician, researcher, data provider, or potential funder interested in contributing to or collaborating on CLARA's next phase, [`ROADMAP.md`](./ROADMAP.md) is the place to start.

---

## Contact

This project is independently maintained. For questions, feedback, or collaboration enquiries, please open a [GitHub Issue](../../issues).

---

*Developed in Singapore. Nothing in this repository constitutes medical advice or clinical guidance under the Singapore Medical Registration Act (Cap. 174) or any equivalent legislation.*

© 2026 Kevin Lai. Licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/).
