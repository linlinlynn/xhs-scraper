# xhs-scraper

Claude Code skill：小红书帖子采集与整理工具。让 AI Agent 帮你自动搜索、采集、分类、归档小红书帖子。

## 功能

- 按关键词搜索小红书帖子，自动提取帖子列表
- 逐篇采集正文、评论（支持多种采集深度）
- 按发帖人类型（官方帖 / 媒体帖 / 用户帖）自动归档
- 生成结构化总结报告，直接写入飞书 Wiki
- 图片 OCR 支持（可选）

## 实战效果

已用这个 Skill 完成了「指尖农场」的完整调研：

- 采集 12 篇帖子（官方 + 媒体 + 用户），提取原始评论 100+ 条
- 自动按类型归档，生成结构化报告
- 从 raw 数据中提取完整功能拆解（作物系统、动物系统、鱼塘、装修、效率工具等 10+ 模块）
- 总结用户高赞建议 Top 5、舆论关键词、核心反馈方向
- 报告直接输出到飞书 Wiki，零手动排版

从 0 到出报告，全程由 AI Agent + 人协作完成。

## 工作流

```
参数收集 → 搜索帖子 → 逐篇采集（随抓随存 raw） → 自动分类 → 生成报告 → 输出飞书
```

每一步都有兜底设计：登录检测、页面超时跳过、MCP 连接修复、raw 失真预防。

## 安装

```bash
# 克隆到本地 skills 目录
git clone https://github.com/linlinlynn/xhs-scraper.git ~/.agents/skills/xhs-scraper

# 创建符号链接（让 Claude Code 识别）
ln -sf ../../.agents/skills/xhs-scraper ~/.claude/skills/xhs-scraper
```

## 使用

在 Claude Code 中输入：

- `/xhs-scraper`
- 或说"爬小红书看看 xxx 相关的帖子"

运行时会询问采集篇数、内容类型、评论深度、是否存档 raw 等参数。

## 依赖

- [chrome-devtools MCP](https://github.com/GoogleChromeLabs/chrome-devtools-mcp) — 浏览器自动化
- Chrome 浏览器（需手动登录小红书）
- [lark-cli](https://github.com/larksuite/cli)（可选）— 输出到飞书 Wiki

## 目录结构

```
├── SKILL.md                        # 主 skill 定义（工作流指令）
└── references/
    └── output-template.md          # 输出文件模板参考
```

