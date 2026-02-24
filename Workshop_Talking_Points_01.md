# Workshop: How to Build a Production Flowchart for Any Financial Document
## Talking Points & Script — Ezequiel Padilla
### Format: 30–45 minutes, talk + live demonstration
### Audience: 12 captains, each responsible for one financial document type

---

## STRUCTURE OVERVIEW

| Block | Time | Format | Content |
|-------|------|--------|---------|
| 1. The End Product | 5 min | Show | What we're building and why |
| 2. Before You Start | 5 min | Talk | The three decisions that determine everything |
| 3. The Pipeline | 10 min | Talk + Demo | The 9-stage methodology, stage by stage |
| 4. Working With Claude | 7 min | Demo | The propose-and-validate pattern in action |
| 5. The Hard Constraints | 3 min | Talk | Non-negotiable rules for uniformity across 12 captains |
| 6. What "Done" Looks Like | 5 min | Show | The validation checklist and cross-deliverable coherence |
| 7. Your Action Items | 3 min | Talk | What each captain needs to do next |
| 8. Q&A | 5–7 min | Open | |

---

## BLOCK 1: THE END PRODUCT (5 min)
### Format: Screen-share the S-1 summary slide, then the flowchart, then the RACI

**Talking points:**

- This is what each of you will produce for your document type. Three deliverables: a Mermaid flowchart, a RACI matrix, and a summary slide. All three must reconcile to the same numbers.

- [Show EP_S1_Flowchart_Slide_vF.pdf] This is the summary slide. It's the entry point. The engineer sees 12 of these — one per document type — and can immediately compare: how many steps, how many roles, and most importantly, what percentage of production steps are LLM-assistable.

- [Show the Mermaid flowchart in mermaid.live] This is the underlying flowchart. 76 parent work steps, 123 total nodes, 8 roles, 6 phases. Every node is color-coded to the role that currently performs it. The detail is concentrated where the automation opportunity exists — LLM and Hybrid steps are expanded into sub-steps; Human and External steps stay high-level.

- [Show S1_RACI_Matrix.xlsx] This is the RACI. Every node in the flowchart has a row. Every role has a column. R matches the flowchart color. The RACI captures who is Consulted and Informed — the collaborative reality the flowchart can't show.

- The engineer's question is simple: for each document type, where can an LLM be inserted into the production process today? Your flowchart answers that question. The uniformity across all 12 slides is what makes the portfolio view useful.

**Key point to emphasize:** You are not producing a flowchart. You are producing a *package* — three deliverables that must agree with each other. If the flowchart says Company Counsel owns 44 steps, the RACI's R column must show 44 for Company Counsel, and the summary slide's role legend must say 44. Any mismatch gets flagged immediately.

---

## BLOCK 2: BEFORE YOU START (5 min)
### Format: Talk, no screen

**Talking points:**

- Before you open Claude, before you write a single node, you need three things nailed down. If you get these wrong, everything downstream is wrong.

- **Decision 1: What is your single deliverable?** Not "the transaction." Not "the IPO." One document. For me it was the S-1 registration statement. For you it might be the 10-K, the S-3, the CIM, the proxy statement. The scope of your flowchart is the production of that one document — from the event that triggers its production to the event that signals it's complete. Everything outside that boundary is out of scope. Period.

- [Pause] This sounds obvious but it's the single most consequential decision you'll make. If you scope too broadly — say you try to chart "the IPO" instead of "the S-1" — your step count explodes, the chart becomes unreadable, and you'll spend weeks trying to consolidate it back down. I learned this the hard way. Define the trigger, define the end condition, write them down, and enforce them at every stage.

- **Decision 2: What are your source materials?** You need 3–5 authoritative published guides from different publisher types — at least one top-10 law firm guide, at least one Big 4 accounting firm guide, and at least one industry or entity-type specialist. These are the skeleton of your step list. No single guide captures every step. The overlap between sources is how you ensure completeness. The manual tells you how to find these — you search for "[your document type] preparation guide," "[your document type] checklist," and similar terms.

- **Decision 3: What is your precedent transaction?** This is the single most critical input. The guides give you the process skeleton; the precedent filing gives you the actual section structure, the exhibit list, the amendment history, the real-world detail that no guide captures. You need the original filing plus all amendments. For me it was Mach Natural Resources — the S-1 plus three S-1/A amendments. You select yours from EDGAR or the relevant filing system, matching your entity type and document type.

