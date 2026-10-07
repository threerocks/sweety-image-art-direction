# 图像美术指导

中文 | [English](README.en.md)

把「塑料感」「假光影」「画面稀碎」转成具体的修正指令，保留你选择的画风、人物与构图。

`sweety-image-art-direction` 是一个手动调用的 AI Skill。它负责美术方案、提示词和成图检查，适用于人像、现实场景、商品、海报、信息图与手绘。实际生成和编辑图片使用你当前工具提供的能力。

## 先试一次

上传一张需要修改的图片，然后输入：

```text
使用 $sweety-image-art-direction 修改这张图。
保留人物身份、姿态、构图、配色和画风。
先查看整图，找出影响主体的碎亮点、强边缘与细纹。
本轮只修正这些问题，再检查有没有改变我要求保留的内容。
请生成修改后的图片。
```

只需要提示词时，把最后一句改成「只给修改提示词，不生成图片」。

## 它会处理什么

| 遇到的问题 | 美术指导的处理方式 |
| --- | --- |
| 皮肤、衣服、玻璃看起来都是同一种光泽 | 按材料区分光照响应，检查投影、反射与接触关系 |
| 细节很多，主体却不清楚 | 先组织完整形体、连续明暗与观看主次，再处理局部纹理 |
| 参考图一多，人物和画风互相混淆 | 明确每张参考图提供身份、服装、构图还是画风 |
| 修好一个问题，又改变了人物或构图 | 每轮写清修改目标与保留项，对照原图检查非目标变化 |
| 手绘像照片加了一层纸纹 | 统一造型、色块、笔触与媒介表现 |
| 海报有了主视觉，但文字仍然出错 | 核对准确文案、层级与出现次数，区分版式草图和最终文字排版 |

## 安装

### 在 Codex 中安装

把下面这段话发送给 Codex：

```text
使用 skill-installer 安装 https://github.com/threerocks/sweety-image-art-direction。
Skill 路径为 skills/sweety-image-art-direction，安装名称为 sweety-image-art-direction。
保留 agents/openai.yaml 中仅手动调用的设置。
如果已有同名安装，先核对来源并备份，再更新。
```

安装后，在下一轮对话中输入 `$sweety-image-art-direction` 调用。题材关键词不会自动触发这个 Skill。

安装器下载 ZIP 失败时，可以要求它使用 Git 模式。安装器参数为：

```text
--repo threerocks/sweety-image-art-direction
--path skills/sweety-image-art-direction
--name sweety-image-art-direction
--method git
```

也可以下载仓库，将 `skills/sweety-image-art-direction` 整个目录放入 `${CODEX_HOME:-$HOME/.codex}/skills/`。目录中必须同时保留 `SKILL.md` 和 `agents/openai.yaml`。

更新时让安装器核对来源、备份已有安装，再从本仓库安装。不要假定安装目录是 Git 仓库。

### 其他工具

支持 `SKILL.md` 的工具可以按自身的安装方式加载 `skills/sweety-image-art-direction` 目录。调用语法和手动触发策略取决于宿主工具。没有 Skill 加载能力时，可以把 [SKILL.md](skills/sweety-image-art-direction/SKILL.md) 作为对话指令使用。

Skill 不要求 API 密钥、额外脚本、软件包或其他 Skill。生成图片仍需要宿主提供图像生成能力，相关费用由宿主决定。没有生成能力时，Skill 可以交付美术方案和提示词。

## 使用示例

### 新图：说明主体、用途和画风

```text
使用 $sweety-image-art-direction 生成一张 3:4 商品图。
主体是一只带木柄的白色陶瓷茶壶，放在浅色木桌上。
用途是商品详情页，壶嘴、壶柄和壶盖都要完整入画。
保留陶瓷与木材各自的材料特征，画面不添加文字。
```

### 参考图：分别指定用途

```text
使用 $sweety-image-art-direction 生成一张阅读场景图。
图 1 只提供人物身份，图 2 只提供服装，图 3 只提供水粉画风。
人物坐在窗边读书，双手托住打开的书。
不要把图 2 的模特面孔带进结果，也不要复制图 3 的文字和构图。
```

### 已有图：围绕一个目标修改

```text
使用 $sweety-image-art-direction 修改上传的插画。
保留角色比例、原有饱和颜色和构图。
背景的碎点和强边缘抢走了主体注意力。
请通过完整色块与有方向的笔触修正，不要靠整图模糊或降低饱和度处理。
```

这些是使用示例，未声称是已经验证的生成结果。更完整的输入模板见 [SKILL.md](skills/sweety-image-art-direction/SKILL.md#可直接复制的专业输入)。

## 效果怎样判断

先在预期使用尺寸查看主体和观看主次，再检查脸、手、材料、文字和尺寸。修改已有图时，还要核对人物、构图与其他保留项。

更暗、更柔、道具更少或换了构图，都不能单独证明质量提高。提示词完整、文件可读和安装成功，也不能证明视觉效果通过。Skill 不承诺每张图都能改善；模型、输入和编辑能力会影响结果。

## 从 sweety-skills 迁移

本仓库由 [sweety-skills](https://github.com/threerocks/sweety-skills) 中的同名 Skill 提取。独立版本 `1.0.0` 保留原有两份运行文件，来源为 commit [`5d9ff13`](https://github.com/threerocks/sweety-skills/commit/5d9ff13c809cbf239ab016e0b499a07faa3bc7c0)。版本号从独立仓库重新计算，不代表重写了规则。

今后的规则更新以本仓库为准。已有个人安装可以继续使用；更新时改用本仓库作为来源。如果通过旧版 `sweety-skills` 插件加载了同名 Skill，应避免同时启用两份。

## 文件与许可

- [SKILL.md](skills/sweety-image-art-direction/SKILL.md)：完整执行规则与输入模板。
- [agents/openai.yaml](skills/sweety-image-art-direction/agents/openai.yaml)：Codex 显示名称、默认提示词与手动调用策略。
- [CHANGELOG.md](CHANGELOG.md)：版本记录。
- [LICENSE](LICENSE)：MIT 许可，沿用原仓库声明的许可类型。

方法来源保留在 Skill 的 `SKILL.md` 中。执行规则已经写入文件，使用时不需要访问来源网页。
