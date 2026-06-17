# 贡献指南

感谢你愿意改进这个 Codex Pet 资源包。这个项目的重点是保持 QQ 宠物企鹅记忆点的同时，让它在 Codex Pet 中稳定、清晰、轻量地运行。

## 可以贡献什么

- 修复 `spritesheet.webp` 中的透明像素、裁切、帧错位或动作不连贯问题。
- 改进某一行动画，但保持同一只宠物的外观、比例、围巾、像素风格和调色。
- 补充安装说明、校验步骤、截图、示例或其他中文文档。
- 提供完全原创、不侵犯第三方权利的新形象替代方案。

## 素材要求

- 图集总尺寸保持 `1536x1872`。
- 单元格保持 `192x208`。
- 行顺序保持：`idle`、`running-right`、`running-left`、`waving`、`jumping`、`failed`、`waiting`、`running`、`review`。
- 未使用格子必须完全透明。
- 不要加入可读文字、Logo、界面截图、二维码或独立漂浮特效。
- 避免新增更接近原权利方官方素材的元素；如需商用或大范围分发，请改用完全原创设计。

## 提交前检查

建议在提交前运行：

```bash
python3 "$HOME/.codex/skills/hatch-pet/scripts/validate_atlas.py" \
  spritesheet.webp \
  --json-out /tmp/qq-penguin-validation.json
```

如果本地没有 hatch-pet 脚本，请至少确认：

- `pet.json` 中的 `spritesheetPath` 指向 `spritesheet.webp`。
- `spritesheet.webp` 是透明 WebP。
- Codex 能正常加载宠物。
- 每个状态的动作语义与 Codex Pet 状态一致。

## Pull Request 建议

请在 PR 中说明：

- 修改了哪些状态行或文档。
- 是否改动最终图集 `spritesheet.webp`。
- 使用了哪些参考素材或生成流程。
- 是否通过图集校验。

涉及外部素材时，请明确来源和授权状态。