**Key point to emphasize:** If you walk into your Claude session with these three things defined — scope, sources, precedent — the manual handles the rest. If you walk in without them, no amount of prompting will save you.

---

## BLOCK 3: THE PIPELINE (10 min)
### Format: Talk through each stage, with brief screen-shares of intermediate outputs from the S-1 project

**Talking points:**

- The methodology has 9 stages. They run in sequence. Each stage produces a deliverable that feeds the next. Claude does the heavy lifting at each stage, but you make the judgment calls. Here's the pipeline:

- **Stage 1 — Gather sources (Manual Section 3.1).** You give Claude your source documents and precedent filings. Claude identifies and confirms the authoritative sources for your document type. If you're doing a 10-K, Claude will search for 10-K preparation guides from the same publisher categories.

- **Stage 2 — Extract raw steps (Section 3.2).** Claude reads every source and extracts every discrete production activity. No filtering, no consolidation — just a raw inventory. For the S-1, this produced 198 raw steps. Your count will vary. The scope gate fires here — anything outside your scope boundary gets excluded during extraction.

- **Stage 3 — Merge (Section 3.3).** Claude combines all extracted steps into a single list. The scope gate fires again — any post-completion steps that slipped through extraction get removed. For the S-1, 198 raw steps became 164 merged steps.

- **Stage 4 — Deduplicate against precedent (Section 3.4).** This is the first stage where you make decisions. Claude walks the merged list against your precedent filing: if two entries describe the same work, merge them; if the precedent reveals a missing step, add it; if a step doesn't apply to your document type, remove it. Ambiguous cases come to you as numbered flags with default recommendations. You approve in bulk or override specific items.

  [DEMO: Show a flag table from the S-1 project — the F-1 through F-10 flags from Section 3.4. Show the "APPROVE ALL" response template. Show one override example — F-4: splitting DCF forecast as a standalone deliverable.]

- **Stage 5 — Assign single-role ownership (Section 3.6).** Every step gets assigned to exactly one role — the person who currently holds the pen. Not a working group, not "the team." One role, one color. Claude proposes assignments based on the source materials and live search. Ambiguous cases come to you as flags. For the S-1, this produced 8 roles. Your document type may have fewer or more.

  [Brief note] The roles come from the precedent filing — the cover page, signature pages, legal opinions, expert consents. Each distinct functional party becomes a role. The Okabe-Ito color palette gives you 8 colors. If your document type has more than 8 distinct roles, we need to discuss that as a team.

- **Stage 6 — Classify by LLM capability (Section 3.7).** Every step gets classified into one of four tiers: LLM (fully automated), Hybrid (Claude drafts, human reviews), Human (100% human), or External (SEC, exchange, FINRA). Claude proposes, you decide. This classification drives everything — it determines which steps get expanded into sub-steps and which stay high-level. It's also the basis for the LLM Opportunity percentages on your summary slide.

  [Key point] Classify based on the core production activity, not the prerequisites. If a step requires human-supplied input data but the drafting can be done by an LLM once inputs are in hand, that's Hybrid, not Human. The input-gathering is a dependency, not the step itself.

- **Stage 7 — Consolidate (Section 3.7.1).** After classification, Claude groups related steps into parent work steps. Multiple prospectus sections drafted by the same role in the same phase become one node, not five. The target is 60–90 parent work steps. If you're above 90, keep consolidating. If you're below 60, your granularity is probably too coarse.

- **Stage 8 — Expand sub-steps (Section 3.7.2).** Only LLM and Hybrid parent steps get expanded. Target 2–3 sub-steps per parent, max 5. After expansion, the total node count (including decisions and milestones) must stay under 150. If it doesn't, go back and consolidate more — don't split into multiple charts.

- **Stage 9 — Generate Mermaid code, build RACI, produce summary slide (Sections 4–10).** Claude generates the Mermaid code following the manual's syntax rules, naming conventions, and color system. The RACI is built concurrently — every node gets a row as it's added to the code. The summary slide is derived mechanically from the flowchart and RACI.

**Key point to emphasize:** Stages 1–3 are mechanical — Claude does the work, you approve. Stages 4–6 are where your domain expertise matters — Claude proposes, you make the judgment calls. Stages 7–8 are structural — Claude consolidates and expands within defined limits. Stage 9 is production — Claude generates code and deliverables to spec.

