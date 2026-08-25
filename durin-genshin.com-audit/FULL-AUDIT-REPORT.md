# Durin Genshin 全站 SEO 审计报告

> 目标域名：`https://www.durin-genshin.com`
> 本地目录：`d:\workspaces\website\durin-genshin`
> 审计类型：**上线前本地技术 SEO 审计**（站点未部署，域名不可解析，无法采集线上 CWV/收录/外链数据）
> 审计日期：2026-08-25

---

## 一、执行摘要（Executive Summary）

| 项 | 结论 |
|---|---|
| **SEO 健康分** | **77 / 100** |
| 站点类型 | 单角色垂直攻略站（Content / Game Guide，单页极致 SEO） |
| 上线状态 | ❌ 未上线（`curl` 返回 000，域名未解析/未部署） |
| 技术栈 | Astro 静态生成 + Tailwind CSS v4 + @astrojs/sitemap |
| 页面数 | 1 张首页长页（无内页） |

**Top 5 关键问题**

1. **[Critical]** 站点未上线，无法被收录。
2. **[High]** H1 仅为「Durin」（5 字符），缺少目标关键词。
3. **[High]** `og:image` 用 SVG，社交平台不支持渲染分享图。
4. **[High]** 页面 0 张真实图片，无 alt 文本。
5. **[Medium]** E-E-A-T 作者块为占位符，无 Person schema。

**Top 5 快速赢点（Quick Wins）**

1. H1 改为「Durin – Genshin Impact Character Guide」。
2. `og.svg` → `og.png`（1200×630）。
3. meta description 精简至 ≤160 字符。
4. 补 favicon。
5. 作者块填真实玩家身份 + Person 结构化数据。

---

## 二、技术 SEO（Technical SEO）— 22 分权重，得分 80

### 达标项
- ✅ Astro 静态生成，构建产物干净，单页无重复内容。
- ✅ 域名统一 `www` 前缀，`trailingSlash: always` 符合站内治理规范。
- ✅ canonical 首页不带尾斜杠（`https://www.durin-genshin.com`），与 sitemap 首页一致。
- ✅ `scripts/fix-sitemap-home.mjs` 构建后处理生效，sitemap-0.xml 首页 URL 无尾斜杠。
- ✅ `robots.txt` 正确 Allow 全部，并引用 `sitemap-index.xml`。
- ✅ `meta robots=index,follow`、`lang="en"`、viewport 完整。
- ✅ `<script>` 内 TypeScript 类型注解被正确剥离（dist 中 0 处残留），交互脚本无语法错误。

### 问题

| 严重度 | 问题 | 建议 |
|---|---|---|
| Critical | 站点未上线，域名不可解析 | 部署 Cloudflare Pages + 裸域名 301 → www + GSC 提交 sitemap |
| High | `og:image` 为 SVG | 改用 1200×630 PNG/JPG |
| Low | 缺 favicon | 补 favicon.ico / apple-touch-icon |

---

## 三、内容质量（Content Quality）— 23 分权重，得分 85

### 达标项
- ✅ 内容深度业界少见：33 条 FAQ + 完整 build + 三阶段剧情时间线 + 材料清单 + 优劣势 + 配队伤害提升数据。
- ✅ 信息增益四件套齐全：竞品对比表（vs 香菱/班尼特）、命座性价比逐层解析、材料刷取成本、避坑清单。
- ✅ 数据已回填核实（专武 Athame Artis、6.6 复刻、霜盏花 168 朵等），符合「角色词建站先核实真实数据」要求。
- ✅ 垂直专一度 + 无付费墙 + 无广告，差异化明确。
- ✅ H2 数量 10 个，符合「每页至少 2 个 H2」规范。

### 问题

| 严重度 | 问题 | 建议 |
|---|---|---|
| Medium | E-E-A-T 作者块为占位（「Editorial Team」，无真实姓名/头像/练度凭证） | 填真实玩家身份 + Person schema |

---

## 四、页面 SEO（On-Page SEO）— 20 分权重，得分 75

### 达标项
- ✅ Title（59 字符）含核心关键词，长度达标。
- ✅ H2/H3 层级清晰，导航为锚点内链。
- ✅ 单页覆盖身份+抽取+培养+剧情+材料五大意图。

### 问题

| 严重度 | 问题 | 建议 |
|---|---|---|
| High | H1 仅「Durin」（5 字符） | 改为「Durin – Genshin Impact Character Guide」 |
| Medium | meta description 约 173 字符，超 160 | 精简至 150-160 字符 |

---

## 五、结构化数据（Schema）— 10 分权重，得分 70

### 现有实现
`WebPage`、`VideoGame`（嵌套）、`FAQPage`（33 条）、`BreadcrumbList`（1 节点）、`HowTo`（5 步）。

### 问题

| 严重度 | 问题 | 建议 |
|---|---|---|
| Medium | BreadcrumbList 仅 1 个节点，基本无效 | 改为两级或移除 |
| Medium | VideoGame 仅作为 about 嵌套，非顶层主实体 | 提升为独立顶层 JSON-LD 并补全属性 |
| Medium | 缺 Person 作者实体 + author meta | 新增 Person schema |
| Low | FAQPage 33 条 / HowTo 富摘要收益有限（Google 已停用） | 保留用于内容覆盖，勿依赖富摘要 |

---

## 六、性能（Performance / CWV）— 10 分权重，得分 88（实验室预估）

### 达标项
- ✅ 静态生成 + 自托管字体，无第三方渲染阻塞脚本。
- ✅ 无大图，仅 2 个小型内联交互脚本，LCP 预估为文本类，应极快。
- ✅ 未接入 gtag，无第三方跟踪脚本开销。

### 问题

| 严重度 | 问题 | 建议 |
|---|---|---|
| Medium | 未接入 analytics，无法衡量性能与流量 | 部署后接入 GA4/gtag（需声明全局类型） |
| Low | 无图片导致缺少视觉锚点 | 上线后 PageSpeed Insights 实测 CWV 基准 |

---

## 七、AI 搜索就绪度（AI Search Readiness）— 10 分权重，得分 75

### 达标项
- ✅ QuickSummary 提供 5 条高密度可引用结论，利于 AI Overview 引用。
- ✅ robots.txt 未屏蔽 AI 爬虫。
- ✅ FAQ 问答对结构化，易被抽取为答案片段。

### 问题

| 严重度 | 问题 | 建议 |
|---|---|---|
| Low | 缺 llms.txt 与作者实体 | 上线后补 llms.txt + Person 实体增强 citability |

---

## 八、图片（Images）— 5 分权重，得分 40

| 严重度 | 问题 | 建议 |
|---|---|---|
| High | 页面 0 张真实图片，无 alt 文本，Hero 仅 CSS 渐变占位 | 版权合规前提下引入角色视觉 + 描述性 alt |

---

## 九、结论

内容侧（内容深度、信息增益、结构化 FAQ）已达到单页极致 SEO 的高水准，是明显的竞争优势；**主要短板集中在「未上线」与「视觉/信任层」**：

1. 当务之急是**部署上线 + www 重定向 + GSC 提交**（否则一切优化无意义）。
2. 上线后优先修复 **H1 关键词缺失、og:image SVG、页面零图片** 三个 High 项。
3. 中后期补 **真实作者实体（E-E-A-T）+ 外链分发**，这是与高 DA 竞品（Fandom/Game8）争夺首页的信任杠杆。

详细分阶段执行见 `ACTION-PLAN.md`。
