# QQ Penguin Codex Pet（非官方个人使用资源包）

这是一个供 Codex Pet 本地使用的非官方个人资源包。当前图集基于 QQ 宠物企鹅相关视觉素材与特征生成、整理，采用像素风黑白企鹅、红围巾和轻量动画表现，适合作为 Codex 工作时的桌面陪伴宠物。

本项目与腾讯、QQ、QQ 宠物官方没有从属、赞助、授权或背书关系，也不是官方复刻、官方素材包或官方周边。QQ、QQ 宠物及相关标识、角色形象、美术资源、品牌资产、软件程序和衍生内容归原权利方所有；本仓库不主张也不授予这些第三方权利。

本仓库仅用于个人学习、研究、怀旧与 Codex Pet 打包格式交流。README、NOTICE 和 LICENSE 中的声明只能说明项目性质和授权边界，不能替代腾讯或相关权利方的授权。若你希望公开分发、长期维护或商业使用，建议改用完全原创的宠物形象。

## 发布边界

本项目公开内容按以下边界理解：

- 本仓库原创的文档、配置、目录结构说明和 Codex Pet 打包整理工作，按 `LICENSE` 中限定的范围授权。
- `spritesheet.webp` 及 `materials/` 中与 QQ 宠物企鹅相关的素材，不代表你获得腾讯或相关权利方授权，也不随本仓库许可证再授权给他人。
- 请勿将本项目用于收费分发、广告导流、商业运营、官方冒充或任何可能造成来源混淆的场景。
- 如腾讯或其授权代理人认为本仓库内容侵犯其合法权益，请通过 GitHub Issue 或仓库联系方式提出，维护者将优先下架、替换或移除相关素材与发布产物。

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

如果仅做个人本地使用，可将最终产物复制到 Codex 的宠物目录下：

```bash
PET_DIR="${CODEX_HOME:-$HOME/.codex}/pets/qq-penguin"
mkdir -p "$PET_DIR"
cp pet.json spritesheet.webp "$PET_DIR"/
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
├── README.md
├── LICENSE
├── NOTICE.md
├── SECURITY.md
├── pet.json
├── spritesheet.webp
└── materials/
    ├── hover-jumping-6frame-strip.png
    ├── hover-jumping-ref-8frame-strip.png
    ├── hover-jumping-ref-codex-5frame-row.png
    ├── spritesheet.before-forward-kick.webp
    ├── spritesheet.before-ref-redraw-20260617T1605.webp
    └── spritesheet.forward-kick-v2.webp
```

- `spritesheet.webp` 是当前推荐使用的最终图集。
- `pet.json` 是 Codex Pet 读取的宠物元数据。
- `materials/` 存放迭代素材、历史图集版本和动作参考帧条，不参与 Codex Pet 的默认加载。

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

本仓库中的贡献者原创文档、配置和不包含第三方权利元素的工程内容，按 `LICENSE` 中限定的范围授权。

但本项目的视觉方向受 QQ 宠物企鹅形象启发。QQ、QQ 宠物及相关角色形象、名称、商标、品牌资产、美术资源、软件程序与原始版权不属于本仓库贡献者，亦不随本仓库许可证授权。若你计划商业使用、公开分发修改版，或在产品中使用该形象，请自行确认并取得必要授权；更稳妥的方式是替换为完全原创的宠物形象。

更多说明见 `NOTICE.md`。
