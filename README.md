# Studio Portrait Master

面向亚洲人物照片生成的 Skill，适合健康服务、家庭生活照、人物素材和商业宣传人物。

[![License: MIT](https://img.shields.io/badge/License-MIT-8B6F47.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-8B6F47.svg)](CHANGELOG.md)

## 支持范围

- 中青年单人肖像
- 中青年双人合影
- 中老年单人肖像
- 中老年双人合影
- 儿童单人、儿童双人或按需求生成的亲子人物照片

默认规则是：亚洲面孔、4:3、近景/胸像/自然半身、头部完整露出、简单背景、自然可信的人物状态。服装可以按春夏秋冬、职业、生活和场景要求变化；具体长相和发型不会固定。

## 生成样例

![Studio Portrait Master 生成样例](docs/images/samples-grid.jpg)

覆盖全部五类人物模式，全部为 4:3 画幅、亚洲面孔、头部完整露出、简洁背景。
逐张说明与复现提示词见 [`docs/EXAMPLES.md`](docs/EXAMPLES.md)。

| 模式 | 样例 |
|---|---|
| 中青年单人 | 4 张（含运动风、运动场、棚拍、口腔场景） |
| 中青年双人 | 1 张 |
| 中老年双人 | 3 张（户外、居家、针织） |
| 儿童 | 1 张（积木场景） |

## 安装

将整个 `studio-portrait-master` 文件夹复制到当前使用的 Agent 技能目录：

| Agent | 路径 |
|---|---|
| Codex（Windows） | `%USERPROFILE%\.codex\skills\studio-portrait-master` |
| Codex（macOS/Linux） | `~/.codex/skills/studio-portrait-master` |
| Claude Code | `~/.claude/skills/studio-portrait-master` |

复制后重新打开 Agent 或重新加载技能列表，然后用 `$studio-portrait-master` 调用。

## 示例

```text
使用 $studio-portrait-master，生成一张4:3的中老年夫妻合影，亚洲面孔，秋季针织服装，简单背景，头部完整露出，表现健康幸福。
```

```text
使用 $studio-portrait-master，生成一张4:3的中青年女性单人肖像，春日环境，薄荷绿开衫和米白长裙，头部完整露出，清甜自然。
```

```text
使用 $studio-portrait-master，生成一张4:3的儿童照片，6岁亚洲男孩，夏季公园，明亮自然，不能成人化。
```

## 文件说明

| 文件 | 作用 |
|---|---|
| `SKILL.md` | 核心规则、模式路由、质量检查和负向约束。 |
| `references/prompt-recipes.md` | 五类人物模式的提示词模板和定向修正模板。 |
| `agents/openai.yaml` | 技能名称、简介和默认调用语句。 |
| `USER-GUIDE.html` | 可直接打开的中文启用和使用说明书。 |
| `docs/EXAMPLES.md` | 生成样例说明、覆盖矩阵与复现提示词。 |
| `docs/images/` | 样例图片（9 张单图 + 1 张总览拼图）。 |
| `CHANGELOG.md` | 版本变更记录。 |

## 设计原则

- **先判模式，再填字段。** 用户明确给出的模式、人数、年龄、地点、服装和构图，优先于所有默认值。
- **默认值不重复问。** 4:3、亚洲面孔、完整头部、简单背景这些不该让用户每次都说一遍。
- **修复只修失败点。** 出现头部裁切就只修头部，不连带改年龄、服装和场景。
- **真实性优先于完美。** 毛孔、细纹、发丝飞丝要保留，拒绝蜡像脸和塑料皮肤。

## 贡献

欢迎提 Issue 和 PR。提交前请确认：

1. 改动仍符合 `SKILL.md` 的负向防呆清单，不引入文字水印、塑料皮肤、手部畸形等回归。
2. 涉及规则变更时，同步更新 `CHANGELOG.md`。
3. 提示词模板变更时，同步更新 `references/prompt-recipes.md`。

## License

[MIT](LICENSE)
