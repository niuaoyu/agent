# gzh — 公众号自动排版发布工具

## What This Is

一个本地命令行工具，把每天写好的纯文本正文自动套用固定模板排版成微信公众号文章，通过浏览器自动化把草稿建好、图片选好、封面设好，最后停在「定时发布」那一步交给人工点确认。

服务对象是单个作者、单个公众号（要旅游的每一天 / LittleSpark7602），日更，固定早上 7:05 定时发布。

## Core Value

**把「每天发一篇」这件事，从手工排版 + 逐张贴图 + 设封面 + 设定时，压缩成「写正文 → 敲一条命令 → 点一下确认」。**

如果排版结果和手工做出来的不像素级一致，这个工具就没有价值——因为用户会退回手工重做。

## Requirements

### Validated

(None yet — ship to validate)

### Active

- [ ] 从 txt 读取内容：首行标题 → 空行 → 正文，正文已由作者分好行
- [ ] 正文按行渲染：一行 = 一个 `<section>`，18px，黑色，内联样式
- [ ] 自动生成开头语 `又是美好的一天，祝您开心每一天（MMDD）`，日期自动填充
- [ ] 自动拼接固定尾部块（分割线 / 正文完 / 三行说明 / 分享今日图片 / 俯卧撑 / 跳绳）
- [ ] 从本地图片文件夹随机挑 7 张，插入底部「分享今日图片：」之后
- [ ] 封面图从选中的 7 张里随机取 1 张
- [ ] 浏览器自动化：登录公众号后台、新建草稿、灌入排版后的内容、上传图片、设置封面与标题
- [ ] 流程停在「定时发布 7:05」确认前，把控制权交回人工
- [ ] 输出可预览的 HTML，便于自动化失败时手动兜底粘贴

### Out of Scope

- **官方 API 发布**（草稿箱 / freepublish 接口）— 个人未认证订阅号无接口权限，拿不到
- **自建定时调度器**（cron / 常驻进程 / CI）— 微信后台自带定时发布按钮，无需重造
- **俯卧撑 / 跳绳计数的状态管理与累加**— 作者确认数字已固定不再变化，退化为静态文本
- **多账号、多用户、权限体系**— 单人单号自用
- **Web 后台界面**— CLI 形态已满足
- **AI 推断文章结构**— 输入已分好行、标题已写好，规则确定性优于模型判断
- **全自动点击「定时发布」**— 最脆弱且不可逆的一步，刻意保留人工确认
- **Markdown / Word 解析**— 输入就是纯文本

## Context

### 账号与接口现实

- 账号类型：**个人订阅号，未认证** — 微信的草稿箱接口和发布接口只对已认证账号开放，本项目拿不到
- 因此发布链路**只能走网页端浏览器自动化**，没有第二条路
- 定时发布：微信后台在草稿点「发布」后会跳转到新页面，那里有定时发布按钮 — 直接用它
- 实际发布时间记录：0513 篇 07:07、0802 篇 07:09，与设定的 7:05 吻合

### 模板来源

模板不是凭空设计的，是从作者两篇真实文章逆向出来的（`只和靠谱的人一起玩0513.html/md`、`一个人的成长上限…0802.html/md`）。**以 0802 版为当前模板**。

### 0802 模板结构（HTML 实测顺序，权威）

```
开头语      又是美好的一天，祝您开心每一天（0802）
正文        每行一个 <section>，18px，黑色
──── <hr> 细分割线 ────
正文完      居中
在这里，分享个人生活上遇到的各种问题，以及解决办法。
提供一个日常反思进步的环境，您可以时不时看一下。
如果对您有帮助，是我的荣幸，欢迎在评论区分享您的想法，观点。
分享今日图片：
【7 张图】  每张 <section style="display:inline-block"><img></section>
今日俯卧撑：0      累计俯卧撑：26600
今日跳绳：0     累计跳绳：196000
```

标题格式：`{主题}（MMDD）`
文件命名惯例：`{主题去标点}{MMDD}.txt`

### 关键样式指纹

- 段落容器是 `<section>`，**不是** `<p>`（老模板用 `<p>`，新模板已改）
- 正文字号 `font-size: 18px`，**无 color 属性**（继承黑色）
- 部分正文行带 `letter-spacing: 0.034em`、`background-color: transparent` — 微信编辑器留下的痕迹
- 分割线：`<hr style="border-style:solid;border-width:1px 0 0;transform:scale(1,0.5);transform-origin:0 0">`
- 图片包裹：`<section><section style="display:inline-block"><img …></section></section>`
- 尾部块统一 `text-align:left`，「正文完」单独 `text-align:center`

### 老模板（0513）差异存档

作者已弃用，仅作参考：正文是蓝色 `rgb(61,170,214)`、段落用 `<p>`、字距 `0.578px`、头图在顶部只有 1 张、尾部含「欢迎关注公众号 / 加私人微信」、只有俯卧撑没有跳绳。

## Constraints

- **接口权限**：无公众号 API 权限 — 未认证个人订阅号，发布必须走网页端
- **样式兼容**：微信编辑器会过滤 `<style>` 标签和外部 CSS — 所有样式必须内联
- **页面依赖**：浏览器自动化依赖微信后台 DOM 结构 — 微信改版会直接打断链路，需要可维护的选择器策略和明确的失败兜底
- **登录态**：后台需扫码登录，会话有有效期 — 需要 cookie 持久化和过期时的清晰提示
- **保真度**：排版结果必须与手工产出视觉一致 — 这是工具存废的判据，不是加分项
- **形态**：命令行工具，本地运行，单人单号

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| 自动到草稿为止，「定时发布」人工点确认 | 无 API 权限只能操控浏览器；发布不可逆，最脆弱的一环留给人 | — Pending |
| 复用微信后台自带的定时发布 | 官方接口不支持传发布时间；后台已有此功能，自建调度器纯属重造 | — Pending |
| 一行 = 一个段落，不做结构推断 | 输入已由作者分好行，规则确定性远优于 AI 判断，且零成本 | — Pending |
| 运动数据（俯卧撑/跳绳）作为静态文本 | 作者确认数字不再变化，省掉全部状态管理与持久化 | — Pending |
| 以 0802 模板为准，0513 存档 | 作者已更新模板；同时保留差异记录以防回退 | — Pending |
| 必须同时输出可预览 HTML | 浏览器自动化必然有失效的一天，需要手工粘贴的降级路径 | — Pending |

## Evolution

This document evolves at phase transitions and milestone boundaries.

**After each phase transition** (via `/gsd-transition`):
1. Requirements invalidated? → Move to Out of Scope with reason
2. Requirements validated? → Move to Validated with phase reference
3. New requirements emerged? → Add to Active
4. Decisions to log? → Add to Key Decisions
5. "What This Is" still accurate? → Update if drifted

**After each milestone** (via `/gsd-complete-milestone`):
1. Full review of all sections
2. Core Value check — still the right priority?
3. Audit Out of Scope — reasons still valid?
4. Update Context with current state

## Open Questions

留待 `/gsd-discuss-phase 1` 敲定，不阻塞路线图：

1. 图片数量固定 7 张，还是取文件夹当日全部？挑选是否纯随机？
2. 正文首句「听到一句话」与尾句「好，今天就聊这些，各位看客明天见！」— 属于作者每日手写，还是固定块由工具自动加？
3. 正文颜色以 0802 黑色为准（推定如此），是否需要做成可配置以便切回蓝色？
4. 图片文件夹的具体路径与组织方式（是否按主题分子目录）？

---
*Last updated: 2026-08-02 after initialization*
