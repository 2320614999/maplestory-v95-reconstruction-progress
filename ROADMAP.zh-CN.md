# 路线图

[English](ROADMAP.en-US.md) | [首页](README.md)

> 这是公开路线图，只描述非敏感工程方向。具体 runtime 日志、IDA 数据库、WZ、客户端资产均不公开。

## Phase 0：公开展示仓库

目标：把 public 仓库变成干净的进度展示页。

- [x] 创建 progress-only public 仓库。
- [x] 添加中英双语 README。
- [x] 添加 NOTICE，明确不分发资产和第三方源码树。
- [ ] 添加 `index.html` 中英切换 dashboard。
- [ ] 配置 GitHub Pages。
- [ ] 按审计结果定期更新 progress 表。

## Phase 1：稳定 runtime baseline

目标：保持私有工作区的自动化 smoke 可复现。

- [x] Login smoke passing。
- [x] Character select smoke passing。
- [x] Channel migration 可进入 `MigrateIn`。
- [x] `SetField(0x008D)` 可进入可见 map `10000`。
- [x] clean baseline 下 Field CRC / Space2D CRC / Portal CRC 与 Kinoko 对齐。
- [x] `UserPortalScriptRequest(0x0070)` 正常触发 `tuto00` / `tutoChatNPC`。
- [ ] 把 stale-client / forced-relaunch / deployment state 的诊断规则固定成公开摘要。

## Phase 2：Field / CharacterData

目标：把当前 `SetField` fixture map 推进到更多变体和更完整的 `CharacterData` contract。

- [x] `SetField(0x008D)` prefix 已确认。
- [x] server FILETIME tail anchor 已确认。
- [x] 当前 clean fixture offset map 已建立。
- [ ] 扩展 `CharacterData::Decode` 的 section map。
- [ ] 添加非空/不同装备/不同技能/不同任务状态的变体 fixture。
- [ ] 把 `GW_CharacterStat::Decode` 从当前 fixture 推进到独立 contract。
- [ ] 保持 field-stage `CharacterData` 与 login-stage `AvatarData` 边界分离。

## Phase 3：Movement / MovePath

目标：从单条 clean fixture 扩展到更广泛的 movement variant corpus。

- [x] local user movement `0x002C` 已确认。
- [x] `CVecCtrlUser::EndUpdateActive -> CMovePath::Flush/Encode` 路径已确认。
- [x] 一条 clean 112-byte `0x002C` fixture 已 decode / re-encode。
- [x] NPC movement `0x00F1/0x013A` 已正确归属。
- [ ] 扩展 `MoveElem` attr group 样本。
- [ ] 捕获 option `2` enabled 时的 random-counter 样本。
- [ ] 区分 outbound encode tail 与 inbound non-passive decode 的所有已知路径。
- [ ] 避免把 NPC movement parser 改动泄漏到 local user move contract。

## Phase 4：Kinoko v95 server line

目标：让 Kinoko 成为稳定、严格、可回归的 v95 对照服务端。

- [x] Kinoko v95 baseline 可作为当前测试台。
- [x] map `10000` clean CRC parity matched。
- [x] `104000000` 等 proof map 开始进入对照范围。
- [ ] 建立 map CRC / portal CRC / Space2D CRC corpus。
- [ ] 建立 packet fixture / golden test 体系。
- [ ] 保持 temporary workaround 默认关闭或显式 gated。
- [ ] 整理 v95 服务端生态资源可信度目录。

## Phase 5：Localization / Ecosystem

目标：建立非资产化的汉化和生态资源目录。

- [ ] 建立 WZ tooling catalog。
- [ ] 建立 v95 server ecology catalog。
- [ ] 设计 localization overlay JSON schema。
- [ ] 导出 String/Quest/UI 文本索引。
- [ ] 建立 untranslated report / length-risk report / glyph-risk report。
- [ ] 保证 public 仓只发布 overlay 说明和差异报告，不分发 WZ。

## Phase 6：Long-term client reconstruction

目标：逐步从证据和 host-side contracts 走向更完整的语义重构。

- [ ] 扩展 UI、pool、mob、NPC、drop、reactor 等模块。
- [ ] 扩展 WZ/ResMan/ActionMan 语义边界。
- [ ] 建立更完整的 socket/encryption/buffer lifecycle 模型。
- [ ] 将更多 IDA/runtime 证据 promotion 成最小可维护 contract。
- [ ] 长期探索可替代客户端或跨架构移植可能性。
