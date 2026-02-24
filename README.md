# jimeng-workflow

Claude Code 插件，用于即梦AI创作工作流，支持AI短剧制作、视频/图片提示词生成等功能。

## 安装

```bash
/plugin install <marketplace-url>/jimeng-workflow
```

## 功能

- **AI短剧工作流**: 完整的短剧创作流程，从策划到导出
- **视频提示词生成**: Seedance 2.0 提示词专家
- **图片提示词生成**: Seedream 4.0-4.5 提示词专家
- **角色/场景设计**: 创建一致性控制的角色和场景设定

## 使用方法

### 技能

- `/jimeng-workflow:drama-new` - 创建新的AI短剧项目
- `/jimeng-workflow:drama-plan` - 策划阶段，生成故事大纲
- `/jimeng-workflow:drama-character` - 角色设计
- `/jimeng-workflow:drama-scene` - 场景设计
- `/jimeng-workflow:drama-storyboard` - 分镜脚本
- `/jimeng-workflow:drama-prompt` - Seedance 2.0 视频提示词
- `/jimeng-workflow:drama-image` - Seedream 4.0-4.5 图片提示词
- `/jimeng-workflow:drama-script` - 配音台本
- `/jimeng-workflow:drama-review` - 分镜审核
- `/jimeng-workflow:drama-export` - 导出提示词

### 代理

- `drama-creator` - AI短剧创作代理

## 配置

（如有配置项，在此说明）

## 开发

本地测试：
```bash
claude --plugin-dir ./jimeng-workflow
```

## 许可证

MIT
