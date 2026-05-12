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
    title: "实时协同",
    text: "工单状态、风险等级和处理人及时更新，管理者可以快速判断项目是否按计划推进。",
  },
  {
    title: "本地化业务设置",
    text: "支持检测模板、分类、角色权限和服务配置，适配不同机构的检查标准。",
  },
  {
    title: "多视图管理",
    text: "列表、详情、日历和统计看板服务不同岗位，让运营、检测和客户各取所需。",
  },
]
</script>

<template>
  <section id="benefits" class="benefit-section section-pad reveal-on-scroll">
    <div class="section-heading benefit-heading">
      <p class="eyebrow">核心优势</p>
      <h2>为检测团队而建，以简单流程驱动</h2>
      <p>
        系统围绕检测机构和运维团队的日常工作展开，不堆功能，用清晰的数据结构支撑稳定交付。
      </p>
    </div>

    <div class="benefit-showcase">
      <article class="benefit-card customization-card">
        <h3>围绕你的业务流程灵活配置</h3>
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
          <strong>定制每个细节</strong>，从客户、建筑、服务、计划、工单到报告字段，都能贴合团队已有的检测交付方式。
        </p>
      </article>

      <article class="benefit-card integration-card">
        <h3>连接现场与管理端</h3>
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
        <p><strong>无缝协作</strong>，把现场采集、消息通知、报告归档与后台调度接在一起，减少口头转述和重复录入。</p>
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
