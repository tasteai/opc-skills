---
created: 2026-03-15T17:58:19
---

# OPC Skills 评估批注

> Fork 自 [ReScienceLab/opc-skills](https://github.com/ReScienceLab/opc-skills)（551 stars, Apache 2.0）
> 评估日期: 2026-03-15
> 评估目的: 筛选对 Digital Brain + 内容创作工作流有价值的 skills

## 仓库质量

- skills.sh 审计: seo-geo 92分, reddit Gen Low Risk / Socket 0 alerts
- 结构规范, 每个 skill 都有标准化 SKILL.md + Python 脚本
- 定位: Solopreneurs / Indie Hackers, 契合我的使用场景

---

## 已采纳 (Adopted)

### reddit
- **状态**: 已安装 (`npx skills add --skill reddit`)
- **安装位置**: `.agents/skills/reddit` → symlink `.claude/skills/reddit`
- **理由**: 填补 Reddit 数据源空白。免费, 无需 API key
- **与现有 skills 的关系**: 和 `reddit-reply-guy` 互补不冲突
  - reddit = 数据层 (搜索/读取 Reddit 内容, research)
  - reddit-reply-guy = 决策层 (找帖子写评论, engagement)
- **使用场景**: 内容选题调研, 竞品分析, 了解 subreddit 讨论趋势

### seo-geo
- **状态**: 已安装 (`npx skills add --skill seo-geo`)
- **安装位置**: `.agents/skills/seo-geo` → symlink `.claude/skills/seo-geo`
- **理由**: 全新能力, 现有 22 个 skills 中无任何 SEO 相关。GEO 概念有价值
- **核心价值**: Princeton 9 种 GEO 方法, 量化的优化效果数据
  - 引用权威来源 +40%, 统计数据 +37%, 专家引述 +30%
- **使用场景**: 优化公众号/博客内容被 AI 搜索引擎引用的概率

---

## 观望中 (Watching)

### nanobanana
- **状态**: 未安装, 待定
- **理由**: 全新图片生成能力, 可为小红书/公众号生成配图
- **阻塞**: 需要 GEMINI_API_KEY, 尚未评估 Gemini 免费额度是否够用
- **纳入条件**: 如果开始频繁需要 AI 生成配图, 且 Gemini 免费额度足够
- **注意**: 是 logo-creator 和 banner-creator 的依赖, 装了它才能解锁设计类 skills

### requesthunt
- **状态**: 未安装, 待定
- **理由**: 需求聚合思路有价值 (Reddit + X + GitHub 反馈), 但与 `tech-research` 目的重叠
- **差异**: tech-research 偏技术调研, requesthunt 偏产品需求/用户痛点
- **纳入条件**: 如果开始做更多产品向的内容创作, 需要系统性收集用户需求

---

## 已跳过 (Skipped)

### twitter
- **理由**: `x-research` skill 已覆盖 X/Twitter 数据访问 (用 Bird CLI + xreach + Grok)
- **且**: `tech-research` 的 Grok 数据源也能拉 X 数据
- **且**: 此 skill 需付费 API (~$0.15-0.18/千次), 性价比低
- **重新评估条件**: 如果 Grok 或 Bird CLI 出问题, 需要备用 Twitter 数据源

### archive
- **理由**: 与现有三层留存系统直接重叠
  - `.claude/memory/MEMORY.md` — 自动持久记忆
  - `session-log` skill — 手动记录到 Daily Note
  - Daily Note 系统 + Git 自动备份 — 完整知识留存链路
- **安装会引入第四个冗余路径, 增加认知负担**
- **重新评估条件**: 无, 除非完全重构记忆系统

### logo-creator
- **理由**: 非高频需求, 且需 3 个 API key (GEMINI + REMOVE_BG + RECRAFT)
- **重新评估条件**: 如果开始做产品品牌建设

### banner-creator
- **理由**: 非高频需求
- **重新评估条件**: 如果开始系统性运营多个平台的 banner

### domain-hunter
- **理由**: 与 PKM/内容创作工作流无关
- **重新评估条件**: 如果开始做独立产品, 需要选域名

### producthunt
- **理由**: 与当前工作流无关
- **重新评估条件**: 如果在 Product Hunt 发布产品

---

## 上游同步策略

- 定期 `git fetch upstream` 检查更新
- 关注新增 skills 是否有适合的
- 已安装的 reddit / seo-geo 通过 `npx skills add` 更新, 不需要从 fork 更新
