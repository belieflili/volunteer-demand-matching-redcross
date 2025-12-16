🎯 Purpose

Identify operational risk signals for each shift based on simple, explicit, and auditable rules.

This prompt documents the human decision rationale used in routine operational review.
It does not make staffing decisions, rank individuals, or recommend actions.

Prompt 01 acts as a risk signal layer, not a decision-maker.

📥 Input
Data source

File: 01_risk_flags.xlsx

Table: tbl_risk_flags

Fields used
Field	Description
Date	Shift date
Time Slot	Morning / Midday / Afternoon / Evening
Planned Headcount	Required staffing level
Actual Headcount	Observed staffing level
Must-have Skills Missing	Yes / No
Single-point Skill Risk	Yes / No
Workload Level	Low / Normal / High

All inputs are treated as observed operational facts.
No inference is performed on individual performance.

🧠 Risk Flagging Logic

(Explicit, rule-based, human-interpretable)

1️⃣ Identify risk signals

A shift is considered to have a risk signal if any of the following conditions are met:

Must-have Skills Missing = Yes

Single-point Skill Risk = Yes

These conditions represent capability or resilience risk,
not individual error or responsibility.

2️⃣ Assign risk level
Condition	Risk Flag
Risk signal present AND Workload Level = High	Red
Risk signal present AND Workload Level ≠ High	Amber
No risk signal present	Green

This mapping reflects how a human operator would assess severity,
given the same inputs.

📘 Interpretation Guidelines

Green
No immediate capability or resilience risk detected under the observed workload.

Amber
A potential risk signal is present.
Human attention or monitoring may be required.

Red
High likelihood of operational failure if the risk signal remains unaddressed under high workload.

⚠️ Risk flags are signals for human review,
not automated decisions or actions.

📤 Output

For each shift record, Prompt 01 outputs:

1️⃣ Risk Flag

Green / Amber / Red

2️⃣ Triggered Rules

A list of explicit rule codes indicating which conditions were met:

MUST_HAVE_SKILL_MISSING

SINGLE_POINT_SKILL_RISK

WORKLOAD_HIGH

This list constitutes the primary decision evidence.

3️⃣ Risk Reason (optional, human-readable)

Generated only from the triggered rule codes

Uses fixed, deterministic templates

No free-form or additional inference allowed

Example:

Single-point skill risk; High workload

📌 Risk Reason reflects the human decision rationale implied by triggered rules.
It does not represent independent machine reasoning.

🚫 Explicit Constraints

Do not assess, rank, or comment on individuals

Do not generate staffing changes or recommendations

Do not override or reinterpret input data

Do not introduce new reasoning beyond the defined rules

All outputs must remain:

Transparent

Auditable

Reversible

🧩 Role in the Overall System

Prompt 01 provides a lightweight, front-line risk signal layer for:

Prompt 02 — Targeted support or adjustment recommendations

Prompt 03 — Manager-level operational summaries

Prompt 04 — Retrospective review of staffing rules and false signals

Prompt 01 is intentionally conservative and minimal.
Later prompts may reinterpret, challenge, or override its outputs.
