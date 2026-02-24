  
**MERMAID FLOWCHART**

**INSTRUCTION MANUAL**

Coding Standards, Best Practices & Style Guide

Version 3.0

February 2026

# **1\. Purpose & Scope**

This manual defines the mandatory standards for creating Mermaid flowcharts. It codifies the methodology, coding conventions, shapes, colors, node naming, labeling rules, and structural patterns to be followed on every flowchart produced by this team.

## **1.1 What Is Mermaid?**

Mermaid is a lightweight, text-based diagramming language. You write structured code in a plain text file, then render it into a visual flowchart. There is no drag-and-drop interface; the diagram is generated entirely from code.

## **1.2 Where to Render**

All flowcharts are tested and rendered in **mermaid.live** (https://mermaid.live). Paste your code in the left panel; the rendered diagram appears on the right. This is the canonical rendering environment.

## **1.3 Scope of This Manual**

This manual covers flowchart-type diagrams only (not pie charts, timelines, Gantt charts, or other Mermaid diagram types). All rules below apply to every flowchart produced under this methodology.

## **1.4 Foundational Design Principles**

Every flowchart produced under this methodology is governed by a set of foundational design principles. These principles are the “why” behind the rules in the sections that follow. All coding conventions, shape choices, color assignments, and structural patterns trace back to one or more of these principles.

1. **End-to-end coverage (“soup to nuts”).** The flowchart must capture the complete process from its initiating trigger to its terminal event, with an unbroken chain of nodes connecting the two. No gaps, no dead ends, no disconnected clusters. A viewer should be able to walk the entire process from start to finish without leaving the chart.

2. **Explicit decision points.** Real-world processes are not linear—they contain gates, approvals, and conditional branches. The flowchart must surface these as diamond-shaped decision nodes with labeled Yes/No outcomes, rather than burying them inside action steps or treating the workflow as a straight sequence.

3. **Role-based accountability.** Different steps are performed by different people. The flowchart must make this visible at a glance by assigning each action node a color tied to the role that currently performs it, and by prefixing every node’s display text with the role name. This single requirement drives the role taxonomy, the color palette, the node naming convention, and the companion RACI matrix.

4. **LLM-driven granularity.** The primary objective of the flowchart is to identify where an LLM (currently Claude, by Anthropic) can be inserted into the production process. Every step is classified into one of four tiers: **LLM** (Claude can perform entirely on its own), **Hybrid** (Claude drafts or assists, human reviews/approves), **Human** (requires 100% human judgment or action), or **External** (performed by an outside party such as the SEC or an exchange). Only LLM and Hybrid steps are expanded into granular sub-steps in the flowchart; Human and External steps remain high-level. This ensures the chart’s detail is concentrated where the automation opportunity exists.

*This list is not exhaustive.* Additional principles may be identified as the methodology evolves. When a new principle is established, it should be added here and cross-referenced to the sections it governs.

# **2\. Scoping the Flowchart**

Before writing any code, define the workflow boundary. Without a clear scope, flowcharts become infinite and unreadable. Answer four questions before you begin:

| Question | Example |
| :---- | :---- |
| Trigger | What initiates the process? (e.g., sponsor decides to pursue IPO; board authorizes proxy filing) |
| End condition | What signals completion? (e.g., SEC declares registration statement effective; proxy mailed to shareholders) |
| Setting / context | Department, location, system, or channel (e.g., SEC/EDGAR, NYSE listing application portal) |
| Object / variant | What type of case? (e.g., Oil & Gas MLP IPO; REIT 10-K annual report) |

## **2.1 Define the Single Deliverable**

Before scoping the flowchart, identify the single document or deliverable whose production process you are mapping. Real-world processes (such as an IPO) are vast and contain many workstreams. Attempting to chart the entire process will produce an unreadable diagram. Instead, narrow the scope to one concrete output.

**Example:** An IPO involves roadshows, pricing, allocation, closing, settlement, and more. But the flowchart’s scope is not “the IPO” — it is ***the production of the S-1 registration statement***. Everything in the chart must relate to producing, filing, reviewing, and obtaining effectiveness for that single document. Steps that occur after the S-1 is declared effective (pricing, allocation, closing) are out of scope.

This narrowing decision should be made explicitly and documented before any nodes are drafted. It determines both the start milestone (the event that triggers production of the deliverable) and the end milestone (the event that signals the deliverable is complete).

**WARNING:** LIVE SEARCH REQUIRED. If you are unfamiliar with the deliverable type, search for its regulatory definition, required contents, and how it differs from similar filings (e.g., S-1 vs. F-1 vs. S-11). You must understand what the deliverable contains before you can scope its production process.

**SCOPE ENFORCEMENT GATE (mandatory at every stage).** The scope boundary defined in this section is enforced at every subsequent stage of the methodology — merge (3.3), deduplication (3.4), role assignment (3.6), classification (3.7), and validation (11). Before presenting any deliverable to the user, re-verify that every entry falls within the defined scope boundary. Any step whose trigger event occurs after the end milestone is out of scope and must be removed immediately — do not carry it forward to the next stage. This is not discretionary; it is a hard gate.

**TIP:** USER INPUT REQUIRED. The choice of which deliverable to map is a strategic business decision that depends on the user’s objective. No instruction or source document can make this decision. The user must define the single deliverable before any other work begins.

## **2.2 The Soup-to-Nuts Rule**

**Every flowchart must be end-to-end.** It must begin with a start milestone (the trigger event that initiates the process) and end with an end milestone (the event that signals completion), with an unbroken chain of nodes connecting the two. There must be no gaps — every node must be reachable from the start, and the end must be reachable from every branch. If a viewer walks the chart from top to bottom, they should be able to trace the entire process without encountering dead ends or disconnected clusters.

## **2.3 Granularity Rule**

The level of detail in the flowchart is not uniform — it is driven by LLM capability classification (see Principle \#4). Before drafting the chart, classify every step into one of four tiers:

| Tier | Definition | Granularity in Chart |
| :---- | :---- | :---- |
| LLM | Claude can perform the step entirely on its own, end to end. | Expand into granular sub-steps. |
| Hybrid | Claude drafts or assists; a human reviews, edits, or approves. | Expand into granular sub-steps. |
| Human | Requires 100% human judgment, negotiation, or physical action. | Keep high-level (single node). |
| External | Performed by an outside party (SEC, exchange, FINRA, reserve engineer). | Keep high-level (single node). |

This classification ensures the chart’s detail is concentrated where the automation opportunity exists. Steps outside the team’s control stay big-picture; steps where Claude can add value get the full sub-step treatment.

**Defining “high-level” for Human and External steps.** A Human or External step should represent a complete work product, engagement, or regulatory action — not an individual document section or sub-task. If multiple sections are drafted by the same role in the same work session or phase, they are one step, not five. Example: “Draft Management, Compensation, and Ownership sections” is one Human step, not three separate nodes.

**Classification is based on the core production activity, not prerequisites.** Classify each step based on what happens when the drafter sits down to produce the output — not on the input-gathering that precedes it. If a step requires human-supplied input data (e.g., management interviews, board decisions) but the drafting or assembly work can be performed or assisted by an LLM once those inputs are in hand, classify it as Hybrid. The input-gathering is a dependency, not the step itself. The flowchart maps the document production process, and classification should reflect the production activity.

**TIP:** The four-tier classification is documented in a companion step classification table, not in the flowchart itself. The flowchart reflects the granularity outcome; the companion table records the underlying LLM/Hybrid/Human/External designation.

**TIP:** USER INPUT REQUIRED. The four-tier classification depends on the user’s specific operating environment — their team’s capabilities, risk tolerance, and compliance culture. What qualifies as “LLM” for a sophisticated team may be “Hybrid” or “Human” for a more conservative one. The user must validate every classification before the chart is expanded.

## **2.4 One-Page Rule**

**Rule of Thumb:** If the flowchart won’t fit legibly on one screen (or one printed page), the scope is too broad. Split into levels or sub-processes.

**Target step count range:** For a single-deliverable flowchart, target 60–90 parent work steps. If the count exceeds 90 after classification and consolidation (Section 3.7), review all tiers for further consolidation: group related sections drafted by the same role in the same phase into combined nodes, regardless of tier. The goal is a chart that renders legibly in mermaid.live without horizontal scrolling at default zoom. A chart with more than 150 total nodes (including expanded sub-steps, decision diamonds, and milestones) will not render legibly as a single chart and must be split per Section 2.5.

## **2.5 When to Split Into Sub-Processes**

Break into sub-processes when:

* A branch or section exceeds approximately 8–10 steps.

* A handoff goes to another department/function with many internal details.

* The detail level jumps dramatically (e.g., from “submit request” to “how IT provisions a laptop”).

**Consolidation checkpoint before splitting.** Before committing to a multi-level split, verify that the step count reflects proper consolidation per Sections 2.3 and 3.7. A two-level split is a structural decision driven by genuine process complexity — not a workaround for overcounting. If the count exceeds the targets in Section 2.4 due to insufficient grouping rather than genuine complexity, consolidate first. Only after confirming that consolidation has been fully applied should you proceed to a multi-level architecture.

## **2.6 Step Inclusion Test**

A step merits its own node if it changes:

* Who does it (role shift).

* Where or in what tool it happens.

* What can happen next (a decision point).

* It involves risk, time, or compliance impact.

# **3\. Step Identification Methodology**

The steps in the flowchart are not invented from memory or intuition. They are derived systematically from authoritative source materials and validated against a real precedent transaction. This section documents the process so it can be replicated for any new deliverable.

## **3.1 Gather Authoritative Source Materials**

Identify the leading published guides, checklists, and roadmaps for the type of deliverable being mapped. For the S-1 production flowchart, four primary sources were used:

1. Latham & Watkins — US IPO Guide (full guide \+ checklist annex).

2. Deloitte — IPO readiness guide (IPO Readiness Services & Assessment; DART Roadmap: Initial Public Offerings).

3. PwC — Roadmap for an IPO: A Guide to Going Public.

4. Vinson & Elkins (V\&E) — MLP Primer (for MLP-specific structural and tax steps).

Each source describes the production process from a slightly different angle and level of detail. Using multiple sources ensures comprehensive coverage — no single guide captures every step.

**WARNING:** LIVE SEARCH REQUIRED. Use live web search to identify and locate the leading published guides for your deliverable type. For a different deliverable (e.g., a proxy statement, a 10-K, or a bond offering memorandum), the authoritative sources will be different. Search for “\[deliverable type\] preparation guide,” “\[deliverable type\] checklist,” and equivalent terms to build your source library.

**Source identification procedure:** Search for guides and checklists from at least three categories of publisher: (a) top-10 law firms with capital markets practices (e.g., Latham, Kirkland, Simpson Thacher, V\&E), (b) Big 4 accounting firms (Deloitte, PwC, EY, KPMG), and (c) industry-specific specialists relevant to the deliverable type (e.g., energy-focused firms for MLP filings). Collect a minimum of 3–5 sources before proceeding to extraction. If the deliverable involves a specialized entity structure (MLP, REIT, SPAC, BDC), ensure at least one source addresses that structure specifically.

## **3.2 Extract Steps From Each Source**

Read each source and extract every discrete activity it identifies for producing the deliverable. At this stage, do not filter or consolidate — capture everything. Record each step with its source, the role the source assigns it to, and a brief description.

**WARNING:** LIVE SEARCH REQUIRED. When a source references a regulatory requirement, accounting standard, or legal concept that is not self-explanatory, search for the underlying detail before recording the step. For example, a source that says “prepare financial statements per PCAOB standards” requires searching what PCAOB standards specifically require in order to determine whether that is one step or five.

## **3.3 Merge Into a Combined List**

Combine all extracted steps into a single merged list. This raw union will be larger than the final step count because different sources describe the same activity using different terminology (e.g., Latham may say “prepare risk factors” while Deloitte says “draft Item 1A disclosures”). That overlap is expected and is resolved in the next step.

**SCOPE GATE (Section 2.1).** During the merge step, exclude any steps that fall outside the scope boundary defined in Section 2.1. Do not carry out-of-scope entries forward for deduplication — remove them at the merge stage. For example, if the scope ends at SEC effectiveness, steps such as pricing, 424(b) filing, closing documents, and settlement are out of scope and must be removed here, not carried through.

## **3.4 Deduplicate and Reconcile Against a Precedent Transaction**

Select a real, filed precedent transaction as a ground-truth reference. For the S-1 flowchart, the Mach Natural Resources LP S-1 filing was used.

Walk the merged list against the precedent filing:

* If two entries from different sources describe the same work, merge them into one step.

* If the precedent filing reveals a step that no source captured, add it.

* If a source lists a step that does not apply to the specific deliverable type (e.g., a corporate IPO step that doesn’t apply to an MLP), remove it.

This merge-and-reconcile process causes the step count to fluctuate — the raw union inflates the count, and deduplication brings it back down. That fluctuation is normal and expected.

**The step count at this stage is preliminary.** It will decrease after LLM capability classification (Section 3.7) drives consolidation of Human and External steps into high-level nodes. Do not treat the post-deduplication count as the final number.

**SCOPE GATE (Section 2.1).** Before presenting the deduplicated list to the user, re-verify that every entry falls within the scope boundary. Remove any out-of-scope entries before presenting.

**WARNING:** LIVE SEARCH REQUIRED. Use SEC EDGAR (https://www.sec.gov/cgi-bin/browse-edgar) or equivalent regulatory databases to locate and access the precedent filing. Search for transaction-specific context that the filing alone may not explain (e.g., entity name changes, concurrent transactions, or unusual structural features).

**TIP:** USER INPUT REQUIRED. When two steps from different sources appear to describe the same work but are not identical, only someone with domain expertise can determine whether they are truly duplicates or two distinct activities. The user must make the merge/split/remove judgment calls during deduplication.

**Propose-and-validate workflow for deduplication flags:** When ambiguous items require user judgment, present them as a numbered flag table with three columns: (a) the issue in one sentence, (b) your default recommendation, and (c) an approve/override column. This enables the user to respond in bulk. Include this response template: “To approve all defaults, reply APPROVE ALL. To override specific items, list only the overrides (e.g., F-3: override to X; F-7: remove).”

**LIVE SEARCH REQUIRED before presenting flags.** Before presenting each flag to the user, conduct a live search to verify your default recommendation. If the search result contradicts your default, revise the default before presenting. Cite the search result that supports your final default in the flag table. Do not rely on training knowledge alone for flag defaults — domain-specific facts (e.g., statutory timing requirements, standard industry practices) may differ from your assumptions.

## **3.5 Selecting the Right Precedent Filing**

**The precedent filing is the single most critical input to the process.** The firm manuals provide the process skeleton — the generic steps and their sequence. But they are written at a level of abstraction that leaves significant gaps when building a granular, step-by-step flowchart. They will say “draft risk factors” but will not tell you how many distinct categories of risk factors a real filing contains, how the Business section is actually structured, what the exact exhibit list looks like, or how the front-of-prospectus summary relates to the detailed sections.

The actual filed document fills those gaps because it is the finished product. You can reverse-engineer the production steps from the output: if the document contains a section, someone had to draft it; if there is an exhibit, someone had to compile it; if a reserve report or comfort letter is referenced, someone had to obtain it. The document itself is the most complete checklist of what had to be produced.

**Not just any precedent filing will do.** The precedent must match the target deliverable on at least two dimensions:

1. **Deliverable type.** An MLP S-1 for an MLP flowchart, a corporate S-1 for a corporate flowchart. The section structure, required exhibits, and disclosure requirements differ materially across entity types. An Oil & Gas MLP S-1 contains reserve disclosures (Reg S-X 4-10(a)), IDR waterfall mechanics, partnership agreement terms, and pass-through tax treatment — none of which appear in a tech company’s corporate S-1.

2. **Full amendment history.** Ideally, provide the original S-1 filing plus all subsequent S-1/A amendments. The original shows what the initial draft looked like. The amendments show how the document evolved in response to SEC comment letters — which directly informed the flowchart’s steps for SEC comment categorization, response letter drafting, and amendment filing. A single snapshot of the final effective version would miss that revision cycle entirely.

**Example:** For the S-1 production flowchart, four filings from the Mach Natural Resources transaction were used: the original S-1 (September 22, 2023\) plus three S-1/A amendments (September 29, October 5, and October 16, 2023).

**WARNING:** LIVE SEARCH REQUIRED. Search SEC EDGAR for recent filings of the same type to identify the best precedent match. Filter by SIC code, filing type, and date range. Compare candidates to select the one most analogous to the target deliverable in terms of entity structure, industry, and transaction complexity.

**Precedent selection procedure:** Search EDGAR full-text search (https://efts.sec.gov/LATEST/search-index?q=) for the 3–5 most recent filings of the same type and same SIC code, filed within the last 24 months. Rank candidates by: (a) closeness of entity structure to the target (e.g., MLP vs. corporate), (b) completeness of the amendment history (prefer filings with 2+ S-1/A amendments, which reveal the SEC review cycle), and (c) quality of counsel and advisors (well-known firms tend to produce more thorough filings that serve as better precedents). Select the candidate with the best combination of these factors.

## **3.6 Assign Single-Role Ownership**

For each deduplicated step, determine which single role currently performs it (see Section 10.1). The role assignments come from the source materials and the precedent transaction — not from abstract reasoning. If a source says “securities counsel drafts risk factors,” that step is assigned to Company Counsel.

Where sources use working-group labels (e.g., “Business Section Working Group”), decompose the working group into its constituent roles and assign the step to the one role that holds the pen or makes the decision. Collaborative involvement by other roles is captured in the RACI matrix, not in the flowchart.

**WARNING:** LIVE SEARCH REQUIRED. When the source materials are ambiguous about which role performs a step, search for practice-specific guidance. For example, whether the FINRA Rule 5110 submission is filed by company counsel or underwriter counsel is a niche practice question that may require searching FINRA guidance or law firm client alerts to resolve.

**Propose-and-validate workflow:** The LLM generates the initial proposed role assignment for every step, then presents the complete list to the user for validation. Do not wait for the user to assign each role. The procedure is:

1. Study the source materials and precedent filing to identify which role each source attributes each step to.

2. Conduct live search for any step where the source materials are ambiguous or silent about which role performs it. Search for practice-specific guidance, law firm client alerts, or regulatory procedures that clarify the responsible party.

3. Propose a single-role assignment for each step, citing the source or search result that supports it.

4. Present the complete proposed role-to-step assignment list to the user for review.

5. The user validates, overrides, or approves each assignment. Genuinely ambiguous cases — where reasonable practitioners would disagree about who holds the pen — require the user's definitive call.

**TIP:** USER INPUT REQUIRED. The user's overrides are final. The LLM's proposals are informed starting points derived from source materials and live search, not determinations.

**Self-audit before presenting.** Before presenting the proposed role assignments to the user, re-verify every entry against the scope boundary (Section 2.1) and remove any out-of-scope entries. Present validation flags (ambiguous cases requiring user judgment) as a numbered table with: (a) the issue in one sentence, (b) your default recommendation, and (c) an approve/override column. Include the response template: "To approve all defaults, reply APPROVE ALL. To override specific items, list only the overrides."

**LIVE SEARCH REQUIRED before presenting flags.** Before presenting each flag to the user, conduct a live search to verify your default recommendation. If the search result contradicts your default, revise the default before presenting. Cite the search result that supports your final default in the flag table. Do not rely on training knowledge alone for flag defaults — domain-specific facts (e.g., statutory timing requirements, standard industry practices) may differ from your assumptions.

## **3.7 Classify by LLM Capability and Expand**

With the deduplicated, role-assigned step list in hand, classify each step into one of the four LLM capability tiers (LLM / Hybrid / Human / External) per Section 2.3. Then expand only the LLM and Hybrid steps into granular sub-steps. Human and External steps remain as single nodes.

The result is the final node list that goes into the Mermaid flowchart.

**WARNING:** LIVE SEARCH REQUIRED. Before classifying a step, you must understand what it actually entails. Search for the specific procedure, tool, or regulatory requirement involved. For example, you cannot determine whether “Edgarize the S-1” is LLM-capable without searching what Edgarization involves (HTML/XBRL tagging, EDGAR-specific formatting, filing system constraints).

**Propose-and-validate workflow:** The LLM generates the initial proposed classification for every step, then presents the complete list to the user for validation. Do not wait for the user to classify each step. The procedure is:

1. Study the source materials and precedent filing to understand what each step actually involves.

2. Conduct live search for any step whose procedure, tooling, or regulatory requirements are not clear from the source materials alone.

3. Propose a tier (LLM / Hybrid / Human / External) for each step, with a brief rationale explaining why.

4. Present the complete proposed classification table to the user for review.

5. The user validates, overrides, or approves each classification. Only after user approval should the chart be expanded.

The user’s overrides are final. The LLM’s proposals are informed starting points, not determinations — the user’s operating environment, risk tolerance, and compliance culture may shift classifications in either direction.

**Self-audit before presenting.** Before presenting the proposed classifications to the user, re-verify every entry against the scope boundary (Section 2.1) and remove any out-of-scope entries. Present validation flags as a numbered table with: (a) the issue in one sentence, (b) your default recommendation, and (c) an approve/override column. Include the response template: “To approve all defaults, reply APPROVE ALL. To override specific items, list only the overrides.”

**LIVE SEARCH REQUIRED before presenting flags.** Before presenting each flag to the user, conduct a live search to verify your default recommendation. If the search result contradicts your default, revise the default before presenting. Cite the search result that supports your final default in the flag table. Do not rely on training knowledge alone for flag defaults — domain-specific facts (e.g., statutory timing requirements, standard industry practices) may differ from your assumptions.

### **3.7.1 Consolidate Human-Tier Steps After Classification**

After classification is validated by the user, consolidate Human-tier steps that share the same role and represent related work into grouped nodes. Multiple prospectus sections drafted by the same role in the same work phase should be combined into a single parent work step (e.g., “Draft Management, Compensation, and Ownership sections” rather than three separate nodes). Apply the same consolidation logic to all tiers — not just Human drafting steps. After consolidation, verify the parent work step count falls within the 60–90 target range (Section 2.4). If it exceeds 90, continue consolidating before proceeding to expansion.

### **3.7.2 Sub-Step Expansion Limits**

When expanding LLM and Hybrid steps into sub-steps, observe these limits:

* **Target 2–3 sub-steps per expanded parent.** Individual exceptions up to 5 are acceptable for genuinely complex steps, but the average across all expanded parents should not exceed 3.

* **After expansion, verify the total node count** (action + decision + milestone) does not exceed 150. If it does, consolidate parent steps before expanding further. The expansion phase should not be used to compensate for insufficient consolidation in earlier stages.

* **Cross-role sub-steps.** During sub-step expansion, a parent step may decompose into sub-steps performed by different roles. Each sub-step node gets its own role color regardless of the parent step’s role assignment. If a sub-step belongs to a different role, it is a standalone node in the flowchart — not visually grouped under the parent’s color.

## **3.8 Build the RACI Matrix During Production**

**The RACI matrix is not just an output deliverable — it is an active quality control instrument during flowchart production.** Build it concurrently with the flowchart, not after. The RACI serves four production functions:

1. Role assignment validation. Declaring R/A/C/I for every node × every role forces you to confront ambiguities that the flowchart alone does not surface — cases where a node is assigned to one role in the chart but another role is actually Responsible, or where an uninvolved role should have been Consulted.

2. Completeness check. The RACI is a flat table where every node gets a row. This makes it easy to spot nodes that exist in the Mermaid code but have no RACI row (or vice versa). It is a cross-reference tool that catches orphans and omissions.

3. Scope discipline. If you cannot fill out a coherent R/A/C/I row for a step, that step may be poorly defined, too vague, or a duplicate. The RACI forces precision in step definitions.

4. Capturing collaborative reality. The flowchart shows only the Responsible party (one color, one role). The RACI is where you document which roles are Consulted (provide input before/during the work) and which are Informed (notified after completion). Without the RACI, this information is lost entirely.

Add each node to the RACI as soon as it is added to the Mermaid code. Do not defer RACI construction to the end of the project — by then, the validation benefits are lost and reconciliation becomes costly. See Section 10.5 for the full RACI construction specification.

# **4\. Basic Mermaid Syntax**

## **4.1 The Flowchart Declaration**

Every flowchart file begins with a YAML front-matter title block, followed by the flowchart declaration and direction:

\---  
title: "S-1 Production Flowchart \- Oil & Gas MLP IPO"  
\---  
flowchart TD

Direction options:

* TD or TB — Top to bottom (standard for process flows; mandatory for this team).

* LR — Left to right.

* RL — Right to left.

* BT — Bottom to top.

**WARNING:** All flowcharts produced under this methodology must use TD (top-down) unless explicitly approved otherwise.

## **4.2 Node Anatomy**

A node consists of three parts: a **name (ID)**, a **shape** (determined by brackets), and **display text** (what appears inside the shape).

NodeName\["Display text that appears in the shape"\]

## **4.3 Connections (Arrows)**

Nodes are connected with arrows:

NodeA \--\> NodeB                    %% solid arrow  
NodeA \--- NodeB                    %% solid line, no arrow  
NodeA \-.-\> NodeB                   %% dashed arrow  
NodeA \--\>|"label text"| NodeB      %% arrow with label  
NodeA \-- "label text" \--\> NodeB    %% alternate label syntax

## **4.4 Branching**

To connect one upstream node to multiple downstream nodes, list the upstream node multiple times:

Decision\_Ready \--\>|Yes| NextStep  
Decision\_Ready \--\>|No| PreviousStep

**TIP:** The second time a node is referenced, you do not need to repeat its shape or display text—just use the node ID.

## **4.5 Line Breaks in Display Text**

Use \<br/\> to insert line breaks inside node display text. This keeps nodes compact:

CompCounsel\_DraftRisks\["Company Counsel: Draft commodity,\<br/\>regulatory & environmental risk factors"\]

## **4.6 Comments**

Use %% for inline comments. Mermaid ignores everything after %% on a line:

%% This is a comment  
%% \============================================  
%% PHASE 1: S-1 Input Assembly (Steps 1-16)  
%% \============================================

## **4.7 Hyperlinks**

To make a node clickable:

click NodeName "https://example.com" "Tooltip text" \_blank

# **5\. Node Shapes**

This methodology uses exactly three node shapes. Do not use any other shapes.

| Shape | Syntax | Use For | Example |
| :---- | :---- | :---- | :---- |
| Rectangle | \["text"\] | Action steps | CompCounsel\_DraftRisks\["Company Counsel: Draft risk factors"\] |
| Diamond | {"text"} | Decision points | Decision\_VDRReady{"VDR ready for S-1 drafting?"} |
| Stadium (rounded) | (\["text"\]) | Start / End milestones | Milestone\_Effective(\["SEC DECLARES EFFECTIVE"\]) |

## **5.1 Decision Diamonds**

Keep decisions binary (Yes/No) whenever possible. If you have more than two branches, chain sequential binary decisions rather than using a multi-branch diamond.

Decision labels on outgoing arrows use the pipe syntax:

Decision\_VDRReady \--\>|Yes| NextStep  
Decision\_VDRReady \--\>|No| LoopBackStep

**Descriptive labels:** When the outcomes have domain-specific names that readers would recognize, use descriptive labels instead of generic Yes/No. Examples: |No Objections| / |Unreasonable| for FINRA decisions, |No \- Stale| / |Yes \- Current| for a staleness check. The descriptive label must still map to a binary structure (two outgoing arrows), but replaces Yes/No with terms that convey domain meaning.

**Self-loops for waiting states:** When a decision node represents a waiting state — where the process polls or pauses until a condition is met — use a self-loop: an arrow from the node back to itself with a descriptive label. Example: SEC\_CommentLetterReceived \--\>|Pending| SEC\_CommentLetterReceived. This visually communicates that the process holds at this gate until the external event occurs.

**Decision diamond density.** Use decision diamonds sparingly — they add visual weight and structural complexity. Target no more than 1 decision diamond per 8–10 action nodes. If multiple sequential steps each have an approval gate (e.g., six individual agreement approvals), consolidate into a single gate after the group is complete rather than inserting individual diamonds. Over-use of decision diamonds inflates the total node count and makes the chart harder to read.

**WARNING:** Decision diamonds and milestones receive default Mermaid styling (no custom color). Only action steps receive role-based colors. See Section 8.4 for the exception for external-party decision diamonds.

# **6\. Node Naming Convention**

Every node ID must follow this exact pattern:

\[RoleAbbreviation\]\_\[TaskName\]

## **6.1 Role Abbreviations**

Use these exact abbreviations (no variations):

| Role | Abbreviation | Example Node ID |
| :---- | :---- | :---- |
| Company Counsel | CompCounsel | CompCounsel\_DraftRisks |
| Issuer (Management) | Issuer | Issuer\_HoldOrgMeeting |
| Underwriters | UW | UW\_JoinAccelRequest |
| Underwriter Counsel | UWCounsel | UWCounsel\_ReviewS1Draft |
| Accountants | Acct | Acct\_CommenceAudit |
| Reserve Engineer | ResEng | ResEng\_PrepareReserveReport |
| Tax Counsel | TaxCounsel | TaxCounsel\_DraftPassThrough |
| SEC / FINRA / Exchange | SEC | SEC\_DeclaresEffective |
| Decision (no role) | Decision | Decision\_VDRReady |
| Milestone (no role) | Milestone | Milestone\_IPOTrigger |

## **6.2 TaskName Rules**

1. Use CamelCase (e.g., DraftRiskFactors, not draft\_risk\_factors).

2. Begin with a verb (Draft, Review, Compile, Verify, Prepare, Flag, File, Submit, etc.).

3. Be specific enough to distinguish from other steps (DraftCommodityRisks, not DraftRisks if multiple risk sections exist).

4. If a role has sub-steps, append a number suffix (e.g., CompCounsel\_DraftRisks1, CompCounsel\_DraftRisks2).

# **7\. Node Display Text**

Display text is what appears inside the rendered shape. It follows this mandatory format:

"Role: Verb \+ object (with context)"

## **7.1 Format Rules**

1. Always begin with the full role name followed by a colon (e.g., Company Counsel:, Issuer:, Accountants:).

2. Follow with a verb \+ object phrase. Use crisp, active-voice language.

3. Add parenthetical context where it helps (source document, regulatory cite, or clarifying detail).

4. Use \<br/\> for line breaks to keep nodes compact. Target 2–3 lines maximum.

**WARNING:** LIVE SEARCH REQUIRED. When drafting display text that includes regulatory citations, technical terms, or procedural details, verify the exact citation or terminology via live search. Writing “Reg S-X 4-10(a)” rather than “SEC reserve rules” requires confirming the precise rule reference. Inaccurate citations undermine the credibility of the entire flowchart.

## **7.2 Good vs. Bad Examples**

| Good (Verb \+ Object) | Bad (Vague / Noun-y / Passive) |
| :---- | :---- |
| "Company Counsel: Draft commodity,regulatory & environmental risk factors" | "Risk factor drafting" |
| "Issuer: Compile acreage, drilling locations,infrastructure from VDR\>Ops" | "Operations data" |
| "Accountants: Prepare Item 8 FS & Notes(PCAOB standards; 3yr non-EGC)" | "Financial statement preparation" |

## **7.3 Decision Node Text**

Decision nodes should be phrased as Yes/No questions:

Decision\_VDRReady{"VDR ready for S-1 drafting?"}  
Decision\_FSCurrent{"Financial statements current?"}

## **7.4 Milestone Node Text**

Milestone nodes should be brief and declarative. The milestone keyword (TRIGGER, END, or equivalent) must be ALL CAPS. The descriptive text that follows may use sentence case for readability. The end milestone should be fully capitalized to signal termination visually.

Milestone\_IPOTrigger(\["TRIGGER: Sponsor decides to pursue IPO"\])  
Milestone\_Effective(\["SEC DECLARES REGISTRATION\<br/\>STATEMENT EFFECTIVE\<br/\>— END —"\])

**TIP:** Start milestones use keyword caps (TRIGGER:) with sentence-case description. End milestones use full caps to provide a strong visual signal that the process is complete.

# **8\. Color System**

## **8.1 Why Colors, and Why This Palette**

Each role gets a unique fill color so the responsible party is identifiable at a glance. This methodology uses the Okabe-Ito colorblind-safe palette exclusively, for two reasons:

1. It provides 8 visually distinct colors that remain distinguishable under the most common forms of color vision deficiency (deuteranopia, protanopia), covering approximately 8% of the male population.

2. It provides exactly 8 colors for exactly 8 roles — a clean one-to-one mapping with no ambiguity.

The text color rule (white text on dark fills, black text on light fills) is also an accessibility decision, ensuring sufficient contrast for readability regardless of the background color.

Do not substitute, add, or modify colors without explicit approval.

## **8.2 Color-to-Role Mapping**

**Deriving the role taxonomy:** Extract all distinct parties named in the precedent filing’s cover page, signature pages, legal opinion exhibits, comfort letter references, and expert consents. Each distinct functional role becomes one entry in the taxonomy. For the S-1 production flowchart, this yielded 8 roles: Company Counsel, Issuer (Management), Underwriters, Underwriter Counsel, Accountants, Reserve Engineer, Tax Counsel, and SEC/FINRA/Exchange. A different deliverable type may yield fewer or more roles.

| Role | Fill Color | Stroke | Text Color | Hex Code |
| :---- | ----- | :---- | :---- | :---- |
| Company Counsel | \#0072B2 | \#000000 | \#FFFFFF | Blue |
| Issuer (Management) | \#E69F00 | \#000000 | \#000000 | Orange |
| Underwriters | \#56B4E9 | \#000000 | \#000000 | Sky Blue |
| UW Counsel | \#009E73 | \#000000 | \#FFFFFF | Bluish Green |
| Accountants | \#F0E442 | \#000000 | \#000000 | Yellow |
| Reserve Engineer | \#D55E00 | \#000000 | \#FFFFFF | Vermillion |
| Tax Counsel | \#CC79A7 | \#000000 | \#000000 | Reddish Purple |
| SEC/FINRA/Exchange | \#000000 | \#000000 | \#FFFFFF | Black |

## **8.3 Style Syntax**

Colors are applied via style statements at the bottom of the Mermaid file, after all node and connection definitions:

%% \--- Company Counsel (Blue \#0072B2) \---  
style CompCounsel\_DraftRisks stroke:\#000,fill:\#0072B2,color:\#FFF

%% \--- Issuer / Management (Orange \#E69F00) \---  
style Issuer\_HoldOrgMeeting stroke:\#000,fill:\#E69F00,color:\#000

## **8.4 What NOT to Style**

Decision diamonds and milestone nodes receive default Mermaid styling. Do not assign colors to them. This ensures they are visually distinct from role-based action steps.

**Exception — external-party decision diamonds:** When a decision diamond represents an external party’s action or determination (not an internal process gate), style it with that party’s role color. This applies to regulatory gates where showing the responsible external party adds information — e.g., SEC comment letter decisions styled black (\#000000). These styled diamonds still use the diamond shape and are still counted as decision nodes, but their color communicates that an outside party controls the outcome.

# **9\. Structure & Organization**

## **9.1 Subgraphs (Phases)**

Use subgraphs to group nodes into logical phases or sections. Subgraphs render as labeled boxes around their child nodes:

subgraph P1\["Phase 1: S-1 Input Assembly"\]

    subgraph P1A\["VDR Readiness"\]  
        Milestone\_IPOTrigger(\["TRIGGER: Sponsor decides to pursue IPO"\])  
        Issuer\_EstablishVDR\["Issuer: Establish & populate VDR folders"\]  
    end

    subgraph P1B\["Section Assignment & Kickoff"\]  
        Issuer\_AssignSectionOwners\["Issuer: Assign S-1 section owners"\]  
    end

end

**TIP:** Subgraphs can be nested. Use a parent subgraph for each major phase and child subgraphs for sub-phases within it.

**Target phase count.** For a single-deliverable flowchart, target 4–8 top-level phases. If you exceed 8, consider whether phases can be combined or whether sub-phases (nested subgraphs) are more appropriate. Excessive phase counts fragment the visual structure and make the chart harder to navigate.

**Subgraph naming convention:** Subgraph IDs follow a hierarchical pattern: P \+ phase number for top-level phases (P1, P2, P3), and P \+ phase number \+ letter suffix for sub-phases (P1A, P1B, P2A). This mirrors the nesting structure and keeps IDs short.

## **9.2 Parallel Workstreams (Fan-Out / Fan-In)**

Real-world processes are not purely sequential. After certain trigger points, multiple independent workstreams kick off simultaneously and run in parallel until their outputs converge at a downstream integration point. The flowchart must represent this accurately.

**Fan-out:** One node connects to multiple downstream nodes, each representing an independent parallel track. This is coded by listing the upstream node multiple times with different targets:

Issuer\_HoldOrgMeeting \--\> ResEng\_PrepareReserveReport  
Issuer\_HoldOrgMeeting \--\> Acct\_CommenceAudit  
Issuer\_HoldOrgMeeting \--\> CompCounsel\_ReviewMatlContracts  
Issuer\_HoldOrgMeeting \--\> Issuer\_CompileOpsData

**Fan-in:** Multiple parallel tracks converge back into a single node when their outputs are needed together for the next step:

CompCounsel\_DraftBizStrategy \--\> Decision\_SectionsConsistent  
Acct\_PrepareFinStmts \--\> Decision\_SectionsConsistent  
TaxCounsel\_VerifyTaxAccuracy \--\> Decision\_SectionsConsistent

Without fan-out/fan-in, the chart artificially serializes activities that actually happen concurrently. This misrepresents the real timeline, makes the process look much longer than it is, and obscures the fact that different roles are working independently during the same period.

**WARNING:** Do not serialize steps that are actually parallel just because it produces a cleaner vertical line. If activities are independent of each other, they must branch and converge. Ask: “Does Step B truly require Step A’s output to begin, or can they run at the same time?” If they can run simultaneously, fan out.

**TIP:** USER INPUT REQUIRED. Logical independence and practical independence are not the same thing. Only someone who has lived through the production process knows the real dependencies — for example, whether the reserve engineer actually starts before or after the organizational meeting, or whether auditors wait for certain VDR materials before commencing. The user must validate which steps are truly parallel vs. sequential.

## **9.3 Code Layout Order**

Organize your Mermaid file in this exact order:

1. YAML front-matter (title block).

2. Flowchart declaration (flowchart TD).

3. Subgraph definitions with all nodes declared inside them.

4. Connection statements (after all subgraphs, grouped by phase).

5. Style definitions (at the very end, grouped by role).

Use comment banners to separate sections:

%% \============================================================  
%% PHASE 1: S-1 Input Assembly  
%% \============================================================

## **9.4 Connection Placement**

Place all connection statements outside of subgraphs, after the subgraph definitions. Group them by phase with comment headers. This keeps the subgraph blocks clean and makes the flow logic easy to audit.

**Cross-phase connections:** Connections that span across phase boundaries — where an arrow connects a node in one phase to a node in a different phase — are expected, particularly for feedback loops (e.g., a failed staleness check in Phase 5 routing back to an amendment step in Phase 4). Group cross-phase connections with the originating phase’s connection block. Add a comment noting the target phase for clarity.

## **9.5 Style Placement**

Place all style statements at the very end of the file, grouped by role with comment headers. This makes it easy to verify color assignments during review.

**Style section legend:** Before the first style statement, include a comment block listing every role, its color name, hex code, text color, and which node categories receive default styling. This serves as an in-code reference for anyone editing the file:

%% \============================================================  
%% STYLE DEFINITIONS — Okabe-Ito Colorblind-Safe Palette  
%% \============================================================  
%%  
%% Color Legend (8 roles):  
%% Company Counsel          \= Blue           \#0072B2  (white text)  
%% Issuer (Management)      \= Orange         \#E69F00  (black text)  
%% Underwriters             \= Sky Blue       \#56B4E9  (black text)  
%% Underwriters' Counsel    \= Bluish Green   \#009E73  (white text)  
%% Accountants              \= Yellow         \#F0E442  (black text)  
%% Reserve Engineer         \= Vermillion     \#D55E00  (white text)  
%% Tax Counsel              \= Reddish Purple \#CC79A7  (black text)  
%% SEC/FINRA/Exchange       \= Black          \#000000  (white text)  
%%  
%% Decision diamonds: default Mermaid styling (except external-party diamonds)  
%% Start/End milestones: default Mermaid styling

After the legend, group style statements by role with comment headers:

%% \--- Company Counsel (Blue \#0072B2) \---  
style CompCounsel\_ReviewMatlContracts stroke:\#000,fill:\#0072B2,color:\#FFF  
style CompCounsel\_ReviewRelPartyTxn stroke:\#000,fill:\#0072B2,color:\#FFF  
...

%% \--- Issuer / Management (Orange \#E69F00) \---  
style Issuer\_EstablishVDR stroke:\#000,fill:\#E69F00,color:\#000  
...

# **10\. Handoffs & Responsibilities**

Failures in real-world workflows most often occur at transitions between people or teams. The flowchart must make handoffs painfully explicit.

## **10.1 Single-Role Ownership, Not Working Groups**

In practice, complex transactions organize around working groups — cross-functional teams where counsel, management, bankers, and accountants all collaborate on the same sections. However, working groups defeat the purpose of the flowchart. A working group is not a single accountable party; it is a collection of roles.

The rule is: assign each step to the one role that currently performs it. One node, one color, one responsible party. The collaborative reality — multiple roles consulting, reviewing, or being informed — is captured in the companion RACI matrix (C and I columns), not in the flowchart.

This single-role ownership principle is what makes the color system work. Without it, nodes would need multiple colors or ambiguous labels, and the chart would lose its ability to show accountability at a glance.

## **10.2 Scope Determines Role Distribution**

Once you assign single-role ownership, the resulting distribution of steps across roles is a direct consequence of the scope decision (Section 2.1). Expect it to be lopsided — and resist the impulse to “rebalance” it.

**Example:** In the S-1 production flowchart, Company Counsel owns 44 of 76 steps while Underwriters own only 1\. This initially seemed wrong, but it was correct: the S-1 is a legal document, so counsel holds the pen for most of it. The underwriters’ heavy lifting (book building, pricing, allocation) happens outside S-1 production. Had the scope been “the IPO” rather than “the S-1,” the distribution would look entirely different.

A seemingly lopsided role distribution should be interrogated against the scope, not artificially balanced. If it tracks to the deliverable being mapped, it is correct.

**Distribution validation procedure:** If the role distribution appears lopsided, cross-check each high-count role’s steps against the deliverable’s section structure. For every step assigned to the dominant role, confirm it maps to a distinct section, exhibit, or activity in the precedent filing. If each step has a unique counterpart in the filing, the distribution is correct. If steps appear duplicative or artificially split, consolidate them. The distribution is a diagnostic output of the methodology, not a target to be engineered.

## **10.3 In-Chart Handoff Rules**

1. Label every action node with the primary role performing it (via both the display text prefix and the node color).

2. When a handoff occurs (Role A to Role B), ensure the arrow clearly connects the two differently-colored nodes.

3. For decision-based handoffs, use labeled arrows (Yes/No) so the reader knows which outcome triggers the handoff.

## **10.4 Companion Deliverables**

The flowchart alone cannot capture all handoff detail. Pair it with:

* A RACI matrix (8 roles × all steps) — see Section 10.5 for the full construction specification.

* A companion table with step-level detail: current owner, LLM-capable flag, inputs/outputs, and source documents.

* A legend/glossary defining role colors, abbreviations, and domain terms.

**TIP:** The flowchart shows who currently performs each step. LLM-capable designations and other metadata go in the companion table, never in the flowchart itself.

## **10.5 RACI Matrix Construction Specification**

This section defines the structure, assignment rules, and validation requirements for building a RACI matrix that matches the flowchart.

### **10.5.1 Workbook Structure**

The RACI workbook contains three sheets:

1. RACI Matrix — the primary grid (one row per node, one column per role).

2. Legend — RACI definitions, role color key, and interpretive notes.

3. Summary — role × R/A/C/I count matrix, mechanically derived from the RACI Matrix sheet.

### **10.5.2 RACI Matrix Sheet Layout**

The RACI Matrix sheet has 13 columns:

| Column | Header | Content |
| :---- | :---- | :---- |
| A | \# | Sequential number (1 to N). Blank for phase separator rows. |
| B | Phase | Phase or sub-phase name (e.g., VDR Readiness, Phase 2B: S-1 Prospectus Drafting). |
| C | Node ID | Exact node ID from the Mermaid code (e.g., CompCounsel\_DraftRisks). Blank for phase separator rows. |
| D | Step Description | Display text from the Mermaid node (without \<br/\> tags). |
| E | Type | ACTION, DECISION, or MILESTONE. |
| F–M | Role columns | One column per role (Company Counsel, Issuer (Mgmt), Underwriters, UW Counsel, Accountants, Reserve Engineer, Tax Counsel, SEC/FINRA/Exch). Each cell contains R, A, C, I, or blank. |

**Phase separator rows:** Insert a row with no number, no Node ID, no Type, and no RACI values at the start of each phase or sub-phase. The Phase column contains the phase name. These rows visually group the matrix by phase.

### **10.5.3 RACI Assignment Rules**

**Responsible (R):** The one role that performs the work. Must match the flowchart’s color assignment for that node. Every ACTION node gets exactly one R.

**Accountable (A):** The role that approves or owns the outcome. Follows these rules:

| If R is... | Then A is... | Rationale |
| :---- | :---- | :---- |
| Company Counsel | Issuer (Mgmt) | Registrant has Section 11 liability |
| Accountants | Issuer (Mgmt) | Registrant engages the auditors |
| Tax Counsel | Issuer (Mgmt) | Registrant is the taxpayer |
| Reserve Engineer | Issuer (Mgmt) | Registrant owns the reserves |
| UW Counsel | Underwriters | UWs engage their own counsel |
| Issuer (Mgmt) | (none shown) | R and A are the same party (see Note 5\) |
| SEC/FINRA/Exchange | (none) | External regulatory actions (see Note 4\) |
| Underwriters | (none shown) | R and A are the same party (see Note 5\) |

**Consulted (C):** Roles that provide input before or during the work. Assign C when:

* The step’s output feeds directly into another role’s subsequent work.

* The step requires technical input from a specialist (e.g., Tax Counsel consulted on tax-related disclosures drafted by Company Counsel).

* The step involves terms or provisions that affect another party’s interests.

**Informed (I):** Roles that are notified of the outcome after completion. Assign I when:

* The step has regulatory or filing implications that affect another role’s timeline.

* The step produces an output that another role will need to reference later (but does not need their input now).

* The step represents a milestone or status change that the broader working group should know about.

**Decision and milestone nodes:** Leave all RACI cells blank. These are process control points, not work steps.

**Propose-and-validate workflow for C/I assignments:** The Responsible (R) and Accountable (A) assignments follow deterministic rules (the tables above). The Consulted (C) and Informed (I) assignments require domain judgment. The LLM generates the initial proposed C/I assignments for every action node, then presents the complete matrix to the user for validation. The procedure is:

1. Study the source materials and precedent filing to understand the collaborative relationships between roles — which roles provide input to which steps, and which roles need to know about which outcomes.

2. Conduct live search for any step where the collaborative relationships are not clear. Search for how working groups are typically structured for this deliverable type, which roles attend which review cycles, and which regulatory filings trigger notification obligations.

3. Apply the C and I heuristics above to propose assignments for every action node × every role.

4. Present the complete proposed RACI matrix (including R, A, C, and I) to the user for review.

5. The user validates, overrides, or approves the C/I assignments. The user may identify consulting or notification relationships that the source materials do not document.

### **10.5.4 Legend Sheet**

The Legend sheet contains three sections:

1. RACI Definitions — R (Responsible: performs the work), A (Accountable: approves/owns the outcome), C (Consulted: provides input before/during), I (Informed: notified after completion).

2. Role Color Key — the Okabe-Ito hex code and role name for each of the 8 roles (must match Section 8.2).

3. Interpretive Notes — document any rules that govern how the RACI should be read. At minimum, include:

* Decision and milestone nodes have no RACI assignments (process control points).

* Issuer (Management) is Accountable for most steps as the registrant with Section 11 liability.

* Underwriters are Accountable for UW Counsel steps as the engaging party.

* SEC/FINRA/Exchange steps have no separate Accountable — external regulatory actions.

* Where a role is both R and A, only R is shown.

### **10.5.5 Summary Sheet**

The Summary sheet is a role × R/A/C/I count matrix, mechanically derived from the RACI Matrix sheet. It has 5 columns (Role, R count, A count, C count, I count), one row per role, and a Total row. All values are computed by counting the corresponding letter in each role’s column across all ACTION rows. This sheet is fully automatable and should be regenerated whenever the RACI Matrix changes.

## **10.6 Summary Slide Specification**

The summary slide is a single-page visual overview of the entire deliverable package. It serves as the entry point for stakeholders who need to understand the scope, structure, and LLM opportunity at a glance before diving into the flowchart or RACI. Most of its content is derived mechanically from the flowchart, RACI, and step classification table.

### **10.6.1 Layout Architecture**

The slide uses a 3-column layout on a single widescreen (16:9) slide:

| Column | Width | Content |
| :---- | :---- | :---- |
| Left | \~25% of slide width | Context definitions \+ LLM Opportunity panel |
| Center | \~45% of slide width | Phase bar \+ flowchart thumbnail \+ stats \+ RACI link |
| Right | \~30% of slide width | Roles legend \+ Key Terms glossary |

Above all three columns, a header bar spans the full slide width containing the title, deliverable type, and attribution.

### **10.6.2 Header Bar**

* Left-aligned title: the deliverable name \+ em dash \+ entity/transaction type (e.g., “S-1 Production Flowchart — Oil & Gas MLP IPO”).

* Right-aligned attribution: the role and name of the deliverable owner (e.g., “VDR Captain: Ezequiel Padilla”). This is a user-supplied field.

**TIP:** USER INPUT REQUIRED. The attribution name and title must be provided by the user.

### **10.6.3 Left Column — Context Definitions**

The left column contains three short context boxes that define the key concepts for a non-specialist reader:

1. Entity type definition — 2–3 sentences explaining what the entity type is (e.g., what an MLP is) in plain, accessible language. Assume the reader has no background in the domain.

2. Deliverable type definition — 2 sentences explaining what the deliverable is (e.g., what an S-1 is) and what it contains.

3. Flowchart purpose statement — 1–2 sentences stating what the flowchart maps, with key stats: total work steps, number of roles, and approximate timeline.

**WARNING:** LIVE SEARCH REQUIRED. If you are unfamiliar with the entity type or deliverable type, search for plain-language definitions before writing these boxes. The definitions must be accurate and accessible.

### **10.6.4 Left Column — LLM Opportunity Panel**

Below the context boxes, display the LLM opportunity breakdown. This is derived mechanically from the step classification table:

* Header: “LLM OPPORTUNITY” in accent color (Okabe-Ito blue \#0072B2).

* For each of the 4 tiers (LLM, Hybrid, Human, External), display: percentage \+ step count \+ tier label.

* Percentages are computed on the parent work-step basis (not total nodes). Use the counting denominator defined in Section 11.1.

* Each tier is separated by a colored underline: blue for LLM, orange for Hybrid, neutral for Human, gray for External.

### **10.6.5 Center Column — Phase Bar**

A horizontal row of colored boxes showing each phase’s abbreviated name (e.g., “P1: VDR & Setup”, “P2: S-1 Drafting”). Derive phase names from the flowchart’s top-level subgraphs. Use the Okabe-Ito blue (\#0072B2) as the box fill with white text.

### **10.6.6 Center Column — Flowchart Thumbnail**

Embed a small-scale rendering of the complete Mermaid flowchart as an image. This provides a visual preview of the chart’s structure, density, and color distribution.

**Procedure:** Render the Mermaid code in mermaid.live. Export as PNG at sufficient resolution (minimum 1200px wide). Embed in the center column at thumbnail scale, sized to show the overall shape and color patterns without requiring readability of individual node text.

### **10.6.7 Center Column — Stats and Links**

Display three key stats derived from the flowchart:

* Total parent work steps (e.g., “76 work steps”).

* Total decision diamonds (e.g., “12 decisions”).

* Total phases (e.g., “6 phases”).

Include two functional hyperlinks:

* “Open Flowchart” — links to the Mermaid live rendering or the canonical Mermaid code file.

* “RACI Matrix: \[filename\]” — links to the RACI workbook file.

### **10.6.8 Right Column — Roles Legend**

Derived mechanically from the flowchart and RACI:

* Header: “ROLES (N)” in accent color (Okabe-Ito orange \#E69F00), where N is the number of roles.

* One row per role: Okabe-Ito color swatch \+ role name \+ step count on the parent work-step basis.

* Step counts must match the RACI Summary sheet’s R column and the flowchart’s style statement counts (per the cross-deliverable coherence rules in Section 11.1).

### **10.6.9 Right Column — Key Terms Glossary**

A glossary of 10–15 domain-specific terms that appear in the flowchart and would be unfamiliar to a general business audience.

* Header: “KEY TERMS” in accent color (Okabe-Ito orange \#E69F00).

* Each entry: term in colored monospace font \+ one-line plain-language definition in gray.

* Term colors should use the Okabe-Ito palette where the term is associated with a specific role (e.g., “VDR” in orange for Issuer, “Section 11” in blue for Company Counsel). General terms use a neutral color.

**WARNING:** LIVE SEARCH REQUIRED. Verify the accuracy of every term definition via live search. Domain terms have precise legal or regulatory meanings that must not be approximated.

**Term selection procedure:** Scan all node display text in the Mermaid code for acronyms, legal citations, and technical terms. Select terms that: (a) appear multiple times in the flowchart, (b) are essential to understanding the process, and (c) would not be known to a general business reader. Exclude terms that are self-explanatory from context.

### **10.6.10 Visual Design Standards**

* Accent colors: use Okabe-Ito blue (\#0072B2) for the title, phase bar, and LLM-related headers. Use Okabe-Ito orange (\#E69F00) for section headers (ROLES, KEY TERMS).

* Fonts: use a clean sans-serif (e.g., Arial, Calibri) for body text. Use monospace (e.g., Consolas, Courier New) for key terms.

* Color swatches in the Roles legend must use the exact Okabe-Ito hex codes from Section 8.2.

* The slide must be legible when projected or viewed on screen. Minimum body text size: 10pt. Minimum header size: 14pt.

* No decorative elements. Every visual element must convey information.

### **10.6.11 Visual Specification — Panel Formatting Rules**

These rules address how each panel should look, not just what it contains. Apply these in addition to the content specifications in Sections 10.6.2–10.6.10.

**Left Column — Definitions:**
* Write definitions in practitioner plain-English, not statutory or textbook language. Write as if explaining to a first-year associate, not citing a statute. Example: "An MLP is a publicly traded partnership — not a corporation — that typically owns midstream oil & gas infrastructure. Pass-through tax; K-1s, not 1099s." Not: "A Master Limited Partnership (MLP) is an exchange-traded limited partnership that earns ≥90% of gross income from qualifying natural resource activities under IRC §7704."
* Do not use section subheadings (e.g., "ENTITY TYPE", "DELIVERABLE TYPE", "FLOWCHART PURPOSE") within the left column. Instead, use bold lead-in phrases: "**An MLP**…", "**An S-1**…", "**This flowchart**…".

**Left Column — LLM Opportunity Panel:**
* Each LLM tier row uses a colored horizontal bar (matching the tier's accent color) with the percentage in large bold type, the step count in parentheses, and the tier label below. Do not use plain text lists or horizontal rule separators.

**Center Column — Phase Bar:**
* Phase bar boxes must accommodate the full phase name without truncation. If the flowchart has more than 8 phases, abbreviate phase names to fit (e.g., "P3: VDR & DD" not "P3: VDR Assembly & Due Diligence") or use a two-row layout.

**Center Column — Thumbnail:**
* The LLM should leave a sized placeholder with dimensions matching the center column width (~45% of slide width) and approximately 50% of slide height. Include the instruction text: "Render in mermaid.live → Export as PNG → Insert here."

**Center Column — Stats:**
* Stats (parent work steps, decisions, phases) stack vertically to the left of the thumbnail, not horizontally below it. Use 28–36pt bold for numbers with a small label below each. Do not use display-size type (60pt+).

**Right Column — Role Swatches:**
* Role swatches must use the exact Okabe-Ito hex values from Section 8.2. Provide the hex codes as a lookup table in the pptxgenjs code. Verify rendered swatch colors match the flowchart node colors.

**Right Column — Key Terms:**
* Each term uses monospace bold for the abbreviation, rendered in an Okabe-Ito accent color (orange \#E69F00), followed by a space and a plain-text definition of ≤10 words on the same line.
* Include practitioner shorthand alongside regulatory terms. The target audience knows the law but not necessarily deal-execution jargon. Examples of practitioner terms to include: red herring, gun-jumping, comfort letter, DRS.

**Footer:**
* The precedent citation belongs in the flowchart purpose statement (left column), not in a separate footer bar. If a footer is used, limit it to file references only.

**Column Weight:**
* The center column (thumbnail + stats + hyperlinks) should carry approximately 45% of the visual weight. Left and right columns are reference panels, not primary content areas.

# **11\. Validation & Testing**

Before a flowchart is considered complete, run through this checklist:

1. Paste the full code into mermaid.live and confirm it renders without errors.

2. Verify every node is connected (no orphan nodes floating disconnected).

3. Confirm every action node has a style statement assigning its role color.

4. Confirm decision diamonds and milestones have no style statements, except for external-party decision diamonds which are styled per Section 8.4.

5. Verify all node IDs follow the \[RoleAbbrev\]\_\[TaskName\] naming convention.

6. Verify all display text follows the "Role: Verb \+ object" format.

7. Check that all decision branches are labeled (Yes/No or descriptive labels per Section 5.1).

8. Walk the happy path from start milestone to end milestone to confirm logical completeness.

9. Cross-reference against the RACI matrix: every node in the flowchart must have a corresponding RACI row, and vice versa.

10. Test all subgraph boundaries: every node should appear inside the correct phase subgraph.

11. Scope boundary verification: confirm every node falls within the scope defined in Section 2.1. Any node whose trigger event occurs after the end milestone is out of scope and must be removed.

12. Step count verification: confirm the parent work step count is within the 60–90 target range (Section 2.4) and the total node count does not exceed 150 (Section 3.7.2). If either limit is exceeded, investigate whether upstream consolidation was insufficient before proceeding.

## **11.1 Cross-Deliverable Coherence**

A flowchart is typically one deliverable in a larger package that includes a RACI matrix, a summary slide, a step classification table, and possibly a companion table. All deliverables must reconcile to the same numbers. Inconsistencies between deliverables erode credibility and trigger costly reconciliation rework.

**The root problem: multiple valid counting methodologies.** A single flowchart can be counted several ways:

* Total nodes (action steps \+ decision diamonds \+ milestones).

* Parent work steps only (excluding sub-steps created during LLM/Hybrid expansion).

* Action nodes only (excluding decisions and milestones).

* Steps per role (a subset of any of the above).

Each of these is a valid count, but they produce different numbers from the same chart. If the summary slide uses one basis, the RACI uses another, and the Mermaid code implies a third, every reviewer will flag a discrepancy.

**The rule:** Define your counting denominator once, at the start of the project, and document it explicitly. Every deliverable must reference the same basis. When a deliverable requires a different count (e.g., the RACI lists all 123 nodes while the summary slide reports 76 parent work steps), state the basis and the relationship between the two counts in that deliverable.

**Example:** The S-1 production flowchart has 123 total nodes (109 action \+ 12 decision \+ 2 milestone). It also has 76 parent work steps (the basis used on the summary slide). The RACI matrix lists all 123 nodes. The summary slide states “76 parent work steps” with a footnote explaining the relationship to 123 total nodes. Both numbers are correct; the basis is documented in each deliverable.

Before delivering any output, verify:

* Every node in the Mermaid code has a corresponding row in the RACI matrix, and vice versa.

* Every count cited in a summary slide or companion document matches the defined basis.

* Role-level counts (e.g., Company Counsel: 44 steps) are consistent across all deliverables that report them.

* If any deliverable was updated independently (e.g., a node was added to the Mermaid code), all other deliverables have been updated to match.

* The RACI’s Responsible (R) column must exactly match the flowchart’s role-color assignments. If a node is blue (Company Counsel) in the chart, it must have R under Company Counsel in the RACI. Any mismatch indicates an error in one or both deliverables.

**WARNING:** LIVE SEARCH REQUIRED. During validation, verify that the sequence of steps reflects current actual practice. Search for current SEC review timelines, FINRA processing procedures, exchange listing requirements, and any recent rule changes that may affect the accuracy of the flowchart. A chart that follows all coding conventions but misrepresents the actual process is a failure.

**TIP:** USER INPUT REQUIRED. The user is the ultimate quality gate. An LLM can check syntax, orphan nodes, and naming conventions, but only the user can confirm that the flowchart represents the actual process as practiced — not just as described in manuals. The user must perform the final accuracy review before the flowchart is considered complete.

# **12\. Quick Reference Card**

## **12.1 Shape Cheat Sheet**

| Element | Syntax | When to Use |
| :---- | :---- | :---- |
| Rectangle | ID\["text"\] | Action steps (the vast majority of nodes) |
| Diamond | ID{"text"} | Decision points (labeled gates) |
| Stadium | ID(\["text"\]) | Start/End milestones only |
| Subgraph | subgraph ID\["label"\] ... end | Phase/section grouping |
| Arrow | A \--\> B | Flow connection |
| Labeled arrow | A \--\>|"Yes"| B | Decision branches |
| Style | style ID stroke:...,fill:...,color:... | Role color assignment |

## **12.2 External Resources**

* Mermaid Official Documentation: https://mermaid.js.org/syntax/flowchart.html

* Mermaid Live Editor: https://mermaid.live

* Mermaid Tutorials: https://mermaid.js.org/ecosystem/tutorials.html

* Okabe-Ito Color Palette Reference: https://jfly.uni-koeln.de/color/