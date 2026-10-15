# Test Case: Suspicious PowerShell Hidden-Window Execution

## Objective
Validate detection of PowerShell process-creation events containing hidden-window arguments.

## Data source
- Index: `main`
- Source: Windows Sysmon Operational log
- Event ID: 1 — Process creation

## Test activity
A controlled command was executed in the authorized lab using `-WindowStyle Hidden` and the marker `SOC_HIDDEN_TEST_001`.

## Expected result
The SPL query returns the process-creation event and labels it `Hidden PowerShell window`.

## Observed result
- Matching events shown: 2
- Test marker: `SOC_HIDDEN_TEST_001`
- Process: `powershell.exe`
- Detection reason: `Hidden PowerShell window`

## Status
**Pass — hidden-window branch validated.**

The two results may represent repeated executions of the same test and are not evidence of two separate attacks.

## Limitations
- Encoded-command branch not yet separately validated.
- Hidden PowerShell can be legitimate and requires context.
