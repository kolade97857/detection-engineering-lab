# Detection Engineering Lab

A hands-on detection engineering project using Windows Sysmon telemetry, Sigma rules, Splunk SPL, controlled testing, and investigation notes.

## Goals
- Create Sigma rules and Splunk implementations.
- Validate detections against controlled lab activity.
- Document observed results, limitations, and false-positive considerations.
- Map relevant behavior to MITRE ATT&CK.

## Layout
- `sigma-rules/` — portable detection rules.
- `splunk-spl/` — Splunk searches.
- `test-cases/` — test procedures and results.
- `investigations/` — investigation notes and templates.
- `evidence/` — screenshots supporting test results.

## Current status
The hidden-window PowerShell branch matched two controlled test events containing `SOC_HIDDEN_TEST_001`. The encoded-command branch has not yet been separately validated. The failed-logon observations documented here do not prove an attack.

A detection match is an investigative lead, not proof of malicious activity. Verify index and sourcetype settings in your own lab before reusing searches.
