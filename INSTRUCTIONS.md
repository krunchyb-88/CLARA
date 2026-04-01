# Getting Started with CLARA

CLARA is a health literacy tool. It evaluates health and wellness claims using structured, evidence-based frameworks — and helps you navigate the gap between what health content says and what the evidence actually shows.

This document covers everything you need to go from zero to your first useful CLARA session.

---

## Step 1 — Read Part One of the User Guide First

Before your first session, read Sections 1–6 of [`CLARA_User_Guide_v3.2.pdf`](./CLARA_User_Guide_v3.2.pdf) (approximately 15 minutes).

This is not optional background reading — it is what makes every session significantly more useful. It teaches you:

- The **Five Manipulation Techniques** CLARA is designed to detect
- How health evidence actually establishes causation — and the two errors this prevents
- The **Intervention Hierarchy** — why Tier 1 foundations matter before any supplement
- How to recognise when you are cognitively vulnerable to misinformation
- How to bring the right questions to get the most useful evaluations

Sections 7–13 (Part Two) go deeper into the science behind CLARA's frameworks. Come back to these when you are ready to get more from the system. You do not need Part Two before your first session.

---

## Step 2 — Set Up the Project

CLARA runs inside a **Claude.ai Project**. Projects are available on Claude Pro and Claude Team plans. You will need an active account with Projects access.

> **[claude.ai/projects](https://claude.ai/projects)**

### Step 2a — Create a new Project

In Claude.ai, navigate to Projects and create a new Project. Give it a name (e.g. "CLARA").

### Step 2b — Add the System Prompt

Open **Project Settings** and paste the full contents of [`CLARA_system_prompt_v3.md`](./CLARA_system_prompt_v3.md) into the **"Project instructions"** field.

This defines CLARA's identity, its operating modes, its behavioural constraints, and how it responds. It must be in the Project instructions field — not uploaded as a file and not pasted into the chat.

### Step 2c — Upload the Knowledge File

Upload [`CLARA_Knowledge_File_v3_2.md`](./CLARA_Knowledge_File_v3_2.md) as a **knowledge file** in the same Project (via the Project's file/document section, not the chat window).

This is CLARA's reference library — the frameworks, evidence hierarchies, intervention hierarchy tables, manipulation playbook, and glossary it draws on when evaluating claims. Without it, CLARA operates from the model's training knowledge, which may be less precise for structured framework outputs.

> **Note on file size:** The Knowledge File is large. If you encounter context window issues on lower-tier plans, try uploading it in sections or check whether your plan supports the full context window needed. Claude Pro handles the full file without issue.

---

## Step 3 — Start a Session

Open the Project and ask your first question.

CLARA will first display a one-sentence disclaimer, then ask whether you prefer:

- **Lay Mode** — plain language, narrative explanations, inline definitions
- **Expert Mode** — technical depth, reference format, direct framework application

Choose whatever feels right. You can switch modes at any point during a session by saying:
- *"Explain this more simply"* → switches to Lay Mode
- *"Switch to expert mode"* → switches to Expert Mode

CLARA will not answer your substantive question until mode is confirmed. If you do not choose, it defaults to Lay Mode.

---

## How to Ask a Question That Gets a Useful Answer

CLARA works best on **specific claims**, not general topics. Naming the source, the specific assertion, and what decision you are trying to make produces a much more useful evaluation than a broad question.

| Instead of this | Try this |
|---|---|
| *"Is magnesium good for sleep?"* | *"I read a study claiming magnesium reduces cortisol by 30% — what does the evidence actually show, and where does magnesium sit in the intervention hierarchy for sleep?"* |
| *"Should I take omega-3?"* | *"I don't take statins and have a standard lipid panel — is there evidence that omega-3 supplementation improves cardiovascular outcomes for someone like me?"* |
| *"Is this study reliable?"* | *"Here is a 2023 RCT from [journal] showing berberine reduces HbA1c by 1.1 mmol/L — can you run the Source Quality Audit and tell me where it sits in the broader evidence network?"* |

The more specific the claim, the more useful the evaluation. See Section 13 of the User Guide for a full guide to asking better questions.

---

## What CLARA Does — and Does Not Do

**CLARA does:**
- Evaluate health and wellness claims using structured evidence frameworks
- Grade evidence A–D using the GRADE framework, with direction indicators
- Place interventions in a four-tier priority hierarchy before evaluating their specific evidence
- Identify manipulation techniques in health content
- Provide factual information on known drug interactions from clinical reference sources
- Prepare you with specific questions and evidence summaries for clinical conversations (Clinical Bridge)
- Present absolute risk figures alongside relative figures

**CLARA does not:**
- Diagnose conditions from described symptoms
- Recommend initiating, stopping, or changing any medication
- Present a single study as settled science
- Replace the clinical judgment of a qualified healthcare professional

---

## Troubleshooting

**CLARA is not following the structured output format**
Confirm the system prompt is in the Project instructions field, not uploaded as a file or pasted into chat. The instructions field is what governs CLARA's behaviour throughout the session.

**The Knowledge File is not being referenced**
Ensure the file is uploaded to the Project's knowledge/document section, not sent in the chat window. If the file appears truncated, check your plan's context window limit.

**Mode switching is not working as expected**
Use the exact phrases: *"explain this more simply"* or *"switch to expert mode."* If switching still seems inconsistent, start a new session within the same Project — mode is set at session start.

**CLARA is giving generic health information rather than structured framework outputs**
This usually means the Knowledge File is not loaded or the system prompt was not saved correctly. Verify both are in place, then start a fresh session.

---

## Using CLARA on ChatGPT

CLARA has been tested on ChatGPT Projects using the same two files (system prompt + knowledge file) and works at a general level.

However, **CLARA was designed and optimised for Claude**. Some behaviours — particularly mode switching, the Clinical Bridge outputs, and structured evidence output formats — may be less consistent on ChatGPT, as these depend on how each model follows detailed structured instructions. The User Guide is written for Claude, so some operational details may differ slightly on other platforms.

The underlying frameworks, evidence logic, and what to bring to a session work the same way regardless of platform.

---

## The Goal

CLARA is designed to build your health literacy over time — not just to answer individual questions. The more you use it, the more you will recognise the patterns yourself: the claim type, the manipulation technique, the hierarchy placement. The aim is that over time, you need it less.

---

*For project documentation, licensing, and contribution guidelines, see [`README.md`](./README.md).*  
*For legal disclaimer and limitation of liability, see [`DISCLAIMER.md`](./DISCLAIMER.md).*