---

## BLOCK 4: WORKING WITH CLAUDE (7 min)
### Format: Live demonstration

**Talking points:**

- Let me show you what the interaction actually looks like. You don't need to be a prompt engineer. The manual does the prompting for you. Here's the pattern:

  [DEMO: Open a Claude conversation. Show the manual being uploaded. Show source documents being uploaded. Show the initial instruction: "Read the Instruction Manual. This is a [document type] for a [entity type]. The precedent transaction is [name]. Proceed with Section 3.1."]

- Claude reads the manual and follows it stage by stage. At each stage, it does the work, applies the scope gates, and presents you with either a clean deliverable for approval or a set of flags for your decision.

- **The flag workflow.** This is the core interaction pattern. When Claude encounters ambiguity — a step that could be merged or kept separate, a role assignment that could go either way, a classification that's borderline — it doesn't guess. It presents you a numbered flag table:

  | # | Issue | Default | Your Call |
  |---|-------|---------|-----------|
  | F-1 | Steps 23 and 47 both describe risk factor drafting — merge or keep separate? | Merge (same role, same output) | Approve / Override |
  | F-2 | Is DCF forecast a standalone deliverable or part of financial projections? | Part of projections | Approve / Override |

  You respond: "APPROVE ALL" or "F-2: override — split as standalone."

- **The live search requirement.** Before Claude presents each flag, the manual requires it to conduct a live web search to verify its default recommendation. This catches cases where Claude's training knowledge is wrong about domain-specific facts. For example, during our S-1 test, Claude initially placed test-the-waters meetings in the wrong phase — a live search for JOBS Act Section 5(d) would have caught that before it was presented to me.

- **What you should NOT do.** Do not try to give Claude all your instructions verbally in the chat. Do not try to explain the methodology conversationally. Upload the manual, upload your sources, and let the manual drive. Your job is to make decisions at the flags and verify the outputs. Claude's job is everything else.

  [DEMO: Show Claude presenting a flag table, user responding with "APPROVE ALL" plus one override, Claude proceeding to the next stage.]

---

## BLOCK 5: THE HARD CONSTRAINTS (3 min)
### Format: Talk, no screen

**Talking points:**

- For the 12-slide deck to work as a portfolio view, all 12 flowcharts must follow the same rules. These are non-negotiable:

- **Okabe-Ito color palette.** Every captain uses the same 8 colors for the same role types. If your document type has a role called "Company Counsel," it's blue #0072B2. If it has "Accountants," it's yellow #F0E442. If your document type has a role that doesn't map to the standard 8, raise it with the team before assigning a color.

- **Same three node shapes.** Rectangles for action steps, diamonds for decisions, stadiums for milestones. Nothing else.

- **Same naming convention.** Node IDs: [RoleAbbrev]_[TaskName]. Display text: "Role: Verb + object." Every flowchart, every captain.

- **Same RACI structure.** Three sheets: RACI Matrix, Legend, Summary. Same 13 columns. Same R/A/C/I assignment rules. Decision and milestone rows blank.

- **Same summary slide layout.** Three-column, 16:9. Left column: definitions + LLM opportunity. Center: phase bar + thumbnail + stats. Right: roles legend + key terms. Same font treatment, same accent colors.

- **Same counting basis.** Define "parent work steps" and "total nodes" for your document type. Report parent work steps on the slide headline. Report total nodes in the RACI and footnote. Document the relationship between the two counts.

- **60–90 parent steps, 150 total node ceiling.** If you exceed these, consolidate. Do not split into multiple charts unless the team agrees to a different architecture.

---

## BLOCK 6: WHAT "DONE" LOOKS LIKE (5 min)
### Format: Screen-share the Section 11 validation checklist

**Talking points:**

- You are not done when Claude generates the Mermaid code. You are done when you pass the Section 11 validation checklist — all 12 checks — and the cross-deliverable coherence check.

  [Show the 12-item checklist from Section 11]

- Walk through briefly:
  1. Renders in mermaid.live without errors
  2. No orphan nodes
  3. Every action node has a style statement
  4. Decisions and milestones have no style statements (except external-party diamonds)
  5. Node IDs follow naming convention
  6. Display text follows format
  7. Decision branches labeled
  8. Happy path complete (start to end, unbroken)
  9. RACI matches Mermaid node-for-node
  10. Subgraph boundaries correct
  11. Scope boundary verified — nothing past the end milestone
  12. Step counts within targets

