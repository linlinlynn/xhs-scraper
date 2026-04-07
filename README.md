# xhs-scraper

Claude Code skill：小红书帖子采集与整理工具。

## 功能

- 按关键词搜索小红书帖子
- 逐篇采集正文、评论、图片 OCR 内容
- 按发帖人类型（官方帖 / 媒体帖 / 用户帖）自动归档
- 生成结构化总结报告

## 安装

```bash
# 克隆到本地 skills 目录
git clone https://github.com/<your-username>/xhs-scraper.git ~/.agents/skills/xhs-scraper

# 创建符号链接（让 Claude Code 识别）
ln -sf ../../.agents/skills/xhs-scraper ~/.claude/skills/xhs-scraper
```

## 使用

在 Claude Code 中输入：

- `/xhs-scraper`
- 或说"爬小红书看看 xxx 相关的帖子"

## 依赖

- [chrome-devtools MCP](https://github.com/GoogleChromeLabs/chrome-devtools-mcp) — 用于浏览器自动化
- Chrome 浏览器（需手动登录小红书）

## 目录结构

```
├── SKILL.md                        # 主 skill 定义（工作流指令）
└── references/
    └── output-template.md          # 输出文件模板参考
```
