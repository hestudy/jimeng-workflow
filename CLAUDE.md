# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个 Claude Code 插件（`jimeng-workflow`），为即梦 AI 的两个核心产品提供提示词生成工具：
- **Seedream 4.5** — 图片生成
- **Seedance 2.0** — 视频生成

## 本地开发

```bash
# 本地测试插件
claude --plugin-dir ./jimeng-workflow
```

## 插件结构

```
agents/          # 代理定义（.md 文件，包含系统提示词和能力描述）
commands/        # 命令定义（.md 文件，用户通过 /jimeng-workflow:命令名 调用）
skills/          # 技能定义（SKILL.md，通过关键词自动激活）
hooks/           # 钩子配置（hooks.json）
.claude-plugin/  # 插件元数据（plugin.json, marketplace.json）
settings.json    # 插件默认配置
```

## 核心架构

### 三层工具体系

1. **Skills**（`skills/*/SKILL.md`）— 关键词自动激活，无需手动调用
   - `seedream-prompts` — 图片提示词（触发词：图片提示词、文生图、Seedream提示词等）
   - `seedance-prompts` — 视频提示词（触发词：视频提示词、镜头设计、Seedance提示词等）

2. **Commands**（`commands/*.md`）— 用户主动调用，针对特定场景深度优化
   - 图片：`seedream-prompts`（通用）、`seedream-poster`（海报）、`seedream-infographic`（信息图）
   - 视频：`seedance-prompts`（通用）、`seedance-action`（动作/打斗）、`seedance-cinematic`（电影镜头）

3. **Agents**（`agents/*.md`）— 专家代理，可被 Skills/Commands 调用
   - `seedream-prompt-generator` — 图片提示词生成专家
   - `seedance-prompt-generator` — 视频提示词生成专家

### 提示词输出规范

所有工具的输出必须包含：
- 主提示词（中文版）
- 英文版（可选）
- 2-3 个风格变体
- 使用建议（宽高比、调整方向）

### Seedream 提示词结构

```
[主体描述] + [风格/氛围] + [构图/视角] + [光线/色彩] + [细节要求] + [--ar 宽高比]
```

宽高比：`2:3`（竖版海报）、`1:1`（正方形）、`16:9`（横版/缩略图）

### Seedance 提示词结构

基础：`[风格标签] + [场景设定] + [主体描述] + [动作/事件] + [镜头语言] + [氛围/光线]`

时间轴（多镜头）：
```
0-3秒：[场景描述，镜头描述]
3-7秒：[场景描述，镜头描述]
```

支持三种模态：T2V（文生视频）、I2V（图生视频，用 `@image1`）、V2V（视频转视频，用 `@video1`）

## 发布插件

插件通过 `.claude-plugin/marketplace.json` 发布到插件市场，用户安装方式：

```bash
/plugin marketplace add hestudy/jimeng-workflow
/plugin install jimeng-workflow@jimeng-workflow
```

## 新增功能时的约定

- 新增图片相关功能：在 `commands/` 下创建 `seedream-*.md`，在 `agents/` 中扩展 `seedream-prompt-generator.md`
- 新增视频相关功能：在 `commands/` 下创建 `seedance-*.md`，在 `agents/` 中扩展 `seedance-prompt-generator.md`
- Skills 的激活关键词定义在 `skills/*/SKILL.md` 文件头部
- 所有 agent 使用 `claude-sonnet-4-6` 模型
