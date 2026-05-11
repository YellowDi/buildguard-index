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
  <section :id="id" class="split-section section-pad" :class="{ reverse }">
    <div v-if="visual === 'work-order'" class="feature-visual work-order-visual">
      <div class="panel-card floating one">
        <span>风险项</span>
        <strong>外墙空鼓</strong>
        <em>需 48h 内复核</em>
      </div>
      <div class="kanban">
        <div><b>待派发</b><span></span><span></span></div>
        <div><b>处理中</b><span></span><span></span><span></span></div>
        <div><b>待验收</b><span></span><span></span></div>
      </div>
    </div>

    <div v-else class="feature-visual report-visual">
      <div class="report-card">
        <span>安全评分</span>
        <strong>86</strong>
        <small>较上次 +12</small>
      </div>
      <div class="report-lines">
        <span></span><span></span><span></span><span></span>
      </div>
      <div class="risk-donut">
        <b>24</b>
        <em>风险项</em>
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
