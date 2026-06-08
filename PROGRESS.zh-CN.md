# GMS v95 重构进度

[English](PROGRESS.en-US.md) | [首页](README.md)

> 本页是公开进度摘要，不是完整源码审计，也不分发客户端资产。

## 总览

当前私有工作区已经形成稳定的 runtime baseline：登录、选人、channel migration、`SetField(0x008D)`、可见进图、Field CRC clean baseline、正常 `tuto00` portal script request、以及一个 clean local-player movement fixture 都已有证据支撑。

公开进度表中的百分比表示**证据与公开展示成熟度**，不是完整客户端源码还原百分比。

## Core Reconstruction

| 模块 | 进度 | 状态 | 说明 |
|---|---:|---|---|
| Workspace / Git hygiene | 80% | 稳定 | 私有工作区结构清晰，客户端/WZ/IDB 等资产保持 local-only。 |
| Packet primitives | 55% | 推进中 | `CInPacket` / `COutPacket` host-side value model 已覆盖基础读写语义。 |
| ZTL / ZXString / ZRef | 50% | 推进中 | `ZXStringW`、`ZRef` hidden-result pointer 等关键 ABI 边界已记录。 |
| Network / CClientSocket | 30% | 早期 | 已有 socket/packet seam skeleton；raw socket、encryption、buffer lifecycle 未完整建模。 |
| Login / AvatarData | 45% | 推进中 | `SelectWorldResult`、`AvatarLook::Decode` 有 IDA/runtime 证据；完整 login packet set 未完成。 |
| Field / SetField | 65% | 重点推进 | `SetField(0x008D)` prefix、FILETIME tail、当前 fixture offset map 已建立。 |
| User / MovePath | 55% | 推进中 | local user `0x002C` clean fixture 已 decode；MovePath 变体覆盖仍不足。 |
| ActionMan / Resource path | 45% | 推进中 | 资源路径与 String ABI 的 root-cause 边界已缩小，但完整资源系统未重构。 |

## Runtime Milestones

| 里程碑 | 状态 | 说明 |
|---|---|---|
| Login smoke | Passing | 登录链路可通过自动化 smoke。 |
| Character select smoke | Passing | 选人流程可进入后续 migration。 |
| Channel migration | Passing | `SelectCharacter` 后可切入 channel-side `MigrateIn`。 |
| Field entry map `10000` | Passing | clean baseline 可见进入 tutorial map。 |
| Field CRC clean baseline | Matched | map `10000` 的 live client CRC 与 Kinoko 对照值匹配。 |
| Portal `tuto00` path | Matched | `UserPortalScriptRequest(0x0070)` 正常触发 `tutoChatNPC`。 |
| Local user move `0x002C` | Fixture decoded | 已有一条 clean 112-byte movement fixture。 |
| NPC movement `0x00F1/0x013A` | Attributed | 已确认是 NPC movement stream，不再混入 local user move。 |
| Full CharacterData | Partial | 当前 fixture map 较强，但完整 nested decode 未完成。 |
| Full MovePath variants | Partial | core body 与一个 clean sample 已验证；更多 attr/option/tail 变体待补。 |
| Full client replacement | Long-term | 仍是长期目标，目前不是可替代客户端源码。 |

## Server / Data / Localization

| 模块 | 进度 | 状态 | 说明 |
|---|---:|---|---|
| Kinoko v95 baseline | 65% | 稳定推进 | 作为当前主服务端对照与自动化测试台。 |
| Space2D CRC | 70% | 匹配基线 | proof map 已对齐，广域 map corpus 仍待扩展。 |
| PortalList CRC | 75% | 匹配基线 | `tuto00` 正常路径和 portal CRC 已在 clean run 对齐。 |
| WZ / localization overlay | 10% | 规划中 | 计划做 overlay/catalog，不分发 WZ。 |
| Ecosystem catalog | 10% | 规划中 | 计划整理 v95 服务端、WZ 工具、汉化资源的可信度目录。 |

## 当前重点

1. 继续扩展 `CharacterData::Decode` 的 section map 和变体样本。
2. 扩展 `MovePath` attr groups、option-gated random counters、keypad/rect tail 样本。
3. 保持 Kinoko 服务端作为严格对照组，避免把临时 workaround 升级成协议事实。
4. 建立 public progress 展示页和中英双语说明。
5. 建立 localization overlay / ecosystem catalog 的非资产化目录。

## 不公开内容

本公开进度仓不包含客户端二进制、WZ、IDA 数据库、PDB、完整反编译导出、runtime dump、私有日志或第三方源码树。详见 [`NOTICE.md`](NOTICE.md)。
