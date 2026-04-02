# CLARA Roadmap

This document describes CLARA's current limitations honestly, the enhancements planned for future versions, and how contributors or collaborators can get involved.

CLARA is an independently developed, unfunded pet project. The constraints described below are resource constraints — not capability or design gaps. The architecture for most of what is described here has already been prototyped.

---

## Current Limitations

### 1. Evidence Retrieval — No Live Database Connectivity

This is the most significant current limitation.

CLARA's evidence outputs are grounded in the CLARA Knowledge File and the underlying LLM's training knowledge. CLARA does not currently query live medical databases in real time. This means:

- Evidence citations are drawn from the LLM's training data, which has a knowledge cutoff date
- Newly published trials, updated systematic reviews, and recent guideline changes may not be reflected
- CLARA cannot verify whether a specific study exists, has been retracted, or has been superseded

**What this means in practice:** CLARA's frameworks, hierarchy placements, and manipulation detection are robust and do not depend on real-time data. Its evidence grading for well-established interventions is reliable. For fast-moving topics (longevity, GLP-1 agonists, microbiome, peptide therapies — flagged explicitly in the Knowledge File), outputs should be treated as provisional and verified against current systematic reviews.

**The planned solution:** A retrieval-augmented generation (RAG) pipeline connecting CLARA to trusted primary databases. A working Python RAG prototype has already been developed. The constraint is operational cost at scale for an unfunded project.

---

### 2. Planned Database Integrations — Not Yet Implemented

The following integrations were designed and partially prototyped. They are not active in the current version.

| Source | Type | Status | Notes |
|---|---|---|---|
| **PubMed / MEDLINE** | Free, open API (NCBI E-utilities) | Prototyped, not deployed | World's largest biomedical literature database. Free API access. Highest priority for implementation. |
| **Semantic Scholar** | Free, open API | Prototyped, not deployed | AI-powered academic search with citation graph and semantic similarity. Strong for evidence network mapping. |
| **Cochrane Library** | Subscription / open access mixed | Planned | Gold standard for systematic reviews. Some content open access; full integration requires institutional or commercial licence. |
| **UpToDate Connect** | Paid enterprise API (Wolters Kluwer) | Planned | Launched October 2025. Enterprise API for embedding evidence-based clinical decision support. Requires organisational licence — cost-prohibitive for an unfunded project currently. |
| **ClinicalTrials.gov** | Free, open API | Planned | CLARA already directs users to ClinicalTrials.gov manually for Grade B/C/D findings. API integration would automate this. |
| **HSA Singapore** | Web-based, no public API currently | Planned | Health Sciences Authority drug and supplement regulatory database. Relevant for Singapore-contextualised compound safety checks. |
| **BNF / NICE** | Mixed access | Planned | British National Formulary and NICE guidelines. Relevant for drug interaction and clinical guideline grounding. |

---

### 3. No Persistent Memory Across Sessions

CLARA operates within a single session context. It does not retain information about a user's health history, medications, previous evaluations, or preferences across sessions. Each session starts fresh.

**Impact:** Users need to re-provide relevant context (current medications, health conditions, what they have already evaluated) at the start of each session for CLARA to give fully personalised outputs via the Clinical Bridge.

**Planned solution:** A lightweight user profile layer that persists relevant context between sessions, with explicit user control over what is stored and the ability to clear it at any time.

---

### 4. Knowledge File Version Lag

The CLARA Knowledge File is a static document that is updated manually with each version release. The evidence landscape — particularly for fast-moving topics — moves faster than periodic releases can track.

**Impact:** For the fast-moving topics listed in the Knowledge File Confidence Map (Appendix A.4), CLARA's outputs reflect the evidence as of the Knowledge File version date, not today.

**Planned solution:** Automated or semi-automated Knowledge File refresh via database integration (above), with a version date prominently surfaced in every CLARA session.

---

### 5. LLM Dependency and Hallucination Risk

CLARA's output quality depends on the underlying LLM's instruction-following capability and training data accuracy. LLMs can hallucinate — generating outputs that are plausible-sounding but factually incorrect. CLARA's structured frameworks reduce (but do not eliminate) this risk by constraining the output format and requiring citations.

