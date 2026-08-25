# Durin Genshin 优化行动计划（Action Plan）

> 目标域名：`https://www.durin-genshin.com` · 当前健康分 77/100
> 优先级：Critical > High > Medium > Low

---

## Phase 1：关键修复（Week 1）

| 优先级 | 动作 | 说明 |
|---|---|---|
| Critical | 部署到 Cloudflare Pages | 构建命令 `npx astro build && node scripts/fix-sitemap-home.mjs`，输出目录 `dist/` |
| Critical | 裸域名 301 → www | 遵循「域名统一 www 前缀」治理规范 |
| Critical | GSC 提交 `sitemap-index.xml` | 提交 www 版本站点地图 |
| High | 上线后跑 PageSpeed Insights | 建立 CWV 基准 |

---

## Phase 2：高影响优化（Weeks 2-3）

| 优先级 | 动作 | 涉及文件 |
|---|---|---|
| High | H1 改为「Durin – Genshin Impact Character Guide」 | `src/components/Hero.astro` |
| High | `og.svg` → `og.png`（1200×630），同步 width/height | `public/`、`src/layouts/Layout.astro` |
| High | 页面引入角色视觉图并补描述性 alt | `src/components/Hero.astro` 等 |
| Medium | meta description 精简至 150-160 字符 | `src/pages/index.astro` |
| Low | 补 favicon / apple-touch-icon | `public/`、`src/layouts/Layout.astro` |

---

## Phase 3：内容与权威度（Month 2）

| 优先级 | 动作 | 说明 |
|---|---|---|
| Medium | E-E-A-T 作者块填真实玩家身份 | 姓名/头像/游戏内练度/数据来源链接 |
| Medium | 新增 Person 结构化数据 | 与 WebPage.author 关联 |
| Medium | VideoGame 提升为顶层主实体 | 补全 name/url/datePublished/gameItem |
| Medium | 修复/移除单节点 BreadcrumbList | 改为两级或删除 |
| Medium | Reddit / Hoyolab / Discord 外链分发 | 角色词天然适合社区分发 |

---

## Phase 4：监控与迭代（Ongoing）

| 优先级 | 动作 | 说明 |
|---|---|---|
| Medium | 接入 GA4 / gtag | 需声明全局类型（遵循 Astro 第三方脚本集成规范） |
| Low | 补 `llms.txt` | 提升 AI 爬虫可抓取性与 citability |
| — | 每个版本更新实测数据 | build/材料/复刻，保持「活站」时效信号 |
| — | GSC 监控收录与排名 | 观察核心词 `durin genshin` 排名变化 |
