# Windows runtime reconciliation

The Windows executable-suffix fix already exists in the source checkout. The
installed legacy generator still reported 4.2.2 when this review began, so
reimplementing the source fix would not repair the operator's actual command.

## Source and issue identity

- Clean dev started at 0ce84d86. Origin is the user-owned fork; external upstream
  pushes remain disabled.
- `internal/generator/validate.go` applies `platform.ExecutablePath` to the
  same path used by the build, help, version, and doctor gates. The call is
  attributed to upstream commit 7365fcc31; the platform helper is from
  d0086ffe. Windows stabilization bdbd549a is later supporting work.
- Installed build metadata identifies the old command as module v4.2.2,
  built with Go 1.26.3. Source version fallback is 4.25.0; a local fork binary
  also needs its Git revision recorded, not just that version string.
- #5 was missing from OPEN_TASKS.md and is now indexed. #3 had only a summary
  heading; the canonical structured writer repaired its body with an exact
  2027-character readback. Governance implementation remains open.
- Cached upstream ancestry shows 62 fork commits and zero upstream-only commits.
  This is not a fresh fetch and does not establish current upstream alignment;
  #4 continues to own integration and promotion.

## Validation and runtime handoff

`go test -p 1 -count=1 -timeout 60s ./internal/platform` passed. Its table
covers Windows suffix addition, an existing suffix, and unchanged Linux/macOS
paths. The initial Go preparation took longer than test execution (0.037s).

The focused generator `TestHelpGateTimeout` passed (0.157s). A staged fork binary
built successfully and returned version 4.25.0 plus generation help; Go build
metadata recorded 0ce84d8663c46d095ceb36073a9f318d4ec4e652 with an unmodified
source tree, using Go 1.26.4.

A fresh credential-free BH/PP demo passed dependency tidy and the x/net safety
gate, then correctly failed govulncheck: six reachable standard-library
vulnerabilities in Go 1.26.4, fixed in 1.26.6 or later. This is a separate
toolchain problem, now tracked in #8. The scanner honors the generated module's
toolchain directive; changing only the calling environment does not override
that pin. Both REST and BLE templates now select 1.26.8, retaining the language
floor and scanner. Official toolchain acquisition succeeded without changing
global configuration.

Patched generated-module tests passed in 79.323 seconds, run without `-short`
using Go 1.26.8, `-p 1`, and `-parallel 1`: REST and BLE outputs actually compiled,
the browser transport output carried the new directive, and help timeouts
retained platform behavior. This compile helper uses module resolution during
build; it does not substitute for the full validator's dependency-tidy gate.
The directive selects a preferred toolchain, while the language floor remains
1.26. Offline runs need the selected toolchain and module cache already present.

Patched fresh normal generation completed with exit 0. All nine gates passed:
dependency tidy, x/net floor, govulncheck, vet, module build, runnable binary
build, generated Windows help, version, and doctor. The generated MCP bundle
was produced locally. A research-run-id warning concerns the separate phase-5
acceptance workflow; this credential-free generation smoke did not run that
workflow or claim its acceptance.

Source commit 87ab14d772211283a886d1f9ed94888ad9d5c995 was pushed to origin/dev.
A clean build from that commit reports Go 1.26.8 and `vcs.modified=false`.
Both installed generator entrypoints now use this binary; installed version
and generation help checks passed. Display version remains 4.25.0, so use the
build revision to distinguish the maintained fork.

Installed SHA-256:
`64e3d51dee1081b32b6861b5cbdb62986a9414039080bd191a7b81d2f5fea0b0`.
The retained 4.2.2 rollback copy matches its pre-install hash:
`b8121fa60c38719ab5fcbba0a77b9be103df27c1b0e05615f8f20f241910e0f1`.

Private receipt: `%LOCALAPPDATA%/MemSys/eval-artifacts/printing-press/runtime-install-20260913.json`.
Rollback copy: `%LOCALAPPDATA%/MemSys/backups/printing-press-20260913/printing-press-4.2.2.exe`.
Rollback consists of restoring that retained file to the legacy Go-bin
entrypoint; the canonical new entrypoint can be retained or removed separately.
Neither global Go configuration nor an external upstream was modified.

#5 and #8 were closed through structured issue writes with exact body and state
readback. #3 and #4 remain open for their distinct governance and promotion work.

## Research

Upstream [issue #1150](https://github.com/mvanhorn/cli-printing-press/issues/1150)
describes an adjacent scorer executable-path problem and was closed through
#1412. It also links the verify-gate #978 case. These reinforce reusing the
existing platform helper rather than adding a parallel Windows rule.

The [official Go release history](https://go.dev/doc/devel/release) identifies
1.26.8 as the current patch in the 1.26 series, including the security fixes
released in 1.26.6. The change stays within that minor series.

The [upstream README](https://github.com/mvanhorn/cli-printing-press) identifies
`cli-printing-press` as the canonical generator entrypoint and the older
`printing-press` command as compatibility behavior. This review builds the
user-owned fork locally; it does not fetch and install an unreviewed upstream
release or publish generated artifacts.