**What CLARA does to mitigate this:** The system prompt constrains CLARA to named reference authorities, requires absolute risk figures alongside relative figures, mandates the Clinical Bridge for clinical territory, and requires explicit uncertainty flags for weak evidence. The Knowledge File provides grounded reference tables rather than relying on the LLM to generate them from scratch.

**What users should do:** Treat CLARA outputs as structured starting points for further verification, not as authoritative final answers. The DISCLAIMER.md is explicit on this point.

---

## Planned Enhancements

### Near-Term (v3.3)

These are documentation and framework improvements that do not require database integration.

- **Precautionary Principle module** — explicit framework for decisions under uncertainty where the evidence is insufficient but potential harms are asymmetric
- **Natural experiments** as a named evidence category in the Bradford Hill / evidence triangulation framework
- **Drug interaction coverage expansion** — broader reference coverage for supplement-drug interactions, which are currently underrepresented relative to drug-drug interactions

### Medium-Term — Database Integration Phase

Priority order based on impact, cost, and implementation complexity:

1. **PubMed RAG integration** — free API, highest evidence volume, most immediate impact on citation accuracy. Python prototype exists.
2. **Semantic Scholar integration** — evidence network mapping, citation graph for Source Quality Audit automation
3. **ClinicalTrials.gov API** — automate the standing ClinicalTrials.gov check currently performed manually for Grade B/C/D findings
4. **Cochrane abstracts** — open-access Cochrane abstract layer for systematic review grounding
5. **UpToDate Connect** — enterprise tier; requires partnership or funding. Highest clinical decision support value for the Clinical Bridge function.

### Longer-Term

- **Persistent user profile layer** — opt-in session memory for medications, health conditions, and previously evaluated claims
- **CLARA Web Interface** — a lightweight Streamlit or equivalent front-end so non-technical users can access CLARA without needing to configure a Claude Project manually
- **Localisation variants** — regional Knowledge File variants adapting reference authorities for non-Singapore contexts (e.g. UK/NICE-primary, Australia/TGA-primary, US/FDA-primary)
- **Clinician-facing mode** — a higher-depth mode designed for healthcare professionals, with full technical reference output and integration with clinical workflow tools

---

## How to Contribute or Collaborate

CLARA is open source under CC BY-NC-SA 4.0. Contributions are welcome. See [`CONTRIBUTING.md`](./CONTRIBUTING.md) for full guidelines.

### What Would Have the Highest Impact

**If you are a developer:**
- PubMed or Semantic Scholar RAG integration (Python preferred — prototype available on request)
- ClinicalTrials.gov API connector
- Streamlit front-end for non-technical user access
- Automated Knowledge File refresh pipeline

**If you are a clinician or health researcher:**
- Review of Clinical Bridge outputs for clinical accuracy
- Drug interaction coverage gaps — flagging underrepresented interactions
- Regional applicability review for non-Singapore populations
- Contributions to Knowledge File evidence tables for specific domains

**If you represent a data provider or database owner:**
If you work with or represent any of the databases listed above — particularly Cochrane, UpToDate/Wolters Kluwer, HSA Singapore, or NICE — and are interested in exploring access arrangements for a non-commercial health literacy project, please open a [GitHub Issue](../../issues) or reach out directly.

CLARA's non-commercial, public health literacy mission may qualify for academic or non-profit access tiers with some providers. Any such arrangement would be disclosed openly in this repository.

**If you are a funder or institutional partner:**
The primary cost barrier to CLARA's next phase is operational database access costs. If you represent an organisation interested in supporting a non-commercial health literacy tool — particularly one contextualised for Singapore and Southeast Asian populations — please open a GitHub Issue.

---

## A Note on Scope

CLARA will remain a health literacy tool — not a diagnostic system, not a clinical decision support tool for healthcare providers, and not a replacement for professional medical judgment. The enhancements above are all in service of making CLARA's existing functions more accurate, more current, and more accessible. The scope boundaries in the system prompt are not planned to change.

---

*Last updated: April 2026*  
*Maintained by Kevin Lai — [github.com/krunchyb-88/CLARA](https://github.com/krunchyb-88/CLARA/)*