- **Cross-deliverable coherence (Section 11.1).** Every number on your summary slide must match the Mermaid code and the RACI. Role counts, step counts, phase counts. One mismatch means something is wrong in one or more deliverables. The manual gives Claude the rules for checking this automatically.

- [Show the role count reconciliation table from the S-1 validation report — Mermaid styles = RACI R count = Summary slide, all matching for all 8 roles]

**Key point to emphasize:** The validation checklist is mechanical. Claude can run every check except #1 (which requires pasting into mermaid.live). If all 12 pass and all counts reconcile, you're done. If any check fails, fix it before delivering.

---

## BLOCK 7: YOUR ACTION ITEMS (3 min)
### Format: Talk

**Talking points:**

- Here's what each of you needs to do:

- **Step 1: Define your single deliverable.** Write down: the document name, the trigger event, the end condition, the entity type. One sentence each. If you can't define the end condition, you're not ready to start.

- **Step 2: Gather your sources.** Find 3–5 authoritative published guides for your document type. At least one law firm guide, one Big 4 guide, one specialist. Plus your precedent filing with full amendment history.

- **Step 3: Start a Claude session.** Upload the Instruction Manual (I'll distribute the vF file to everyone). Upload your source documents and precedent filings. Tell Claude to begin with Section 3.1. Follow the pipeline.

- **Step 4: Make your judgment calls.** At each flag, use your domain expertise. Approve or override. Don't defer — a decision deferred is a flag that comes back later.

- **Step 5: Validate.** Run the Section 11 checklist. Verify cross-deliverable coherence. Paste into mermaid.live. Render the PNG for your summary slide.

- **Step 6: Deliver.** Three files: the .mmd file (Mermaid code), the .xlsx file (RACI workbook), and the summary slide (matching the template format). I'll collect all 12 and assemble the final deck.

- **Timeline:** [User to specify — suggest a deadline for the team]

- **If you get stuck:** The manual has a WARNING or TIP for almost every ambiguous situation. If you encounter something the manual doesn't cover, raise it with me and we'll add guidance for everyone.

---

## BLOCK 8: Q&A (5–7 min)

**Anticipated questions:**

- "What if my document type has more than 8 roles?" → Raise it with the team. We may need to define a shared extended palette or confirm that some roles can be mapped to the standard 8.

- "What if my step count is way below 60?" → Some document types are simpler. A CIM may have 40 parent steps. That's fine — the 60–90 range is a target, not a hard floor. Below 40 suggests your granularity is too coarse; verify against your precedent.

- "What if Claude doesn't follow the manual?" → Re-upload the manual and explicitly tell Claude to re-read it. If a specific section is being ignored, quote the section number and instruct Claude to follow it. The manual was tested twice — if Claude deviates, it's likely a context window issue, not a manual deficiency.

- "Do I need to use Claude specifically, or can I use another model?" → The manual was tested with Claude Opus. It should work with other Claude models (Sonnet, etc.) but has not been tested with non-Anthropic models. The propose-and-validate pattern and flag workflows are model-agnostic in principle, but the live search integration and file handling may differ.

- "How long did this take you?" → The S-1 project, including developing and testing the manual, took several weeks. But that included building the methodology from scratch and running two full test cycles. With the manual in hand, a captain running the pipeline for a new document type should be able to produce the three deliverables in a matter of days, not weeks — assuming they have their sources and precedent ready.

---

## MATERIALS TO DISTRIBUTE

| Item | File | Purpose |
|------|------|---------|
| 1 | Mermaid_Flowchart_Instruction_Manual_vF.md | The operating manual — upload to Claude |
| 2 | EP_S1_Flowchart_Slide_vF.pdf | Reference example — what the summary slide should look like |
| 3 | S1_RACI_Matrix.xlsx | Reference example — what the RACI should look like |
| 4 | EP_S1_Flowchart_Mermaid_vF.txt | Reference example — what the Mermaid code should look like |
| 5 | Manual_Test_Findings.md | Optional — shows the 16 findings and how they were resolved, for captains who want to understand why specific rules exist |
