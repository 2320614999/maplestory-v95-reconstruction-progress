# MapleStory v95 Reconstruction Progress

[中文](#中文说明) | [English](#english-notes) | [Dashboard](index.html) | [Notice](NOTICE.md)

![runtime baseline](https://img.shields.io/badge/runtime_baseline-passing-brightgreen?style=flat-square)
![field crc](https://img.shields.io/badge/field_CRC-matched-brightgreen?style=flat-square)
![core contracts](https://img.shields.io/badge/core_contracts-82%25-green?style=flat-square)
![formal promotions](https://img.shields.io/badge/formal_promotions-6937-blue?style=flat-square)
![verified](https://img.shields.io/badge/verified-0-lightgrey?style=flat-square)
![server parity](https://img.shields.io/badge/server_parity-68%25-yellowgreen?style=flat-square)
![assets](https://img.shields.io/badge/assets-not_distributed-lightgrey?style=flat-square)

> Progress-only public display for a private GMS v95 reconstruction workspace.
>
> No client binaries, WZ files, IDA databases, proprietary game assets, runtime dumps, or third-party source trees are distributed here.

---

## Progress Snapshot / 进度快照

Percentages below describe **evidence and public-display maturity**, not full client source reconstruction completion.

下方百分比表示**证据与公开展示成熟度**，不是完整客户端源码还原百分比。

Current headline / 当前头条：

```text
formal promotions = 6937
verified = 0
```

Most new promotions are **metadata / opaque-token / row-identity facts**, not source intake, runtime equivalence, production ABI/layout closure, or verified reconstruction.

大部分新增 promotion 属于 **metadata / opaque-token / row-identity facts**，不是源码合流、runtime 等价、生产 ABI/layout 闭合，也不是 verified reconstruction。

### Core Reconstruction / 核心重构

| Folder | Progress | Status | Description / 说明 |
|---|---:|---|---|
| `workspace` | ![80%](https://img.shields.io/badge/80%25-stable-brightgreen?style=flat-square) | Stable | 私有工作区结构清晰，客户端/WZ/IDB 等资产保持 local-only。<br><sub>Private workspace layout is clear; client/WZ/IDB assets stay local-only.</sub> |
| `contract-tests` | ![93%](https://img.shields.io/badge/93%25-expanded-brightgreen?style=flat-square) | Expanded | 统一 contract runner 已覆盖 30+ host-side contract / analyzer gates，并继续接入 ZTL metadata、Base64、EqSlotInfo、cash text-money 等 lanes。<br><sub>The unified contract runner covers 30+ host-side gates and includes ZTL metadata, Base64, EqSlotInfo, cash text-money, and related lanes.</sub> |
| `packet` | ![67%](https://img.shields.io/badge/67%25-in_progress-yellowgreen?style=flat-square) | In progress | `CInPacket` / `COutPacket` host-side value model、reader/writer、differential fixtures 与 DecodeBuffer contract 已覆盖基础 packet 语义。<br><sub>Host-side packet models, reader/writer checks, differential fixtures, and DecodeBuffer contracts cover basic packet semantics.</sub> |
| `ztl` | ![82%](https://img.shields.io/badge/82%25-metadata_promoted-green?style=flat-square) | Metadata promoted with limits | ZTL shard10、dirty-filtered quarantine、shard7 V__ZRef 等 metadata / opaque-token facts 已大规模进入 formal promotion；不声明生产 ZTL ABI/layout/lifetime/refcount/destructor/vtable。<br><sub>ZTL shard10, dirty-filtered quarantine, shard7 V__ZRef, and related metadata / opaque-token facts have moved into formal promotion at scale; production ZTL ABI/layout/lifetime/refcount/destructor/vtable are not claimed.</sub> |
| `network` | ![43%](https://img.shields.io/badge/43%25-early-yellow?style=flat-square) | Early | 已有 socket/packet seam skeleton、network compile contract 与 DecodeBuffer source-contract 面；raw socket、encryption、buffer lifecycle 未完整建模。<br><sub>Socket/packet seam skeleton, network compile contract, and DecodeBuffer source-contract coverage exist; raw socket, encryption, and buffer lifecycle are not fully modeled.</sub> |
| `login` | ![48%](https://img.shields.io/badge/48%25-in_progress-yellow?style=flat-square) | In progress | `SelectWorldResult`、`AvatarLook::Decode` 有 IDA/runtime 证据；WorldInformation、SelectCharacterResult 与 send-side contracts 未完成。<br><sub>`SelectWorldResult` and `AvatarLook::Decode` have IDA/runtime evidence; WorldInformation, SelectCharacterResult, and send-side contracts remain pending.</sub> |
| `field` | ![74%](https://img.shields.io/badge/74%25-active-green?style=flat-square) | Active | `SetField(0x008D)` prefix、FILETIME tail、当前 fixture offset map 已建立；完整 CharacterData 仍是长尾。<br><sub>`SetField(0x008D)` prefix, FILETIME tail, and current fixture offset map are established; full CharacterData remains a long tail.</sub> |
| `user-movepath` | ![65%](https://img.shields.io/badge/65%25-in_progress-yellowgreen?style=flat-square) | In progress | local user `0x002C` clean fixture 已 decode/re-encode；MovePath 变体、option gate 与 runtime differential 覆盖仍待扩展。<br><sub>A clean local user `0x002C` movement fixture is decoded/re-encoded; broader MovePath variants, option gates, and runtime differential coverage remain pending.</sub> |
| `npc-move` | ![68%](https://img.shields.io/badge/68%25-attributed-yellowgreen?style=flat-square) | Attributed | `0x00F1` / `0x013A` 已归属为 NPC movement stream，并和 local user movement 分离。<br><sub>`0x00F1` / `0x013A` are attributed as the NPC movement stream and separated from local user movement.</sub> |
| `action` | ![54%](https://img.shields.io/badge/54%25-in_progress-yellowgreen?style=flat-square) | In progress | ActionMan path contract 与 action mapping helpers 已进入 host-side contract；完整资源系统未重构。<br><sub>ActionMan path contracts and action mapping helpers are in the host-side contract set; the full resource system is not reconstructed.</sub> |
| `cstring` | ![45%](https://img.shields.io/badge/45%25-abi_docs-yellow?style=flat-square) | ABI docs | Batch008 已记录 cString accessor、pointer-view、ASCII search/compare 的窄 host-side source-contract facts；不声明生产布局、allocator/lifetime、imported API parity 或 verified。<br><sub>Batch008 records narrow cString accessor, pointer-view, and ASCII search/compare source-contract facts; production layout, allocator/lifetime, imported API parity, and verified status are not claimed.</sub> |
| `sort` | ![40%](https://img.shields.io/badge/40%25-abi_docs-yellow?style=flat-square) | ABI docs | Tier2 shard2 Median neutral 的 6 个 EA table facts 已进入 ABI doc / promotion record；不声明 production sort correctness。<br><sub>Six Tier2 shard2 Median neutral EA table facts are documented in ABI docs / promotion records; production sort correctness is not claimed.</sub> |
| `low-risk-contracts` | ![68%](https://img.shields.io/badge/68%25-expanding-yellowgreen?style=flat-square) | Expanding | 低风险 host-side source contracts 已扩展到 field constants、temporary stat、party quest、minigame、encoding、NM、core、CTRL、interface、data、sort、crypto、Base64、EqSlotInfo、cash text-money 等方向。<br><sub>Low-risk host-side source contracts now cover field constants, temporary stat, party quest, minigame, encoding, NM, core, CTRL, interface, data, sort, crypto, Base64, EqSlotInfo, cash text-money, and related lanes.</sub> |
| `base64` | ![38%](https://img.shields.io/badge/38%25-neutral_contract-yellow?style=flat-square) | Neutral contract | `CBase64::GetCharB64` / `GetValueB64` 已有 neutral scalar mapper contract；不声明完整 codec、padding、buffer 或 runtime parity。<br><sub>`CBase64::GetCharB64` / `GetValueB64` now have neutral scalar mapper contracts; full codec, padding, buffer, or runtime parity is not claimed.</sub> |
| `eqslotinfo` | ![32%](https://img.shields.io/badge/32%25-neutral_contract-orange?style=flat-square) | Neutral contract | `EqSlotInfo::GetX` / `GetY` 已有 neutral coordinate lookup contract；不声明 UI/layout/runtime 语义。<br><sub>`EqSlotInfo::GetX` / `GetY` now have neutral coordinate lookup contracts; UI, layout, and runtime semantics are not claimed.</sub> |
| `cash-text-money` | ![38%](https://img.shields.io/badge/38%25-neutral_contract-yellow?style=flat-square) | Neutral contract | CashTrading text-money 四个 helper rows 已进入 neutral recorder/helper-boundary contract；不声明完整格式化语义。<br><sub>Four CashTrading text-money helper rows now have neutral recorder/helper-boundary contracts; full formatting semantics are not claimed.</sub> |
| `metadata-promotions` | ![88%](https://img.shields.io/badge/88%25-promoted_with_limits-green?style=flat-square) | Promoted with limits | Tier2Ext / ZTL 多个 shard 的 row-identity / opaque-token metadata facts 已进入 formal promotion；这不是 source intake、runtime equivalence 或 verified。<br><sub>Row-identity / opaque-token metadata facts from Tier2Ext and ZTL shards have entered formal promotion; these are not source intake, runtime equivalence, or verified reconstruction.</sub> |
| `tier2-handoff` | ![45%](https://img.shields.io/badge/45%25-pending_handoff-yellow?style=flat-square) | Pending trusted handoff | Claude Tier2 外部报告完成 475 对 `.cpp/.h`；主仓可信 handoff 覆盖 461 对，仍缺 shard3，不能算 source intake。<br><sub>Claude Tier2 is externally reported complete with 475 `.cpp/.h` pairs; trusted main-repo handoff covers 461 pairs and still lacks shard3, so this is not source intake.</sub> |
| `tier2ext-intake` | ![70%](https://img.shields.io/badge/70%25-metadata_promoted-green?style=flat-square) | Metadata promoted with limits | Tier2Ext shard1-18 已从 metadata-only intake 推进到 metadata / opaque-token promoted-with-limits；仍不等于 source intake。<br><sub>Tier2Ext shards 1-18 moved from metadata-only intake to metadata / opaque-token promoted-with-limits; this is still not source intake.</sub> |
| `tier2ext-quarantine` | ![42%](https://img.shields.io/badge/42%25-active_triage-yellow?style=flat-square) | Active triage | Tier2Ext quarantine/Zs plan 覆盖 2218 files；cleanup、/Zs、IDA MCP 顺序已建立，但大量文件仍需 cleanup/quarantine。<br><sub>Tier2Ext quarantine/Zs plan covers 2218 files; cleanup, /Zs, and IDA MCP ordering is established, but many files still require cleanup/quarantine.</sub> |

### Runtime Milestones / Runtime 里程碑

| Milestone | Status | Description / 说明 |
|---|---|---|
| Login smoke | ![passing](https://img.shields.io/badge/passing-brightgreen?style=flat-square) | 登录链路可通过自动化 smoke。<br><sub>Login flow passes automation smoke.</sub> |
| Character select smoke | ![passing](https://img.shields.io/badge/passing-brightgreen?style=flat-square) | 选人流程可进入后续 migration。<br><sub>Character select can proceed into migration.</sub> |
| Field entry map `10000` | ![passing](https://img.shields.io/badge/passing-brightgreen?style=flat-square) | clean baseline 可见进入 tutorial map。<br><sub>Clean baseline reaches visible tutorial map.</sub> |
| Field CRC clean baseline | ![matched](https://img.shields.io/badge/matched-brightgreen?style=flat-square) | map `10000` 的 live client CRC 与 Kinoko 对照值匹配。<br><sub>Live client CRC for map `10000` matches the Kinoko comparison value.</sub> |
| Portal `tuto00` path | ![matched](https://img.shields.io/badge/matched-brightgreen?style=flat-square) | `UserPortalScriptRequest(0x0070)` 正常触发 `tutoChatNPC`。<br><sub>`UserPortalScriptRequest(0x0070)` correctly reaches `tutoChatNPC`.</sub> |
| Formal promotions | ![6937](https://img.shields.io/badge/6937-blue?style=flat-square) | 当前 formal promotions 为 6937；verified 仍为 0。主要是 metadata / opaque-token / row-identity facts。<br><sub>Current formal promotions are 6937; verified remains 0. These are mostly metadata / opaque-token / row-identity facts.</sub> |
| Verified | ![0](https://img.shields.io/badge/0-lightgrey?style=flat-square) | 仍没有 verified reconstruction。<br><sub>No verified reconstruction status is claimed.</sub> |
| ZTL shard7 V__ZRef metadata | ![372 facts](https://img.shields.io/badge/372_facts-promoted-blue?style=flat-square) | 372 个 row-identity / opaque-token metadata facts 已 promotion；source-contract lane 仍 blocked。<br><sub>372 row-identity / opaque-token metadata facts promoted; the source-contract lane remains blocked.</sub> |
| ZTL dirty-filtered metadata | ![1659 facts](https://img.shields.io/badge/1659_facts-promoted-blue?style=flat-square) | 1659 个 active row-identity / opaque-token metadata facts 已 promotion。<br><sub>1659 active row-identity / opaque-token metadata facts promoted.</sub> |
| ZTL shard10 metadata | ![78 facts](https://img.shields.io/badge/78_facts-promoted-blue?style=flat-square) | 78 个 row-identity / opaque-token metadata facts 已 promotion。<br><sub>78 row-identity / opaque-token metadata facts promoted.</sub> |
| Base64 neutral contract | ![reviewed](https://img.shields.io/badge/reviewed_with_limits-yellowgreen?style=flat-square) | Base64 neutral scalar helper/test/runner contract 已 review；不声明完整 codec parity。<br><sub>Base64 neutral scalar helper/test/runner contract is reviewed; full codec parity is not claimed.</sub> |
| Full `CharacterData` | ![partial](https://img.shields.io/badge/partial-orange?style=flat-square) | 当前 fixture map 较强，但完整 nested decode 未完成。<br><sub>Current fixture map is strong, but full nested decode is not complete.</sub> |
| Full `MovePath` variants | ![partial](https://img.shields.io/badge/partial-orange?style=flat-square) | core body 与一个 clean sample 已验证；更多 attr/option/tail 变体待补。<br><sub>Core body and one clean sample are validated; more attr/option/tail variants are pending.</sub> |

### Server / Data / Localization

| Module | Progress | Status | Description / 说明 |
|---|---:|---|---|
| `kinoko` | ![68%](https://img.shields.io/badge/68%25-stable_progress-yellowgreen?style=flat-square) | Stable progress | 作为当前主服务端对照与自动化测试台，clean CRC/portal baseline 稳定。<br><sub>Current main server comparison target and automation testbed, with stable clean CRC/portal baseline.</sub> |
| `space2d-crc` | ![72%](https://img.shields.io/badge/72%25-baseline_matched-green?style=flat-square) | Baseline matched | proof map 已对齐，广域 map corpus 与 linked-map 仍待扩展。<br><sub>Proof maps match; broader map corpus and linked-map coverage remain pending.</sub> |
| `portallist-crc` | ![78%](https://img.shields.io/badge/78%25-baseline_matched-green?style=flat-square) | Baseline matched | `tuto00` 正常路径和 portal CRC 已在 clean run 对齐，旧 NUL 现象降级为 stale。<br><sub>Normal `tuto00` path and portal CRC match in clean runs; older NUL observations are treated as stale.</sub> |
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
