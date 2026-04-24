# storyboard-prompt 短剧分镜自动化Skill
> OpenClaw生态下的短剧全链路分镜自动化工作流，一键从剧本生成专业分镜表、提示词，适配AI生图/视频工具。

## ✨ 核心能力
| 能力 | 输出格式 | 适配工具 |
|------|---------|----------|
| 分镜表生成 | Bitable表 + Docx表格 | 飞书文档 |
| 场景表生成 | Bitable表 + Docx表格 | 飞书文档 |
| 角色人设表 | Bitable表 + 三视图+特写提示词 | xiameng-prompt-engineer（夏导引擎） |
| 道具表生成 | Bitable表 + 道具提示词 | xiameng-prompt-engineer（夏导引擎） |
| 分镜关键帧提示词 | AI生图提示词（每镜一条） | Midjourney / DALL-E / Stable Diffusion |
| 视频分镜提示词 | AI视频提示词（每镜一条） | Seedance 2.0 / 可灵 / 即梦 |

## 🎯 触发指令
用户说以下关键词即可自动触发对应功能：
- 分镜相关：生成分镜表、生第X集分镜、短剧分镜
- 表格相关：生成场景表、生成角色人设、生成道具表
- 提示词相关：生成分镜关键帧提示词、生成视频分镜提示词
- 全流程：生成全部、全链路分镜生成

## 📋 分步工作流（支持审核闸门）
```
Step 1: 解析剧本 → 提取集数/场景/人物/冲突 → 输出解析报告
         ↓ [用户确认]
Step 2: 生成分镜表 → Bitable + Docx，每集10-13镜，每镜≤5秒
         ↓ [用户确认]
Step 3: 生成场景表 → Bitable + Docx，场景清单+光影氛围
         ↓ [用户确认]
Step 4: 生成角色人设表 → Bitable + 三视图+特写提示词
         ↓ [用户确认]
Step 5: 生成道具表 → Bitable + 道具提示词
         ↓ [用户确认]
Step 6: 生成分镜关键帧提示词 → 复用夏导引擎10维度，每镜一条
         ↓ [用户确认]
Step 7: 生成视频分镜提示词 → Seedance 2.0格式，每镜一条
         ↓ [完成]
```

## 📚 内置格式规范
所有输出严格遵循预设规范，保证一致性：
- [表格格式规范](references/table-format.md)：分镜表/场景表/人设表/道具表统一格式
- [生图提示词规范](references/image-prompt-format.md)：兼容xiameng-prompt-engineer 10维度标准
- [视频提示词规范](references/video-prompt-format.md)：适配Seedance 2.0官方格式要求

## 🚀 安装使用
### 方式1：通过ClawHub安装（推荐）
```bash
clawhub install storyboard-prompt
```

### 方式2：手动安装
1. 克隆仓库到OpenClaw技能目录
```bash
git clone https://github.com/chengbenchao/storyboard-prompt.git ~/.openclaw/skills/storyboard-prompt
```
2. 重启OpenClaw服务即可自动加载

## 📝 使用示例
### 示例1：生成单集分镜
用户输入：`生第3集分镜`
输出：
1. 第3集分镜表（Bitable + Docx）
2. 对应场景表
3. 涉及角色人设提示词
4. 涉及道具提示词
5. 分镜关键帧生图提示词
6. 视频分镜Seedance格式提示词

### 示例2：仅生成视频提示词
用户输入：`生成第3集视频分镜提示词`
输出：符合Seedance 2.0规范的单镜提示词列表，可直接导入Seedance生成视频

## 🛠️ 依赖技能
- `xiameng-prompt-engineer`：生图提示词10维度生成引擎（可选，生图功能需要）
- `feishu_bitable_*`：飞书多维表格操作能力（内置，无需额外安装）
- `lark-cli`：飞书文档操作能力（内置，无需额外安装）

## 📄 许可证
MIT License
