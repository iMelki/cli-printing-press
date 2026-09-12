# Open Tasks

GitHub Issues are the durable source of truth for this user-owned Printing
Press fork. This file keeps the local checkout discoverable for agents that
start from the repo.

## Active GitHub Issues

| Issue | Status | Scope | Notes |
| --- | --- | --- | --- |
| [#4](https://github.com/iMelki/cli-printing-press/issues/4) | Open | Upstream sync and dev-to-main promotion | Plan a safe report-first sync from `mvanhorn/cli-printing-press`, trial integration away from active `dev`, preserve fork governance work, then produce a reviewed `dev -> main` promotion brief. |
| [#3](https://github.com/iMelki/cli-printing-press/issues/3) | Open | Governance and secrets baseline | Backfills the recurring projects-ops quarterly health findings: CODEOWNERS, issue templates, labels manifest, secrets filter/store, `.git-secrets-ignore`, `.gitattributes filter=secrets`, pre-commit guard, and `.gitignore` coverage for local secrets artifacts. |

The #3 placeholder-only body was repaired with exact structured readback on
2026-09-13. CODEOWNERS exists; the remaining baseline still needs implementation
and focused verification. The historical payload gap is recorded in
[agent-settings#133](https://github.com/iMelki/agent-settings/issues/133#issuecomment-5649343102).
The shared asset owner also holds the
[skill portability and stale runtime-reference follow-up](https://github.com/iMelki/cli-printing-press/issues/3#issuecomment-5649381962).
That agent-settings update is coordinated separately from this fork's changes.

## Recently Completed

| Issue | Result |
| --- | --- |
| [#8](https://github.com/iMelki/cli-printing-press/issues/8) | Closed: REST/BLE templates select patched Go 1.26.8, actual generated compilation passed, and the fresh fixture passed all nine normal validation gates including govulncheck. Source published in 87ab14d7. |
| [#5](https://github.com/iMelki/cli-printing-press/issues/5) | Closed: existing Windows executable helper verified end-to-end; both installed generator entrypoints now use clean fork build 87ab14d7 with Go 1.26.8, old 4.2.2 binary retained for rollback. [Runtime evidence](docs/reports/windows-runtime-reconciliation-2026-09-13.md). |
| [#2](https://github.com/iMelki/cli-printing-press/issues/2) | Stabilized the Windows full test suite after the patchset build repair. The fork now passes `go test -p 1 -count=1 -timeout 300s ./...` on Windows, with generated/test helper binaries built to platform executable paths, local HTTP fixture tests hardened, chmod-only permission tests skipped where Windows cannot simulate them, and govulncheck/race-detector checks made deterministic for this environment. |
| [#1](https://github.com/iMelki/cli-printing-press/issues/1) | Restored buildability after deciding the zero-byte tracked source/test/template files were corrupted preservation artifacts. Existing files were restored from the clean base, new empty placeholders were removed, `go test -run '^$' ./...` passes, and `go build ./cmd/cli-printing-press` passes. |
| Local adoption | Forked `mvanhorn/cli-printing-press` into `iMelki/cli-printing-press`, set local `origin` to the fork, disabled upstream pushes, and preserved the prior dirty patchset on `dev` in commit `a5c34bd4`. |

## Historical fork reconciliation

The original seven-commit fork lane is retained as merge ancestry. Its unique
[force-regeneration plan](docs/archive/plans/2026-05-10-force-regen-preservation.md)
is archived with [per-commit provenance](docs/archive/printing-press-branch-reconciliation-2026-09-08.md).
Current generator behavior follows the newer replayed and upstream fixes; the
old plan does not reopen historical implementation tasks. Issue
[#4](https://github.com/iMelki/cli-printing-press/issues/4) remains the tracking
record for upstream alignment and any separately requested dev-to-main promotion.
This reconciliation does not promote main.
