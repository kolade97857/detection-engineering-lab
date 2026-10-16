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

- ## Validation Results

### 1. Sigma Rule Validation

The Sigma rule `sigma-rules/suspicious_powershell.yml` was checked locally using Sigma CLI.

- **Result:** Passed
- Errors: 0
- Condition errors: 0
- Validation issues: 0

These results confirm that the rule passed the Sigma CLI validation checks performed.

### 2. Hidden-Window PowerShell Detection

A controlled PowerShell process was executed with hidden-window arguments and the marker `SOC_HIDDEN_TEST_001`.

- **Result:** Passed
- Sysmon Event ID: 1 (Process Creation)
- Matching events observed in Splunk: 2
- Detection reason: `Hidden PowerShell window`

### 3. Encoded-Command PowerShell Detection

A controlled PowerShell process was executed using the `-EncodedCommand` argument.

- **Result:** Passed
- Event timestamp: `2026-10-15 16:04:56.477`
- Sysmon Event ID: 1 (Process Creation)
- Detection reason: `Encoded PowerShell command`

The event was observed in Windows Sysmon Operational logs and matched by the Splunk detection query.

### Validation Scope

The two detection branches were validated against controlled events in the lab. Sigma CLI validation confirms the rule passed the checks performed; it does not independently establish that every detection condition works across all telemetry sources. Further testing is needed to assess false positives, additional command-line variations, and coverage.

## Current status
Project implementation and initial validation are complete. The Sigma rule passed Sigma CLI validation, and both the hidden-window and encoded-command detection branches were verified against controlled events in Splunk. Further testing may improve coverage and reduce false positives.

A detection match is an investigative lead, not proof of malicious activity. Verify index and sourcetype settings in your own lab before reusing searches.
