# BlazeNetMonitor migration manifest

**Date:** 2026-10-28
**State:** SOURCE_STAGED; CI, hardware/installer acceptance and owner-signing checks pending.

## Exact source and destination

- Original: [BlazingSystems/BlazingSystems-Experiments](https://github.com/BlazingSystems/BlazingSystems-Experiments), path `expiremental/BlazeNetMonitor/`.
- Exact source commit: `3f762cdf436f2c996eb39088a33468e85c23143a`; source [draft PR #206](https://github.com/BlazingSystems/BlazingSystems-Experiments/pull/206). Original PR base: `main`.
- Destination: [BlazingSystems/BlazeNetMonitor](https://github.com/BlazingSystems/BlazeNetMonitor), branch `migration/blazenetmonitor-v100-source-20261028`.
- Untouched default branch: `main@40c692275bf72b7fc24d597befadec12df7bba4f`.
- Exact-source completed staging commit: `c0dd08d6459bfda3a9e5a42f69414b2a58c6d0c5`.

### Source verification

All 40 source subtree files were transferred to destination root. Binary icon `src/BlazeNetMonitor/Assets/BlazeNetMonitor.ico` was re-created with the exact original SHA `eb54e254e7fe1783eb0c96b29e0f93da3f5009f8`, not replaced by a text placeholder. Recursive source/destination tree comparison verified **40/40 exact Git blob SHA and mode matches**, zero added/missing/different source files, without truncated results.

A copied subtree does NOT transfer Git commit ancestry. Original history, PR comments and source workflow remain in Experiments, linked above.

### CI boundary

Original Experiment workflows include `blazenetmonitor.yml` and `blazenetmonitor-v1-installer.yml` (the latter can publish release artifacts). These original workflows are not disabled, deleted or copied unchanged.

The new `.github/workflows/blazenetmonitor-ci.yml` is a root-aware read-only PR and main validator, running native console assertions and a standalone Windows x64 .NET 10 build, with SHA-256 and short-retention internal workflow artifacts. It deliberately does **not** sign binaries, create GitHub releases, run a public installer, install on customer machines, or publish update branches. Existing Windows x86/ARM64 matrix coverage and installer installation/uninstall/QR checks remain dependencies for release acceptance, not covered by this minimal CI.

### Follow-up release gates

- Verify actual exact-head Windows CI and artifact existence/identity; run on real Windows 10/11 and Windows ARM64 where required.
- Review and test original installer workflow as a non-publishing destination copy when its source and release controls are reconciled; preserve original Inno Setup, installation/uninstall, Startup and QR tests.
- Independently test original Windows installer, interactive uninstall and optional self-delete on a real Windows desktop; preserve warning that unsigned installers may trigger SmartScreen.
- Check branding/third-party references, signing provenance, license obligations, and installer support-page behavior.
- Preserve open Experiments PR #206 until destination integration is independently verified. No release is authorized by migration.

**No production release / Windows installer publication is approved here.**
