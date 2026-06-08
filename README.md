# MapleStory v95 Reconstruction Progress

[中文](#中文说明) | [English](#english-notes) | [Dashboard](index.html) | [Notice](NOTICE.md)

![runtime baseline](https://img.shields.io/badge/runtime_baseline-passing-brightgreen?style=flat-square)
![field crc](https://img.shields.io/badge/field_CRC-matched-brightgreen?style=flat-square)
![core contracts](https://img.shields.io/badge/core_contracts-50%25-yellowgreen?style=flat-square)
![server parity](https://img.shields.io/badge/server_parity-65%25-yellowgreen?style=flat-square)
![public docs](https://img.shields.io/badge/public_docs-45%25-yellow?style=flat-square)
![assets](https://img.shields.io/badge/assets-not_distributed-lightgrey?style=flat-square)

> Progress-only public display for a private GMS v95 reconstruction workspace.
>
> No client binaries, WZ files, IDA databases, proprietary game assets, runtime dumps, or third-party source trees are distributed here.

---

## Progress Snapshot / 进度快照

Percentages below describe **evidence and public-display maturity**, not full client source reconstruction completion.

下方百分比表示**证据与公开展示成熟度**，不是完整客户端源码还原百分比。

### Core Reconstruction / 核心重构

| Folder | Progress | Status | Description / 说明 |
|---|---:|---|---|
| `workspace` | ![80%](https://img.shields.io/badge/80%25-stable-brightgreen?style=flat-square) | Stable | 私有工作区结构清晰，客户端/WZ/IDB 等资产保持 local-only。<br><sub>Private workspace layout is clear; client/WZ/IDB assets stay local-only.</sub> |
| `packet` | ![55%](https://img.shields.io/badge/55%25-in_progress-yellowgreen?style=flat-square) | In progress | `CInPacket` / `COutPacket` host-side value model 已覆盖基础读写语义。<br><sub>Host-side packet value models cover basic read/write semantics.</sub> |
| `ztl` | ![50%](https://img.shields.io/badge/50%25-in_progress-yellowgreen?style=flat-square) | In progress | `ZXString`、`ZRef` hidden-result pointer 等关键 ABI 边界已记录。<br><sub>Critical ABI boundaries such as `ZXString` and hidden-result `ZRef` pointers are recorded.</sub> |
| `network` | ![30%](https://img.shields.io/badge/30%25-early-orange?style=flat-square) | Early | 已有 socket/packet seam skeleton；raw socket、encryption、buffer lifecycle 未完整建模。<br><sub>Socket/packet seam skeleton exists; raw socket, encryption, and buffer lifecycle are not fully modeled.</sub> |
| `login` | ![45%](https://img.shields.io/badge/45%25-in_progress-yellow?style=flat-square) | In progress | `SelectWorldResult`、`AvatarLook::Decode` 有 IDA/runtime 证据；完整 login packet set 未完成。<br><sub>`SelectWorldResult` and `AvatarLook::Decode` have IDA/runtime evidence; the full login packet set is incomplete.</sub> |
| `field` | ![65%](https://img.shields.io/badge/65%25-active-yellowgreen?style=flat-square) | Active focus | `SetField(0x008D)` prefix、FILETIME tail、当前 fixture offset map 已建立。<br><sub>`SetField(0x008D)` prefix, FILETIME tail, and current fixture offset map are established.</sub> |
| `user` | ![55%](https://img.shields.io/badge/55%25-in_progress-yellowgreen?style=flat-square) | In progress | local user `0x002C` clean fixture 已 decode；MovePath 变体覆盖仍不足。<br><sub>A clean local user `0x002C` movement fixture is decoded; broader MovePath variants remain pending.</sub> |
| `action` | ![45%](https://img.shields.io/badge/45%25-in_progress-yellow?style=flat-square) | In progress | 资源路径与 String ABI 的 root-cause 边界已缩小，但完整资源系统未重构。<br><sub>Resource-path and string ABI root-cause boundaries are narrowed; the full resource system is not reconstructed.</sub> |

### Runtime Milestones / Runtime 里程碑

| Milestone | Status | Description / 说明 |
|---|---|---|
| Login smoke | ![passing](https://img.shields.io/badge/passing-brightgreen?style=flat-square) | 登录链路可通过自动化 smoke。<br><sub>Login flow passes automation smoke.</sub> |
| Character select smoke | ![passing](https://img.shields.io/badge/passing-brightgreen?style=flat-square) | 选人流程可进入后续 migration。<br><sub>Character select can proceed into migration.</sub> |
| Channel migration | ![passing](https://img.shields.io/badge/passing-brightgreen?style=flat-square) | `SelectCharacter` 后可切入 channel-side `MigrateIn`。<br><sub>After `SelectCharacter`, the client reaches channel-side `MigrateIn`.</sub> |
| Field entry map `10000` | ![passing](https://img.shields.io/badge/passing-brightgreen?style=flat-square) | clean baseline 可见进入 tutorial map。<br><sub>Clean baseline reaches visible tutorial map.</sub> |
| Field CRC clean baseline | ![matched](https://img.shields.io/badge/matched-brightgreen?style=flat-square) | map `10000` 的 live client CRC 与 Kinoko 对照值匹配。<br><sub>Live client CRC for map `10000` matches the Kinoko comparison value.</sub> |
| Portal `tuto00` path | ![matched](https://img.shields.io/badge/matched-brightgreen?style=flat-square) | `UserPortalScriptRequest(0x0070)` 正常触发 `tutoChatNPC`。<br><sub>`UserPortalScriptRequest(0x0070)` correctly reaches `tutoChatNPC`.</sub> |
| Local user move `0x002C` | ![decoded](https://img.shields.io/badge/fixture_decoded-yellowgreen?style=flat-square) | 已有一条 clean 112-byte movement fixture。<br><sub>One clean 112-byte local movement fixture is decoded.</sub> |
| NPC movement `0x00F1/0x013A` | ![attributed](https://img.shields.io/badge/attributed-yellowgreen?style=flat-square) | 已确认是 NPC movement stream，不再混入 local user move。<br><sub>Confirmed as NPC movement stream, not local user movement.</sub> |
| Full `CharacterData` | ![partial](https://img.shields.io/badge/partial-orange?style=flat-square) | 当前 fixture map 较强，但完整 nested decode 未完成。<br><sub>Current fixture map is strong, but full nested decode is not complete.</sub> |
| Full `MovePath` variants | ![partial](https://img.shields.io/badge/partial-orange?style=flat-square) | core body 与一个 clean sample 已验证；更多 attr/option/tail 变体待补。<br><sub>Core body and one clean sample are validated; more attr/option/tail variants are pending.</sub> |

### Server / Data / Localization

| Module | Progress | Status | Description / 说明 |
|---|---:|---|---|
| `kinoko` | ![65%](https://img.shields.io/badge/65%25-stable_progress-yellowgreen?style=flat-square) | Stable progress | 作为当前主服务端对照与自动化测试台。<br><sub>Current main server comparison target and automation testbed.</sub> |
| `space2d-crc` | ![70%](https://img.shields.io/badge/70%25-baseline_matched-green?style=flat-square) | Baseline matched | proof map 已对齐，广域 map corpus 仍待扩展。<br><sub>Proof maps match; broader map corpus remains pending.</sub> |
| `portallist-crc` | ![75%](https://img.shields.io/badge/75%25-baseline_matched-green?style=flat-square) | Baseline matched | `tuto00` 正常路径和 portal CRC 已在 clean run 对齐。<br><sub>Normal `tuto00` path and portal CRC match in clean runs.</sub> |
| `localization` | ![10%](https://img.shields.io/badge/10%25-planned-lightgrey?style=flat-square) | Planned | 计划做 overlay/catalog，不分发 WZ。<br><sub>Planned as overlay/catalog work; WZ files are not distributed.</sub> |
| `ecosystem` | ![10%](https://img.shields.io/badge/10%25-planned-lightgrey?style=flat-square) | Planned | 计划整理 v95 服务端、WZ 工具、汉化资源的可信度目录。<br><sub>Planned trust catalog for v95 servers, WZ tools, and localization resources.</sub> |

---

## 中文说明

这是一个**进度公示仓库**，用于展示 GMS v95 重构工作区的公开进展。

它不是完整源码仓，也不是资源分发仓。真实工作区仍然保持私密；本仓只发布经过整理的路线图、状态摘要和非敏感说明。

### 快速链接

- [`index.html`](index.html) - 中英切换 dashboard
- [`PROGRESS.zh-CN.md`](PROGRESS.zh-CN.md) / [`PROGRESS.en-US.md`](PROGRESS.en-US.md)
- [`ROADMAP.zh-CN.md`](ROADMAP.zh-CN.md) / [`ROADMAP.en-US.md`](ROADMAP.en-US.md)
- [`NOTICE.md`](NOTICE.md)

---

## English Notes

This is a **progress-only public repository** for a private GMS v95 reconstruction workspace.

It is not the full source workspace and it is not an asset distribution repository. The real workspace remains private; this repository only publishes curated roadmap notes, status summaries, and non-sensitive project information.

### Links

- [`index.html`](index.html) - bilingual dashboard
- [`PROGRESS.zh-CN.md`](PROGRESS.zh-CN.md) / [`PROGRESS.en-US.md`](PROGRESS.en-US.md)
- [`ROADMAP.zh-CN.md`](ROADMAP.zh-CN.md) / [`ROADMAP.en-US.md`](ROADMAP.en-US.md)
- [`NOTICE.md`](NOTICE.md)

---

## Not Included / 不包含内容

- MapleStory client binaries / MapleStory 客户端二进制
- WZ files / WZ 文件
- IDA databases, PDBs, or large decompiler exports / IDA 数据库、PDB、反编译大导出
- runtime logs, dumps, or raw screenshots / runtime logs、dump、截图原图
- upstream Kinoko / kinoko_client source trees / upstream Kinoko / kinoko_client 源码树
- proprietary Nexon / Wizet assets / Nexon / Wizet 专有资产
