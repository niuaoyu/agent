---
theme: default
title: NIUAOYU · Personal Portfolio
info: |
  一份用 Slidev 制作的个人展示与成长记录。
author: NIUAOYU
keywords: Java, Spring Boot, Vue, Full Stack, Portfolio
transition: slide-left
mdc: true
aspectRatio: 16/9
canvasWidth: 1440
drawings:
  persist: false
---

<div class="grid-bg" />

<div class="cover-layout">
  <div class="cover-copy">
    <div class="eyebrow">Personal Portfolio · 2026</div>
    <h1 class="cover-title">
      BUILD.<br>
      <span class="outline">LEARN.</span><br>
      <span class="highlight">GROW.</span>
    </h1>
    <p class="cover-description">
      你好，我是 <b>NIUAOYU</b>。一名正在用真实项目建立能力闭环的
      <b>Java 全栈开发学习者</b>。
    </p>
    <div class="cover-meta">
      <span class="meta-chip"><i /> Open to learn</span>
      <span class="meta-chip mono">Java / Spring / Vue</span>
    </div>
  </div>

  <div class="portrait-wrap">
    <div class="portrait-card">
      <div class="portrait-card__code">
        <div><span class="key">class</span> Developer &#123;</div>
        <div>&nbsp;&nbsp;name = <span class="value">"NIUAOYU"</span>;</div>
        <div>&nbsp;&nbsp;focus = <span class="value">"Full Stack"</span>;</div>
        <div>&nbsp;&nbsp;status = <span class="value">"Building"</span>;</div>
        <div>&#125;</div>
      </div>
      <img src="/avatar.svg" alt="NIUAOYU monogram avatar">
    </div>
    <div class="float-note">
      <strong>01 → ∞</strong>
      <span>从第一个可运行 Demo 开始</span>
    </div>
  </div>
</div>

---

<SectionLabel index="01" label="About me" />

<div class="two-col">
  <div>
    <h2>不是“准备好了”<br>才开始，<span class="accent">而是在行动中成长。</span></h2>
    <p class="intro-copy">
      我关注的不只是记住语法，而是让一个需求真正经过页面、HTTP、业务逻辑和数据库，最终变成可验证的结果。
    </p>
    <div class="quote" v-click>
      “信心不是训练的前提，<br>而是连续获得完成证据后的结果。”
    </div>
  </div>

  <div class="stat-grid">
    <div class="stat-card dark" v-click>
      <strong>Full</strong>
      <p>坚持理解完整数据流，而不是只看某一个框架。</p>
    </div>
    <div class="stat-card green" v-click>
      <strong>Small</strong>
      <p>每次只增加一个主要难点，让错误可以被定位。</p>
    </div>
    <div class="stat-card" v-click>
      <strong>Run</strong>
      <p>先让功能可运行，再逐步校验、测试、重构。</p>
    </div>
    <div class="stat-card" v-click>
      <strong>Repeat</strong>
      <p>修改、排错、关闭答案后复现，形成长期记忆。</p>
    </div>
  </div>
</div>

---

<SectionLabel index="02" label="Tech stack" />

<div class="skill-layout">
  <div>
    <h2>我正在构建的<br><span class="highlight">能力栈</span></h2>
    <p class="intro-copy">
      百分比不是“精通度”，而是我当前投入时间与项目覆盖范围的可视化。
    </p>
    <div class="tool-cloud" v-click>
      <span>JAVA</span><span>SPRING BOOT</span><span>MAVEN</span>
      <span>REST API</span><span>SQL</span><span>VUE</span>
      <span>GIT</span><span>DOCKER</span>
    </div>
  </div>

  <div class="skill-panel">
    <SkillBar name="Java / OOP" :value="76" />
    <SkillBar name="Spring Boot / REST" :value="68" color="#ff6a3d" />
    <SkillBar name="SQL / Data Flow" :value="58" color="#7f8cff" />
    <SkillBar name="Vue / Frontend" :value="48" color="#22bd89" />
    <SkillBar name="Testing / DevOps" :value="36" color="#e3af2d" />
  </div>
</div>

---

<SectionLabel index="03" label="How I learn" />

<h2>我的学习闭环：<span class="accent">从输入走向输出</span></h2>

