<script setup>
import { computed, onBeforeUnmount, onMounted, ref } from "vue"

const slides = [
  {
    key: "mobile",
    label: "安全首页",
    title: "建筑概览",
    description: "客户在首页查看建筑评分、健康状态、风险摘要和下次检测提醒。",
  },
  {
    key: "web",
    label: "风险详情",
    title: "问题穿透",
    description: "客户进入风险详情，核对问题位置、现场照片、判定标准和整改建议。",
  },
]

const activeIndex = ref(0)
const switcherRef = ref(null)
let timer

const activeSlide = computed(() => slides[activeIndex.value])

function updateDeviceProgress() {
  if (!switcherRef.value) return

  const rect = switcherRef.value.getBoundingClientRect()
  const viewportHeight = window.innerHeight || 1
  const rawProgress = (viewportHeight - rect.top) / (viewportHeight + rect.height)
  const progress = Math.min(Math.max(rawProgress, 0), 1)

  switcherRef.value.style.setProperty("--device-scroll", progress.toFixed(3))
}

function setActive(index) {
  activeIndex.value = index
  restartTimer()
}

function nextSlide() {
  activeIndex.value = (activeIndex.value + 1) % slides.length
}

function restartTimer() {
  window.clearInterval(timer)
  timer = window.setInterval(nextSlide, 4200)
}

onMounted(() => {
  restartTimer()
  updateDeviceProgress()
  window.addEventListener("scroll", updateDeviceProgress, { passive: true })
  window.addEventListener("resize", updateDeviceProgress)
})

onBeforeUnmount(() => {
  window.clearInterval(timer)
  window.removeEventListener("scroll", updateDeviceProgress)
  window.removeEventListener("resize", updateDeviceProgress)
})
</script>

<template>
  <section id="workflow" class="device-section section-pad reveal-on-scroll">
    <div class="section-heading">
      <p class="eyebrow">客户 App</p>
      <h2>建筑概览与风险详情清晰呈现</h2>
    </div>

    <div ref="switcherRef" class="device-switcher" :class="`is-${activeSlide.key}`">
      <div
        v-for="slide in slides"
        :key="slide.key"
        class="device-slide"
        :class="[`device-slide-${slide.key}`, { active: activeSlide.key === slide.key }]"
        :aria-hidden="activeSlide.key !== slide.key"
      >
        <div v-if="slide.key === 'mobile'" class="device-photo mobile-photo">
          <div class="desk-shape desk-pad"></div>
          <div class="desk-shape desk-book"></div>
          <div class="hand-shape"></div>
          <div class="phone-screen">
            <div class="phone-notch"></div>
            <strong>安全评估</strong>
            <span>南区 A 座 · 16 项风险记录</span>
            <div class="phone-actions">
              <b>结构</b>
              <b>消防</b>
              <b>机房</b>
            </div>
            <div class="phone-task done"></div>
            <div class="phone-task"></div>
            <div class="phone-nav"></div>
          </div>
        </div>

        <div v-else class="device-photo web-photo">
          <div class="laptop-screen">
            <div class="laptop-sidebar">
              <span></span><span></span><span></span><span></span>
            </div>
            <div class="laptop-main">
              <div class="laptop-top"></div>
              <div class="laptop-metrics">
                <span></span><span></span><span></span>
              </div>
              <div class="laptop-chart">
                <i style="--h: 46%"></i>
                <i style="--h: 72%"></i>
                <i style="--h: 38%"></i>
                <i style="--h: 61%"></i>
                <i style="--h: 54%"></i>
                <i style="--h: 82%"></i>
              </div>
            </div>
          </div>
          <div class="laptop-base"></div>
        </div>
      </div>

      <div class="device-tabs" role="tablist" aria-label="客户 App 展示切换">
        <button
          v-for="(slide, index) in slides"
          :key="slide.key"
          type="button"
          role="tab"
          :aria-selected="activeSlide.key === slide.key"
          :class="{ active: activeSlide.key === slide.key }"
          @click="setActive(index)"
        >
          {{ slide.label }}
        </button>
      </div>
    </div>
  </section>
</template>
