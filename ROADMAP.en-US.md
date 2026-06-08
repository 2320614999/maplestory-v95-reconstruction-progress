# Roadmap

[中文](ROADMAP.zh-CN.md) | [Home](README.md)

> This is a public roadmap. It only describes non-sensitive engineering direction. Runtime logs, IDA databases, WZ files, and client assets are not published here.

## Phase 0: Public progress repository

Goal: turn the public repository into a clean progress display.

- [x] Create the progress-only public repository.
- [x] Add bilingual README.
- [x] Add NOTICE to clarify that assets and third-party source trees are not distributed.
- [ ] Add bilingual `index.html` dashboard.
- [ ] Enable GitHub Pages.
- [ ] Update progress tables from audit results periodically.

## Phase 1: Stable runtime baseline

Goal: keep private-workspace automation smoke runs reproducible.

- [x] Login smoke passing.
- [x] Character select smoke passing.
- [x] Channel migration reaches `MigrateIn`.
- [x] `SetField(0x008D)` reaches visible map `10000`.
- [x] Field CRC / Space2D CRC / Portal CRC match Kinoko on clean baseline.
- [x] `UserPortalScriptRequest(0x0070)` reaches `tuto00` / `tutoChatNPC` normally.
- [ ] Publish a sanitized summary of stale-client, forced-relaunch, and deployment-state diagnostics.

## Phase 2: Field / CharacterData

Goal: expand the current `SetField` fixture map into more variants and a stronger `CharacterData` contract.

- [x] `SetField(0x008D)` prefix confirmed.
- [x] Server FILETIME tail anchor confirmed.
- [x] Current clean fixture offset map established.
- [ ] Expand `CharacterData::Decode` section maps.
- [ ] Add variant fixtures for non-empty equipment, skills, quest state, and character data differences.
- [ ] Promote `GW_CharacterStat::Decode` from current fixture evidence into a separate contract.
- [ ] Keep field-stage `CharacterData` separate from login-stage `AvatarData` evidence.

## Phase 3: Movement / MovePath

Goal: expand from one clean fixture to a broader movement variant corpus.

- [x] Local user movement `0x002C` confirmed.
- [x] `CVecCtrlUser::EndUpdateActive -> CMovePath::Flush/Encode` path confirmed.
- [x] One clean 112-byte `0x002C` fixture decoded and re-encoded.
- [x] NPC movement `0x00F1/0x013A` correctly attributed.
- [ ] Expand `MoveElem` attr group samples.
- [ ] Capture random-counter samples when option `2` is enabled.
- [ ] Separate outbound encode tails from inbound non-passive decode paths across all known streams.
- [ ] Prevent NPC movement parser changes from leaking into the local user move contract.

## Phase 4: Kinoko v95 server line

Goal: make Kinoko a stable, strict, regression-friendly v95 comparison server.

- [x] Kinoko v95 baseline works as the current testbed.
- [x] Map `10000` clean CRC parity matched.
- [x] Additional proof maps such as `104000000` are entering the comparison set.
- [ ] Build a map CRC / portal CRC / Space2D CRC corpus.
- [ ] Build packet fixture / golden test workflows.
- [ ] Keep temporary workarounds disabled by default or explicitly gated.
- [ ] Curate a trust catalog for v95 server ecosystem resources.

## Phase 5: Localization / Ecosystem

Goal: establish non-asset localization and ecosystem-resource catalogs.

- [ ] Create WZ tooling catalog.
- [ ] Create v95 server ecology catalog.
- [ ] Design localization overlay JSON schema.
- [ ] Export String/Quest/UI text indexes.
- [ ] Build untranslated, length-risk, and glyph-risk reports.
- [ ] Ensure the public repository publishes only overlay notes and diff reports, not WZ files.

## Phase 6: Long-term client reconstruction

Goal: move gradually from evidence and host-side contracts toward broader semantic reconstruction.

- [ ] Expand UI, pool, mob, NPC, drop, and reactor modules.
- [ ] Expand WZ/ResMan/ActionMan semantic boundaries.
- [ ] Build a stronger socket/encryption/buffer lifecycle model.
- [ ] Promote more IDA/runtime evidence into small maintainable contracts.
- [ ] Explore replacement-client or cross-architecture port possibilities as a long-term direction.