<div class="process">
  <div class="process-step" v-click>
    <span class="num">STEP 01</span>
    <h3>拆需求</h3>
    <p>先写验收标准，再画出数据如何流动。</p>
  </div>
  <div class="process-step" v-click>
    <span class="num">STEP 02</span>
    <h3>独立实现</h3>
    <p>优先自己尝试，卡住时只获取下一步提示。</p>
  </div>
  <div class="process-step active" v-click>
    <span class="num">STEP 03</span>
    <h3>运行验证</h3>
    <p>通过页面、Network、日志与数据库验证结果。</p>
  </div>
  <div class="process-step" v-click>
    <span class="num">STEP 04</span>
    <h3>故意改错</h3>
    <p>制造接口、字段或配置错误，再定位并修复。</p>
  </div>
  <div class="process-step" v-click>
    <span class="num">STEP 05</span>
    <h3>关闭复现</h3>
    <p>离开答案，重新完成核心链路与变式需求。</p>
  </div>
</div>

---

<SectionLabel index="04" label="Selected projects" />

<h2>项目不是收藏夹，<span class="highlight">而是能力证据</span></h2>

<div class="project-grid">
  <ProjectCard
    v-click
    number="PROJECT / 01"
    title="Hello Full Stack"
    description="前端按钮请求 Spring Boot 接口，跑通最小但完整的 HTTP 数据链路。"
    :tags="['Java', 'Spring Boot', 'Fetch']"
    status="DONE"
  />
  <ProjectCard
    v-click
    number="PROJECT / 02"
    title="Text Processor"
    description="页面输入内容，后端完成校验与加工，再把结构化结果返回前端。"
    :tags="['REST', 'JSON', 'Validation']"
    status="BUILDING"
  />
  <ProjectCard
    v-click
    number="PROJECT / NEXT"
    title="Persistent CRUD"
    description="从内存状态走向数据库，完成新增、查询、修改、删除和页面同步。"
    :tags="['SQL', 'JPA', 'Vue']"
    status="NEXT"
  />
</div>

---

<SectionLabel index="05" label="Case study" />

<div class="flow-wrap">
  <div>
    <h2>我如何理解<br><span class="accent">一次完整请求</span></h2>
    <p class="intro-copy">
      不把前端、后端和数据库当成三个孤岛，而是把它们看作一条可观测、可定位、可验证的链路。
    </p>
  </div>

  <div class="flow-stack">
    <div class="flow-item" v-click>
      <span class="icon">UI</span><div><strong>用户操作</strong><small>输入与点击触发业务意图</small></div><code>click()</code>
    </div>
    <div class="flow-item" v-click>
      <span class="icon">HTTP</span><div><strong>前端请求</strong><small>构建 method、URL 与 JSON body</small></div><code>fetch()</code>
    </div>
    <div class="flow-item" v-click>
      <span class="icon">API</span><div><strong>Controller / Service</strong><small>接收、校验并执行业务规则</small></div><code>@PostMapping</code>
    </div>
    <div class="flow-item" v-click>
      <span class="icon">DB</span><div><strong>Repository / Database</strong><small>持久化状态并返回结果</small></div><code>save()</code>
    </div>
    <div class="flow-item" v-click>
      <span class="icon">↩</span><div><strong>页面反馈</strong><small>解析响应，更新界面状态</small></div><code>render()</code>
    </div>
  </div>
</div>

---

<SectionLabel index="06" label="Roadmap" />

<h2>下一段路，<span class="highlight">清晰且可执行</span></h2>

<div class="roadmap">
  <div class="roadmap-item" v-click>
    <span class="date">PHASE 01</span>
    <h3>跑通链路</h3>
    <p>HTTP、JSON、Controller 与页面反馈。</p>
  </div>
  <div class="roadmap-item current" v-click>
    <span class="date">NOW</span>
    <h3>持久化 CRUD</h3>
    <p>数据库、Repository、列表与表单。</p>
  </div>
  <div class="roadmap-item" v-click>
    <span class="date">PHASE 03</span>
    <h3>工程化能力</h3>
    <p>异常处理、测试、日志、Docker 与部署。</p>
  </div>
  <div class="roadmap-item" v-click>
    <span class="date">PHASE 04</span>
    <h3>独立项目</h3>
    <p>从需求拆解到上线，完成可持续迭代产品。</p>
  </div>
</div>

---
layout: center
class: end-layout
---

<div class="end-content">
  <div class="eyebrow" style="color: var(--accent); margin-bottom: 28px">Let’s build something real.</div>
  <h1 class="end-title">保持好奇，持续交付。<span style="color: var(--accent)">下一页，由代码写成。</span></h1>
  <p>
    这是我的个人展示，也是正在发生的成长记录。项目会变多，技术会更新，但“做出可验证结果”会一直保留。
  </p>
  <a class="contact-link" href="https://github.com/niuaoyu" target="_blank">
    GitHub <span>github.com/niuaoyu ↗</span>
  </a>
  <div class="end-footer">
    <span>NIUAOYU / PERSONAL PORTFOLIO</span>
    <span>BUILT WITH SLIDEV + GITHUB PAGES</span>
  </div>
</div>
