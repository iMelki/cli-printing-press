# Open Tasks

GitHub Issues are the durable source of truth for this user-owned Printing
Press fork. This file keeps the local checkout discoverable for agents that
start from the repo.

## Active GitHub Issues

| Issue | Status | Scope | Notes |
| --- | --- | --- | --- |
| [#2](https://github.com/iMelki/cli-printing-press/issues/2) | Planned | Windows test suite | Stabilize the remaining full `go test ./...` failures after the patchset build repair: Windows permission/cert expectations, narrativecheck/OpenAPI/skill expectations, and Go toolchain vulnerability-gate drift. |

## Recently Completed

| Issue | Result |
| --- | --- |
| [#1](https://github.com/iMelki/cli-printing-press/issues/1) | Restored buildability after deciding the zero-byte tracked source/test/template files were corrupted preservation artifacts. Existing files were restored from the clean base, new empty placeholders were removed, `go test -run '^$' ./...` passes, and `go build ./cmd/printing-press` passes. |
| Local adoption | Forked `mvanhorn/cli-printing-press` into `iMelki/cli-printing-press`, set local `origin` to the fork, disabled upstream pushes, and preserved the prior dirty patchset on `dev` in commit `a5c34bd4`. |
