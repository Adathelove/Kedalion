# Kedalion OmniFocus Automation Plan

Goal: stand up Kedalion's OmniFocus automation with mailbox-driven workflow, while keeping any live OmniFocus data out of the repo (use sanitized fixtures only).

## Epics

1) OmniFocus Automation Bootstrap
- Create minimal project layout and config placeholders (no secrets, no live task data).
- Add sanitized sample OmniFocus exports for testing only.

2) Message-Driven Workflow Integration
- Wire mailbox signals (Mailbox/Kedalion) into task orchestration: claim, log progress, and complete via CLI helper.
- Provide helper scripts to generate replies that follow status suffix rules.

3) OmniJS/AppleScript Runner
- Choose runner approach (osascript wrapper vs. OmniJS plug-in trigger) and document invocation contract.
- Build a CLI entrypoint that executes OmniJS/AppleScript actions with: dry-run flag, sanitized logging, exit codes.
- Add minimal test harness (e.g., mocked OmniFocus data) so scripts can be exercised without the app.

4) Exports for Iris
- Define export schema for Iris (likely JSON plus CSV) with field list and redaction rules.
- Implement export command that produces sanitized outputs and writes to a temp/output folder, not tracked.
- Add schema validation or sample fixture to guard against breaking Iris consumption.

5) Ops & Protocol
- Document reply protocol: acknowledge when work starts, request help/decline if blocked, summarize results when done.
- Add quickstart doc for running the runner/export commands and where to drop replies in mailbox.

## Immediate stories (v1)
- Story: Draft CLI contract for OmniJS/AppleScript runner (inputs, flags, outputs, exit codes).
- Story: Sketch mailbox reply helper that renames `*.new.msg` to `*.in-progress.msg` and appends updates.
- Story: Define Iris export JSON/CSV schema and produce one sanitized sample fixture.
- Story: Write ops note capturing the reply protocol and privacy guardrails.

Notes
- Keep live OmniFocus data out of the repository; use mock or redacted fixtures only.
- Prefer plain Bash/osascript/JavaScript (OmniJS) with minimal deps; avoid Homebrew installs unless approved.
