# xhs-scraper

Claude Code skill：小红书帖子采集与整理工具。让 AI Agent 帮你自动搜索、采集、分类、归档小红书帖子。

## 功能

- 按关键词搜索小红书帖子，自动提取帖子列表
- 逐篇采集正文、评论（支持多种采集深度）
- 按发帖人类型（官方帖 / 媒体帖 / 用户帖）自动归档
- 原始文本结构化排版（评论压缩单行、回复嵌套）
- 生成结构化报告：数据概览 → 总结 → 详细内容
- 报告直接写入飞书 Wiki（report + raw 附录）
- 图片 OCR 支持（可选）
- 原始文本清洗（可选，每次采集时确认清洗规则）

## 报告结构

```
数据概览
├── 采集统计（篇数、各类型数量、互动汇总）
├── 情感倾向分析（正面/负面/中性占比）
└── 舆论关键词（正/负面高频词）

总结
├── 产品概况
├── 核心功能
├── 更新时间线
├── 渠道与平台
├── 理念与定位
├── 用户反馈（正面 / 负面 / 中性建议）
└── 值得关注的帖子（一句话提炼）

详细内容
├── 官方帖（正文 + 精选评论）
├── 媒体/自媒体帖（正文 + 精选评论）
└── 用户帖（正文 + 精选评论）

帖子链接列表
```

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

在 Claude Code 中：

- `/xhs-scraper`
- 或说"爬小红书看看 xxx 相关的帖子"

运行时会询问：采集篇数、内容类型、评论深度、原始文本清洗规则、是否存档 raw 等参数。

## 依赖

- [chrome-devtools MCP](https://github.com/GoogleChromeLabs/chrome-devtools-mcp) — 浏览器自动化
- Chrome 浏览器（需手动登录小红书）
- [lark-cli](https://github.com/larksuite/cli)（可选）— 输出到飞书 Wiki

## 目录结构

```
├── SKILL.md                        # 主 skill 定义（工作流指令）
└── references/
    ├── report-template.md          # 报告输出格式
    └── raw-template.md             # Raw 文件格式与排版规则
```
