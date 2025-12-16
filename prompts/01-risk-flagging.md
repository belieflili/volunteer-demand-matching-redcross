Prompt 01 — Risk Flagging (Final, Portfolio Version)
🎯 Purpose

Identify operational risk signals for each shift based on simple, explainable rules and observed conditions.
This prompt does not make staffing decisions and does not evaluate individuals.

📥 Input
Data source

01_risk_flags.xlsx
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
🧠 Risk Flagging Logic (Explainable Rules)

For each time slot, apply the following logic:

1️⃣ Identify risk signals

A shift is considered at risk if any of the following is true:

Must-have Skills Missing = Yes

Single-point Skill Risk = Yes

These conditions indicate capability-related risk, not individual performance.

2️⃣ Assign risk level
Condition	Risk Flag
Risk signal present AND Workload Level = High	Red
Risk signal present AND Workload Level ≠ High	Amber
No risk signal present	Green
3️⃣ Interpretation guidelines

Green: Staffing and skills are sufficient for the observed workload.

Amber: Potential risk detected; monitoring or minor adjustment may be required.

Red: High likelihood of operational failure if unaddressed.

Risk flags are signals for human review, not automated decisions.

📤 Output

For each shift record:

Risk Flag: Green / Amber / Red

Risk Reason: Short, descriptive explanation (e.g. Single-point skill risk; High workload)

🚫 Explicit constraints

Do not rank or assess individuals.

Do not generate rosters or staffing changes.

Keep all rules simple, transparent, and auditable.

🧩 Role in the system

Prompt 01 provides the risk signal layer for:

Prompt 02 (targeted support recommendations)

Prompt 03 (manager operational summary)

Prompt 04 (staffing rule retrospective review)
