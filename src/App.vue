<script setup>
import { onBeforeUnmount, onMounted } from "vue"
import BenefitSection from "./components/BenefitSection.vue"
import DashboardMockup from "./components/DashboardMockup.vue"
import DeviceSection from "./components/DeviceSection.vue"
import FeatureSection from "./components/FeatureSection.vue"
import SiteFooter from "./components/SiteFooter.vue"
import SiteHeader from "./components/SiteHeader.vue"

const logos = ["MetroWorks", "UrbanSafe", "Northline", "Stonefield", "CityOps", "CoreBuild"]
const marqueeLogos = [...logos, ...logos]

const workOrderChips = ["任务派发", "现场照片", "整改闭环", "进度报表"]
const reportChips = ["风险分级", "报告归档", "客户查看", "数据追溯"]

let observer

function updateHeroProgress() {
  const progress = Math.min(window.scrollY / 520, 1)
  document.documentElement.style.setProperty("--hero-scroll", progress.toFixed(3))
}

onMounted(() => {
  updateHeroProgress()
  window.addEventListener("scroll", updateHeroProgress, { passive: true })

  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("is-visible")
          observer.unobserve(entry.target)
        }
      })
    },
    { rootMargin: "0px 0px -12% 0px", threshold: 0.16 },
  )

  document.querySelectorAll(".reveal-on-scroll").forEach((el) => observer.observe(el))
})

onBeforeUnmount(() => {
  window.removeEventListener("scroll", updateHeroProgress)
  observer?.disconnect()
})
</script>

<template>
  <SiteHeader />

  <main id="top">
    <section class="hero">
      <div class="cloud-layer" aria-hidden="true">
        <img class="cloud cloud-left" src="./assets/cloud-right.avif" alt="" />
        <img class="cloud cloud-right" src="./assets/cloud-left.avif" alt="" />
      </div>
      <div class="hero-copy">
        <p class="eyebrow hero-enter enter-1">建筑安全检测与运维管理平台</p>
        <h1 class="hero-enter enter-2">让建筑安全检测像专业团队一样运转</h1>
        <p class="hero-lead hero-enter enter-3">
          宝京云维将检测服务、巡检工单、现场记录、风险分级和报告管理放在同一套流程里，
          帮助团队减少沟通成本，稳定交付每一次建筑安全检测。
        </p>
        <div class="hero-actions hero-enter enter-4">
          <a class="button primary" href="#contact">开始了解</a>
          <a class="button secondary" href="#features">查看功能</a>
        </div>
      </div>

      <div class="hero-dashboard-stage">
        <DashboardMockup />
      </div>
    </section>

    <section class="logo-strip" aria-label="服务对象">
      <p>适用于物业集团、园区运营、检测机构与城市更新项目</p>
      <div class="logo-marquee-window">
        <div class="logo-marquee">
          <span v-for="(logo, index) in marqueeLogos" :key="`${logo}-${index}`">{{ logo }}</span>
        </div>
      </div>
    </section>

    <DeviceSection />

    <FeatureSection
      id="features"
      eyebrow="检测工单"
      title="让每个检测任务持续向前"
      cta="预约演示"
      href="#contact"
      visual="work-order"
      :chips="workOrderChips"
    >
      从服务配置、计划排期到现场执行，宝京云维用清晰的工单流承接每个环节。
      负责人、截止时间、风险等级和处理状态都能被及时看见。
    </FeatureSection>

    <FeatureSection
      eyebrow="报告与风险"
      title="沉淀现场数据，快速生成检测报告"
      cta="了解报告能力"
      href="#contact"
      visual="report"
      reverse
      :chips="reportChips"
    >
      检测记录、图片、问题描述和整改建议统一归档，减少手工整理。
      客户可以查看评估结果、风险项和后续整改状态。
    </FeatureSection>

    <BenefitSection />
  </main>

  <SiteFooter />
</template>
