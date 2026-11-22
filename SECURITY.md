# Security policy

Daybook reads your screenshots and voice notes, so a flaw in it matters. If you find one, please report it privately.

## Reporting a vulnerability

Use the private report form:

**https://github.com/miketigerblue/daybook-releases/security/advisories/new**

It needs a GitHub account. The report is visible only to you and to Tiger Blue. Please do not open a public issue for a security problem.

Useful things to include:

- The Daybook version (Settings, Updates section) and your macOS version.
- What you did, what happened, and what you expected.
- Whether any data left the Mac that should not have, or was read by something that should not have access.

## What to expect

- An acknowledgement within 3 working days.
- An assessment, and a fix plan if the report is confirmed, within 10 working days.
- Credit in the release notes when the fix ships, if you want it.

## Supported versions

Only the latest release gets security fixes. Daybook updates itself, so the fix reaches you as a new version.

## In scope

- Anything that sends a screenshot, a recording, a transcript or a key somewhere the privacy settings say it should not go.
- Anything that lets another app or a web page make Daybook act: record, read files, write notes, or reveal data.
- Flaws in the update mechanism, the licence check, or the signing of releases.
- Content held by the sensitivity gate reaching a model or a note.

## Out of scope

- Attacks that need an administrator account or physical access to an unlocked Mac.
- The behaviour of the model provider you choose (Anthropic, or a local Ollama server).
- Missing detection of a kind of sensitive content the gate does not claim to recognise. That is a welcome feature request, not a vulnerability.

## How releases are checked

Every release is signed with a Developer ID and notarised by Apple, and ships with full release notes and a bill of materials (CycloneDX and SPDX) listing the third-party packages in the build. Updates are signed, and the app verifies the signature before installing one.

Before a release is built, every change passes: the test suite, including runs under the address, thread and undefined-behaviour sanitizers; static analysis with rules specific to Daybook's privacy promises; a scan of the whole history for secrets; a scan of the dependencies for known vulnerabilities; an audit of the built app's signature, entitlements and linked libraries; and a run of the built app with the network switched off, which checks that local-only mode works and that held content is never sent.
