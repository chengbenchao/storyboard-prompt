---
name: storyboard-prompt
description: >
  短剧分镜自动化工作流：从剧本→分镜表/场景表/人设表/道具表→分镜关键帧提示词→视频分镜提示词。
  支持逐集/批量模式，分步审核闸门，输出飞书Bitable+Docx。
  生图提示词复用 xiameng-prompt-engineer（夏导引擎10维度），视频提示词适配Seedance/可灵/即梦。
  触发：生成分镜表、场景表、角色人设、道具表、场景关键帧、道具关键帧、分镜关键帧提示词、视频分镜提示词、短剧分镜。
---

# 短剧分镜自动化工作流

## 能力总览

| # | 能力 | 输出格式 |
|---|------|---------|
| 1 | 分镜表生成 | Bitable表 + Docx表格 |
| 2 | 场景表生成 | Bitable表 + Docx表格 |
| 3 | 角色人设表 | Bitable表 + 三视图+特写提示词 |
| 4 | 道具表生成 | Bitable表 + 道具提示词 |
| 5 | 分镜关键帧提示词 | AI生图提示词（每镜一条） |
| 6 | 视频分镜提示词 | AI视频提示词（每镜一条） |

## 操作模式

- **逐集模式**：用户说"生第X集"→ 处理单集
- **批量模式**：用户说"生成全部"→ 处理全剧

## 分步工作流（分步审核）

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
Step 7: 生成视频分镜提示词 → Seedance格式，每镜一条
         ↓ [完成]
```

## 快速指令路由

| 用户说 | 触发 | 需读 references |
|--------|------|----------------|
| "生成分镜表" / "生第X集分镜" | Step 2 | `table-format.md`（分镜表章节） |
| "生成场景表" | Step 3 | `table-format.md`（场景表章节） |
| "生成角色人设" | Step 4 | `table-format.md`（人设表章节）+ `image-prompt-format.md` |
| "生成道具表" | Step 5 | `table-format.md`（道具表章节）+ `image-prompt-format.md` |
| "生成分镜关键帧提示词" | Step 6 | `image-prompt-format.md` |
| "生成视频分镜提示词" | Step 7 | `video-prompt-format.md` |
| "生成全部" | Step 1→7 | 按需读取 |

## 工具链

| 工具 | 用途 |
|------|------|
| `feishu_bitable_*` | 创建/读写多维表格 |
| `lark-cli docs` +fetch/+update | 读写飞书云文档 |
| `xiameng-prompt-engineer` | 生图提示词生成（10维度，可复用） |
