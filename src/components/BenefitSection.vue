<script setup>
const integrationLogos = [
  { label: "企", tone: "green" },
  { label: "短", tone: "yellow" },
  { label: "微", tone: "blue" },
  { label: "表", tone: "orange" },
  { label: "档", tone: "ink" },
  { label: "权", tone: "purple" },
  { label: "审", tone: "red" },
  { label: "图", tone: "cyan" },
  { label: "云", tone: "lime" },
]

const tickerLogos = [...integrationLogos, ...integrationLogos]

const supportItems = [
  {
    title: "风险状态清晰",
    text: "风险等级、处理状态和结果说明持续更新，客户可以快速判断建筑是否需要重点关注。",
  },
  {
    title: "适配不同建筑",
    text: "支持不同建筑类型、检测分类和服务内容，让客户看到与自身资产匹配的安全信息。",
  },
  {
    title: "多维信息查看",
    text: "首页、详情、历史和服务日历承接不同查看场景，让客户快速找到所需信息。",
  },
]
</script>

<template>
  <section id="benefits" class="benefit-section section-pad reveal-on-scroll">
    <div class="section-heading benefit-heading">
      <p class="eyebrow">核心优势</p>
      <h2>为客户查看建筑安全而建</h2>
      <p>
        客户 App 围绕建筑状态、风险证据、整改建议和历史服务记录展开，用清晰结构降低理解成本。
      </p>
    </div>

    <div class="benefit-showcase">
      <article class="benefit-card customization-card">
        <h3>围绕客户资产清晰呈现</h3>
        <div class="customization-visual" aria-hidden="true">
          <div class="placeholder-panel">
            <div class="placeholder-swatches">
              <span></span>
              <span></span>
              <span></span>
              <span></span>
              <span></span>
              <span></span>
            </div>
            <div class="placeholder-controls">
              <span></span>
              <span></span>
              <span></span>
            </div>
          </div>
        </div>
        <p>
          <strong>聚合关键内容</strong>，从客户、建筑、服务、计划到报告字段，都能贴合客户查看安全状态的方式。
        </p>
      </article>

      <article class="benefit-card integration-card">
        <h3>连接评估结果与客户服务</h3>
        <div class="integration-marquee" aria-hidden="true">
          <div class="integration-track">
            <span
              v-for="(logo, index) in tickerLogos"
              :key="`${logo.label}-${index}`"
              class="placeholder-logo"
              :class="`tone-${logo.tone}`"
            >
              {{ logo.label }}
            </span>
          </div>
        </div>
        <p><strong>信息集中</strong>，把现场照片、消息通知、报告归档与整改建议放到客户 App，减少反复沟通。</p>
      </article>

      <div class="benefit-support-grid">
        <article v-for="item in supportItems" :key="item.title" class="support-card">
          <h3>{{ item.title }}</h3>
          <p>{{ item.text }}</p>
        </article>
      </div>
    </div>
  </section>
</template>
