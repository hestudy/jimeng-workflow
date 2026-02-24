# jimeng-workflow

Claude Code 插件，用于即梦AI创作工作流，支持视频/图片提示词生成等功能。

## 安装

```bash
/plugin install <marketplace-url>/jimeng-workflow
```

## 使用方法

### 技能（Skills）

自动激活，无需手动调用：

- `seedream-prompts` - Seedream 4.5 图片提示词专家（说"图片提示词"、"文生图"等自动激活）
- `seedance-prompts` - Seedance 2.0 视频提示词专家（说"视频提示词"、"镜头设计"等自动激活）

### 命令（Commands）

**图片提示词（Seedream 4.5）**

- `/jimeng-workflow:seedream-prompts [需求]` - 通用图片提示词生成器
- `/jimeng-workflow:seedream-poster [需求]` - 海报专项（活动/商业/公益/封面）
- `/jimeng-workflow:seedream-infographic [需求]` - 信息图专项（架构图/流程图/食谱卡/科学插图）

**视频提示词（Seedance 2.0）**

- `/jimeng-workflow:seedance-prompts [需求]` - 通用视频提示词生成器，支持 T2V / I2V / V2V
- `/jimeng-workflow:seedance-action [需求]` - 动作/打斗场景（武器对决/追逐/动漫格斗）
- `/jimeng-workflow:seedance-cinematic [需求]` - 电影镜头（一镜到底/蒙太奇/故事板/POV）

### 代理（Agents）

- `seedream-prompt-generator` - Seedream 4.5 图片提示词生成专家
- `seedance-prompt-generator` - Seedance 2.0 视频提示词生成专家

## 开发

本地测试：
```bash
claude --plugin-dir ./jimeng-workflow
```

## 许可证

MIT
