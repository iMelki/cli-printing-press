# Open Tasks

GitHub Issues are the durable source of truth for this user-owned Printing
Press fork. This file keeps the local checkout discoverable for agents that
start from the repo.

## Active GitHub Issues

| Issue | Status | Scope | Notes |
| --- | --- | --- | --- |
| _None_ | - | - | All currently tracked fork stabilization issues are closed. |

## Recently Completed

| Issue | Result |
| --- | --- |
| [#2](https://github.com/iMelki/cli-printing-press/issues/2) | Stabilized the Windows full test suite after the patchset build repair. The fork now passes `go test -p 1 -count=1 -timeout 300s ./...` on Windows, with generated/test helper binaries built to platform executable paths, local HTTP fixture tests hardened, chmod-only permission tests skipped where Windows cannot simulate them, and govulncheck/race-detector checks made deterministic for this environment. |
| [#1](https://github.com/iMelki/cli-printing-press/issues/1) | Restored buildability after deciding the zero-byte tracked source/test/template files were corrupted preservation artifacts. Existing files were restored from the clean base, new empty placeholders were removed, `go test -run '^$' ./...` passes, and `go build ./cmd/cli-printing-press` passes. |
| Local adoption | Forked `mvanhorn/cli-printing-press` into `iMelki/cli-printing-press`, set local `origin` to the fork, disabled upstream pushes, and preserved the prior dirty patchset on `dev` in commit `a5c34bd4`. |
