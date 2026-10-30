---
name: missing-report-checker
description: Use this to find which working days each employee did not send a report. A single missing report is a red flag.
---

# Missing Report Checker

## Purpose
Find missed reports for each employee in the date window (normally the last 7 to 8 days).

## Inputs
- Employee list.
- Parsed reports with their dates.
- The leader's holiday list, if provided.

## Rules
- Working days are Monday to Friday, unless the leader says otherwise. Saturdays and Sundays are not counted.
- Dates in the leader's holiday list are not counted.
- If no holiday list was given, count only weekends as non-working and state this assumption in the result.
- A working day with no report from an employee is a missed report.
- A single missed report is a red flag.
- If a report arrived on the next day instead of the correct day, mark the original day "late" and the employee still counts as having reported. Mention it as a pattern note.
- If the data does not cover the date, say "insufficient data" instead of marking it missed.

## Steps
1. List every working day in the window.
2. For each employee and each working day, check whether a parsed report exists.
3. Record missed days, late days and the longest run of consecutive missed days.

## Output
For each employee:
- Employee name
- Working days checked
- Reports received
- Missed dates
- Late dates
- Longest consecutive miss run
- Status: RED FLAG if any missed date, otherwise OK
- Assumptions used (for example "no holiday list provided")
