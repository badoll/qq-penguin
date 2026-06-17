# QQ Penguin Codex Pet（非官方）

这是一个供 Codex Pet 使用的自定义宠物资源包。当前形象基于 QQ 宠物企鹅的记忆点生成与整理，采用像素风黑白企鹅、红围巾和轻量动画表现，适合作为 Codex 工作时的桌面陪伴宠物。

本项目不是腾讯或 QQ 宠物的官方项目，也未获得官方背书。QQ、QQ 宠物及相关角色形象、商标与品牌资产归原权利方所有；本仓库仅用于个人学习、怀旧创作与 Codex Pet 资源包示例。

## 效果与规格

资源包由 Codex Pet 读取：

- `pet.json`：宠物元数据。
- `spritesheet.webp`：透明背景动画图集。

当前 `spritesheet.webp` 已通过 Codex Pet 图集校验：

- 图集尺寸：`1536x1872`
- 单元格尺寸：`192x208`
- 布局：`8` 列 x `9` 行
- 格式：带透明通道的 WebP
- 透明像素残留：`0`

动画行约定：

| 行 | 状态 | 使用列 |
| --- | --- | --- |
| 0 | `idle` | 0-5 |
| 1 | `running-right` | 0-7 |
| 2 | `running-left` | 0-7 |
| 3 | `waving` | 0-3 |
| 4 | `jumping` | 0-4 |
| 5 | `failed` | 0-7 |
| 6 | `waiting` | 0-5 |
| 7 | `running` | 0-5 |
| 8 | `review` | 0-5 |

未使用的格子应保持完全透明。

## 安装

将本目录放到 Codex 的宠物目录下即可：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/pets"
cp -R qq-penguin "${CODEX_HOME:-$HOME/.codex}/pets/qq-penguin"
```

目录中至少需要包含：

```text
qq-penguin/
  pet.json
  spritesheet.webp
```

如果 Codex 已经在运行，安装后可能需要重启或刷新 Codex 才能看到新宠物。

## 文件说明

```text
.
├── pet.json
├── spritesheet.webp
├── hover-jumping-6frame-strip.png
├── hover-jumping-ref-8frame-strip.png
├── hover-jumping-ref-codex-5frame-row.png
├── spritesheet.before-forward-kick.webp
├── spritesheet.before-ref-redraw-20260617T1605.webp
└── spritesheet.forward-kick-v2.webp
```

- `spritesheet.webp` 是当前推荐使用的最终图集。
- `spritesheet.before-*` 和 `spritesheet.forward-kick-v2.webp` 是历史版本或对照版本。
- `hover-jumping-*.png` 是悬停/跳跃动画的参考帧条，可用于继续迭代动作。

## 开发与校验

如需替换或重新生成图集，请保持 Codex Pet 的固定规格：`1536x1872` 总尺寸、`192x208` 单元格、透明背景，以及 9 行状态顺序。

可使用 hatch-pet 校验脚本检查最终图集：

```bash
python3 "$HOME/.codex/skills/hatch-pet/scripts/validate_atlas.py" \
  spritesheet.webp \
  --json-out /tmp/qq-penguin-validation.json
```

也可以快速检查 WebP 画布：

```bash
webpmux -info spritesheet.webp
```

## 授权与权利说明

本仓库中的贡献者原创文档、配置和不包含第三方权利元素的工程内容按 `LICENSE` 授权。

但本项目的视觉方向受 QQ 宠物企鹅形象启发。QQ、QQ 宠物及相关角色形象、名称、商标、品牌资产与原始版权不属于本仓库贡献者，亦不随本仓库许可证授权。若你计划商业使用、公开分发修改版，或在产品中使用该形象，请自行确认并取得必要授权；更稳妥的方式是替换为完全原创的宠物形象。

更多说明见 `NOTICE.md`。
