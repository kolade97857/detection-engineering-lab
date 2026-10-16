# Encoded PowerShell Command Detection Test

## Objective

Validate whether the Splunk detection query identifies PowerShell process creation events that use the `-EncodedCommand` argument.

## Test Environment

- **Platform:** Windows VM
- **Logging:** Sysmon
- **SIEM:** Splunk Enterprise
- **Sysmon Event ID:** 1 (Process Creation)
- **Detection query:** `splunk-spl/suspicious_powershell.spl`

## Test Procedure

A controlled PowerShell command was executed in the Windows lab environment using the `-EncodedCommand` argument. The command encoded a harmless instruction to write a test marker to the console.

The resulting process-creation event was located in Windows Event Viewer under:

`Applications and Services Logs > Microsoft > Windows > Sysmon > Operational`

The event was then located in Splunk using the Sysmon Operational event data.

## Observed Results

- **Event timestamp:** 2026-10-15 16:04:56.477
- **Process:** `powershell.exe`
- **Argument observed:** `-EncodedCommand`
- **Log source:** Sysmon Operational
- **Sysmon Event ID:** 1
- **Splunk detection reason:** Encoded PowerShell command

## Outcome

**PASS — Encoded-command detection validated in Splunk.**

The event appeared in Splunk, and the detection query classified it as `Encoded PowerShell command`. The test confirms that the encoded-command branch of the Splunk query matched the observed event.

## Scope and Limitations

This test validates the encoded-command branch against the observed controlled test event. It does not establish that every encoded PowerShell command is malicious, nor does it independently validate the Sigma rule against a Sigma backend.

## Evidence

The corresponding event was observed in Windows Sysmon Operational logs and in Splunk Search results. Supporting screenshots should be retained in the repository's `evidence/` directory where available.
