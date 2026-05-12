<script setup>
defineProps({
  id: {
    type: String,
    default: undefined,
  },
  eyebrow: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  cta: {
    type: String,
    required: true,
  },
  href: {
    type: String,
    default: "#contact",
  },
  visual: {
    type: String,
    required: true,
  },
  reverse: {
    type: Boolean,
    default: false,
  },
  chips: {
    type: Array,
    default: () => [],
  },
})
</script>

<template>
  <section :id="id" class="split-section section-pad reveal-on-scroll" :class="{ reverse }">
    <div v-if="visual === 'work-order'" class="feature-visual work-order-visual">
      <div class="feature-product-card project-product-card">
        <h3>检测工单</h3>
        <div class="project-toolbar">
          <span>搜索建筑或工单...</span>
          <b>筛选</b>
        </div>
        <div class="project-group-head">
          <strong>进行中</strong>
          <em>5</em>
        </div>
        <div class="project-table-head">
          <span>项目</span>
          <span>风险</span>
          <span>客户</span>
          <span>负责人</span>
        </div>
        <div class="project-row high">
          <span>幕墙安全复核</span><b>高</b><i></i><em></em>
        </div>
        <div class="project-row mid">
          <span>消防通道巡检</span><b>中</b><i></i><em></em>
        </div>
        <div class="project-row low">
          <span>地下车库排水</span><b>轻微</b><i></i><em></em>
        </div>
        <div class="project-group-foot">
          <strong>待验收</strong>
          <em>8</em>
        </div>
      </div>
    </div>

    <div v-else class="feature-visual report-visual">
      <div class="feature-product-card budget-product-card">
        <h3>检测报告</h3>
        <div class="budget-grid">
          <article>
            <span>安全评分</span>
            <strong>86</strong>
          </article>
          <article>
            <span>风险项</span>
            <strong>24</strong>
          </article>
          <article>
            <span>已整改</span>
            <strong>18</strong>
          </article>
          <article>
            <span>完成率</span>
            <strong>89.3%</strong>
          </article>
        </div>
        <div class="analytics-head">
          <strong>风险趋势</strong>
          <span>评估</span>
          <span>整改</span>
        </div>
        <div class="analytics-chart">
          <i></i>
          <svg viewBox="0 0 440 170" aria-hidden="true">
            <path class="chart-line solid" d="M0 145 C70 142 96 134 126 112 S205 110 230 92 268 72 292 57 356 44 440 32" />
            <path class="chart-line dashed" d="M235 98 C270 78 296 76 330 76 S386 45 440 45" />
          </svg>
        </div>
      </div>
    </div>

    <div class="split-copy">
      <p class="eyebrow">{{ eyebrow }}</p>
      <h2>{{ title }}</h2>
      <p><slot /></p>
      <a class="button primary compact" :href="href">{{ cta }}</a>
      <div class="chip-row">
        <span v-for="chip in chips" :key="chip">{{ chip }}</span>
      </div>
    </div>
  </section>
</template>
