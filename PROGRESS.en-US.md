# GMS v95 Reconstruction Progress

[中文](PROGRESS.zh-CN.md) | [Home](README.md)

> This page is a public progress summary. It is not a full source audit and it does not distribute client assets.

## Overview

The private workspace now has a stable runtime baseline: login, character select, channel migration, `SetField(0x008D)`, visible field entry, clean Field CRC parity, normal `tuto00` portal script request, and one clean local-player movement fixture are evidence-backed.

Percentages in this public progress table describe **evidence and public-display maturity**, not full client source reconstruction completion.

## Core Reconstruction

| Module | Progress | Status | Description |
|---|---:|---|---|
| Workspace / Git hygiene | 80% | Stable | Private workspace layout is clear; client/WZ/IDB assets stay local-only. |
| Packet primitives | 55% | In progress | Host-side `CInPacket` / `COutPacket` value models cover basic read/write semantics. |
| ZTL / ZXString / ZRef | 50% | In progress | Critical ABI boundaries such as `ZXStringW` and hidden-result `ZRef` pointers are recorded. |
| Network / CClientSocket | 30% | Early | Socket/packet seam skeleton exists; raw socket, encryption, and buffer lifecycle are not fully modeled. |
| Login / AvatarData | 45% | In progress | `SelectWorldResult` and `AvatarLook::Decode` have IDA/runtime evidence; full login packet set is incomplete. |
| Field / SetField | 65% | Active focus | `SetField(0x008D)` prefix, FILETIME tail, and current fixture offset map are established. |
| User / MovePath | 55% | In progress | A clean local user `0x002C` movement fixture is decoded; broader MovePath variants remain pending. |
| ActionMan / Resource path | 45% | In progress | Resource-path and string ABI root-cause boundaries are narrowed; full resource system reconstruction is not done. |

## Runtime Milestones

| Milestone | Status | Description |
|---|---|---|
| Login smoke | Passing | Login flow passes automation smoke. |
| Character select smoke | Passing | Character select can proceed into migration. |
| Channel migration | Passing | After `SelectCharacter`, the client reaches channel-side `MigrateIn`. |
| Field entry map `10000` | Passing | Clean baseline reaches visible tutorial map. |
| Field CRC clean baseline | Matched | Live client CRC for map `10000` matches the Kinoko comparison value. |
| Portal `tuto00` path | Matched | `UserPortalScriptRequest(0x0070)` correctly reaches `tutoChatNPC`. |
| Local user move `0x002C` | Fixture decoded | One clean 112-byte local movement fixture is decoded. |
| NPC movement `0x00F1/0x013A` | Attributed | Confirmed as NPC movement stream, not local user movement. |
| Full CharacterData | Partial | Current fixture map is strong, but full nested decode is not complete. |
| Full MovePath variants | Partial | Core body and one clean sample are validated; more attr/option/tail variants are pending. |
| Full client replacement | Long-term | Still a long-term goal; this is not a replacement client source tree yet. |

## Server / Data / Localization

| Module | Progress | Status | Description |
|---|---:|---|---|
| Kinoko v95 baseline | 65% | Stable progress | Current main server comparison target and automation testbed. |
| Space2D CRC | 70% | Baseline matched | Proof maps match; broader map corpus remains pending. |
| PortalList CRC | 75% | Baseline matched | Normal `tuto00` path and portal CRC match in clean runs. |
| WZ / localization overlay | 10% | Planned | Planned as overlay/catalog work; WZ files are not distributed. |
| Ecosystem catalog | 10% | Planned | Planned trust catalog for v95 servers, WZ tools, and localization resources. |

## Current Focus

1. Expand `CharacterData::Decode` section maps and variant fixtures.
2. Expand `MovePath` attr groups, option-gated random counters, and keypad/rect tail samples.
3. Keep Kinoko as a strict comparison server and avoid promoting temporary workarounds into protocol facts.
4. Build the public bilingual progress display.
5. Establish non-asset localization overlay and ecosystem catalog workflows.

## Not Distributed

This public progress repository does not include client binaries, WZ files, IDA databases, PDB files, full decompiler exports, runtime dumps, private logs, or third-party source trees. See [`NOTICE.md`](NOTICE.md).
