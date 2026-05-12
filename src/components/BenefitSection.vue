<script setup>
const integrationItems = ["巡检", "定位", "照片", "企微", "短信", "报告", "权限", "导出", "审计", "归档"]

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
        <div class="customization-visual" aria-hidden="true">
          <div class="custom-window">
            <div class="custom-sidebar">
              <span></span>
              <span></span>
              <span></span>
              <span></span>
            </div>
            <div class="custom-main">
              <div class="custom-topbar"></div>
              <div class="custom-preview-grid">
                <span></span>
                <span></span>
                <span></span>
                <span></span>
              </div>
              <div class="custom-table">
                <i></i>
                <i></i>
                <i></i>
              </div>
            </div>
            <div class="custom-settings">
              <b></b>
              <span></span>
              <span></span>
              <span></span>
            </div>
          </div>
        </div>
        <p>
          客户、建筑、服务、计划、工单和报告彼此关联，团队不需要在多个表格之间来回切换。
        </p>
      </article>

      <article class="benefit-card integration-card">
        <h3>连接现场与管理端</h3>
        <div class="integration-marquee" aria-hidden="true">
          <div class="integration-track">
            <span v-for="(item, index) in integrationItems" :key="`${item}-${index}`">{{ item }}</span>
            <span v-for="(item, index) in integrationItems" :key="`${item}-copy-${index}`">{{ item }}</span>
          </div>
        </div>
        <p>现场采集和后台调度保持同步，减少口头转述和重复录入。</p>
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
