# Historical fork branch reconciliation

This record preserves the original fork lane while the active branch uses the
newer generator implementation. It is historical evidence, not an instruction
to replay old source changes or reopen completed work. Main promotion is outside
this reconciliation; [fork issue #4](https://github.com/iMelki/cli-printing-press/issues/4)
continues to track any separately requested promotion.

## Original plan

The [archived force-regeneration plan](plans/2026-05-10-force-regen-preservation.md)
was the unique document left on the original fork branch. The original has 558
lines and was stored at
`docs/plans/2026-05-10-001-fix-force-regen-preserves-templated-hand-edits-plan.md`.

- Original branch tip: `c1367ac1486fd2234082f28fb6bec4aeb9a2e02f`.
- Original plan Git blob: `0e69091149d3e053fd8c9f48d5c9bc9c0610c138`.
- Original bytes SHA-256: `2fde360e8b5403ea29c1990920a8e43a93d47ea1f2bc4ef5679b88dbc7e048ad`.
- Reconciliation source baseline: `433f703867b1576c7248957dfac0c7781bec2fc8`.

The archived copy adds an explicit historical preamble, changes the status to
`archived` while recording `original_status: completed`, and repairs four links
for its archive location. The foundational-plan link pins the original commit
because that plan is absent from the current tree. The original bytes remain
retrievable from the Git blob and retained branch ancestry.

## Original seven-commit lane

The reconciliation keeps these commits reachable through a normal merge. Their
presence in history does not mean their stale source versions should win over
the newer implementation.

| Original commit | Preserved intent and replacement |
| --- | --- |
| `a5c34bd480aa9eccea99a34d30a69b614608fddb` | Initial patchset preservation, including the archived plan. Included corrupted zero-byte source artifacts; evaluate it together with the restoration below. |
| `48f654106911dde7c9af7f6db5ac86ab4d37d218` | Fork task index, patch-equivalent replay `18fd3693b43af4f5b19ddeb144c5400b7af8a97b`. |
| `76753399894903732c8524cc11659bf9466a4d87` | Restored accidentally zeroed source; the net patch is the meaningful comparison, not the intermediate corrupted tree. |
| `8fc4aba7eac73f93d2950c03b56a3ce4486ae6ce` | Windows test fixes replayed against newer upstream as `bdbd549ae2c3e68fa351e0101f6e78f62d1e1df3`. |
| `1a95eb85fa47e3212f9a123a7dbe6d53eb259ac1` | Governance tracking, patch-equivalent replay `e518e253b5211d385fa6301e39751cd326ef18fd`. |
| `e857aaed7e8a785c2e68336b3f52a15f539c4476` | Client limit helper replayed as `ec5c3017ebcd0eb6ece2ee793d39d47910782f8a`, with subsequent corrections `f19a4d9c3a9b51376c1ac447ca20a52efafe2d1b` and `433f703867b1576c7248957dfac0c7781bec2fc8`. |
| `c1367ac1486fd2234082f28fb6bec4aeb9a2e02f` | Upstream-sync tracking replayed as `2d5f2de0f16555ad66fe52e06ace8136dd0d5cdb`. |

The adjusted replay landed through
[fork PR #6](https://github.com/iMelki/cli-printing-press/pull/6).

## Superseding implementation evidence

The reviewed current source already includes the net patchset's functional
intent through the following changes:

- Reserved placeholder host validation: `5f8dae13e1984d46a2bd7f9bf3bf83279fa4c8d6`.
- UTF-8 Python standard streams: `cb1697ed2fcc914b9f53592ba2b2f65ff7de6488`.
- Research-directory forwarding during polish: `e0240ceae66362d78ebf2097bbd66cedf155250a`,
  plus parent-directory lookup in `9a07f2872aa5c0bf61b21f7ed0263e928ec4f23e`.
- Go preflight checks: `0562bca80e8588b02130edeec8dab7d0a3b1ec1d`.
- OAuth2 runtime URL overrides: `a9e9d006af266b5b147cd7bd27bd00733be8829d`.
- Streaming extraction guidance: `182395caaa631a5fa7721dc0a6f158c557cd473e`.
- Force-regeneration preservation: `618fa45627609eff27a103bfc91ee28783e128a6`,
  followed by later preservation work including `cc3692ff27195ac37e90ef7f72228c27041e8b03`.

For maintained explanations, see the
[snapshot/merge solution](../solutions/design-patterns/snapshot-merge-with-ast-classifier-for-force-regen-2026-05-10.md)
and [lineage guard](../solutions/logic-errors/force-regen-provenance-preservation-needs-lineage-guard.md).
The archived plan's May line numbers, old command examples and deferred checklist
are historical context, not current acceptance evidence.
