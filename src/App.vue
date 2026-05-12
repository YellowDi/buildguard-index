<script setup>
import { onBeforeUnmount, onMounted } from "vue"
import SiteFooter from "./components/SiteFooter.vue"
import SiteHeader from "./components/SiteHeader.vue"
import appRiskUrl from "../建筑物详情「存在风险」@2x.png"
import appHomeUrl from "../首页「正常」@2x.png"
import phoneHandUrl from "./assets/phone-hand.png"
import phoneShapeUrl from "./assets/phone-shape.svg"

const heroAvatars = ["管", "业", "维"]

const stats = [
  { value: "36k+", label: "报告在线查看" },
  { value: "17k+", label: "风险跟进记录" },
  { value: "2k+", label: "项目客户使用" },
]

const analyticsItems = [
  {
    title: "风险详情",
    text: "风险等级、问题位置、现场照片和整改建议集中呈现。",
  },
  {
    title: "历史评估",
    text: "每次检测记录长期归档，复查时可以快速对照。",
  },
]

const featureCards = [
  {
    title: "建筑安全首页",
    text: "建筑切换、健康评分、健康状态和风险摘要集中在首页展示。",
    tone: "blue",
  },
  {
    title: "风险问题穿透",
    text: "从异常分类进入具体问题点，查看扣分原因、位置描述和现场照片。",
    tone: "red",
  },
  {
    title: "整改建议明确",
    text: "高危问题优先标记，并给出整改措施、建议时限和专家/AI 综合建议。",
    tone: "green",
  },
  {
    title: "历史与服务留存",
    text: "历史评估、下次检测提醒、报修入口和资产套餐信息统一留存。",
    tone: "violet",
  },
]

const steps = [
  {
    title: "选择建筑",
    text: "客户进入 App 后切换名下园区或建筑，查看对应的最新安全状态。",
  },
  {
    title: "查看风险",
    text: "从评分、异常分类和风险摘要进入问题详情，核对照片、标准和位置。",
  },
  {
    title: "跟进整改",
    text: "根据建议时限和处理状态持续跟进，并长期保留评估记录。",
  },
]

const reasons = [
  {
    title: "客户视角清晰",
    text: "把专业检测结论转成客户能快速理解的评分、风险说明和整改重点。",
  },
  {
    title: "风险状态清楚",
    text: "报告、风险项和整改结果更新后，客户 App 端展示最新状态。",
  },
  {
    title: "一键查看报告",
    text: "核心结论、图片证据和后续建议集中呈现，减少反复沟通。",
  },
  {
    title: "长期服务档案",
    text: "每一次检测和整改都会进入项目档案，方便后续复查。",
  },
]

const storyCards = [
  {
    label: "风险提醒",
    title: "发现高风险问题时，客户看得明白",
    text: "App 会把风险等级、问题位置、现场照片和建议动作放在同一张卡片里，客户可以直接判断处理优先级。",
  },
  {
    label: "报告交付",
    title: "报告完成后，客户可直接查看与留存",
    text: "检测报告、整改建议和历史记录自动归档，适合物业、业委会和资产方长期追踪建筑状态。",
  },
]

const testimonials = [
  {
    quote: "过去业主总要在群里追问报告进度，现在他们打开 App 就能看到检测状态和预计交付时间。",
    name: "陈经理",
    role: "物业项目负责人",
  },
  {
    quote: "风险项展示比 PDF 更直观，照片、位置、整改建议都在一起，客户沟通效率明显提高。",
    name: "周工",
    role: "项目服务顾问",
  },
  {
    quote: "我们最看重历史档案。后续复查时，客户能快速回看上次问题和整改结果。",
    name: "林女士",
    role: "资产管理方",
  },
]

const clientLogos = ["物业集团", "园区客户", "业委会", "商业楼宇", "资产管理", "城市更新", "企业客户"]
const clientTicker = [...clientLogos, ...clientLogos]

const faqs = [
  {
    q: "客户 App 能查看哪些建筑信息？",
    a: "可以查看名下园区或建筑的健康评分、健康状态、风险摘要、历史评估和服务信息。",
  },
  {
    q: "风险点能看到现场照片吗？",
    a: "可以。风险详情会展示问题位置、现场照片或视频、判定标准和整改建议，便于客户核对。",
  },
  {
    q: "历史检测报告会保留吗？",
    a: "会。历史评估记录会按建筑归档，客户可以回看评分变化、风险项和整改结果。",
  },
  {
    q: "客户可以发起报修吗？",
    a: "可以。客户可在 App 内提交报修内容、位置描述和现场照片，并查看后续处理状态。",
  },
]

let observer

function updateHeroProgress() {
  const progress = Math.min(window.scrollY / 620, 1)
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
    { rootMargin: "0px 0px -12% 0px", threshold: 0.14 },
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
    <section class="hero-section" aria-labelledby="hero-title">
      <div class="hero-grid" aria-hidden="true"></div>
      <div class="hero-container hero-enter enter-1">
        <div class="hero-title-block">
          <h1 id="hero-title">
            <span>建筑安全</span>
            <span>随时掌握</span>
          </h1>
        </div>

        <div class="hero-lower">
          <div class="hero-proof hero-enter enter-2">
            <p>宝京云维将安全评分、风险点、现场照片、整改建议和历史报告集中到客户 App。</p>
            <div class="avatar-row" aria-label="客户使用者">
              <span v-for="avatar in heroAvatars" :key="avatar">{{ avatar }}</span>
            </div>
            <strong>项目客户持续使用</strong>
            <small>服务业主、物业和资产管理场景</small>
          </div>

          <div class="hero-phone-stage hero-enter enter-3" aria-label="客户 App 手持截图展示">
            <div class="hero-hand-mock">
              <img class="phone-hand" :src="phoneHandUrl" alt="" aria-hidden="true" />
              <div class="hero-mock-phone">
                <img
                  class="mock-phone-screen"
                  :src="appHomeUrl"
                  alt="宝京云维客户 App 首页巡检报告界面"
                />
                <img class="mock-phone-shape" :src="phoneShapeUrl" alt="" aria-hidden="true" />
              </div>
              <span class="hero-badge badge-new"><span>New!</span></span>
              <span class="hero-badge badge-left">真实 App 截图</span>
              <span class="hero-badge badge-right">风险清晰呈现</span>
            </div>
          </div>

          <div class="hero-actions hero-enter enter-4">
            <p>帮助业主、物业和资产方清晰了解建筑安全状态。</p>
            <div>
              <a class="store-button" href="#cta" aria-label="获取 iOS 客户 App">
                <span>●</span>
                <strong>iOS 客户端</strong>
              </a>
              <a class="store-button android" href="#cta" aria-label="获取 Android 客户 App">
                <span>◆</span>
                <strong>Android</strong>
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="stats-section" aria-label="客户 App 使用数据">
      <div class="stats-intro reveal-on-scroll">
        <h2>让建筑安全状态清晰可见</h2>
        <p>从评估结论到整改建议，客户 App 把专业检测服务变成清晰、可信、可追踪的体验。</p>
      </div>
      <div class="stats-grid reveal-on-scroll">
        <article v-for="stat in stats" :key="stat.label">
          <strong>{{ stat.value }}</strong>
          <span>{{ stat.label }}</span>
        </article>
      </div>
    </section>

    <section id="features" class="analytics-section section-shell reveal-on-scroll">
      <div class="analytics-visual">
        <div class="soft-cloud" aria-hidden="true"></div>
        <figure class="app-shot analytics-shot">
          <img :src="appRiskUrl" alt="宝京云维客户 App 风险详情页" />
        </figure>
      </div>
      <div class="analytics-copy">
        <h2>关键风险，让客户放心跟进</h2>
        <p>客户随时查看安全评分、风险数量、问题位置、现场照片和整改建议，不再依赖零散沟通。</p>
        <div class="analytics-items">
          <article v-for="item in analyticsItems" :key="item.title">
            <span></span>
            <strong>{{ item.title }}</strong>
            <p>{{ item.text }}</p>
          </article>
        </div>
        <a class="button muted-button" href="#app-features">查看 App 功能</a>
      </div>
    </section>

    <section id="app-features" class="feature-section section-shell">
      <div class="section-heading reveal-on-scroll">
        <a class="text-link" href="#cta">查看客户 App</a>
        <h2>客户 App 的核心功能</h2>
        <p>围绕客户最关心的建筑状态、风险证据、整改建议和历史服务记录组织信息。</p>
      </div>
      <div class="feature-card-grid">
        <article
          v-for="(feature, index) in featureCards"
          :key="feature.title"
          class="feature-card reveal-on-scroll"
          :class="`tone-${feature.tone}`"
          :style="{ '--delay': `${index * 90}ms` }"
        >
          <div class="feature-shape" aria-hidden="true"></div>
          <div class="feature-screen">
            <span></span><span></span><span></span>
          </div>
          <h3>{{ feature.title }}</h3>
          <p>{{ feature.text }}</p>
        </article>
      </div>
    </section>

    <section id="workflow" class="steps-section section-shell reveal-on-scroll">
      <div class="section-heading center">
        <span class="pill-label">使用路径</span>
        <h2>三步看清建筑安全状态</h2>
        <p>客户打开 App 后，即可从建筑概览进入风险详情，再持续跟进整改结果。</p>
      </div>
      <div class="steps-grid">
        <article v-for="(step, index) in steps" :key="step.title">
          <span>{{ String(index + 1).padStart(2, "0") }}</span>
          <h3>{{ step.title }}</h3>
          <p>{{ step.text }}</p>
        </article>
      </div>
    </section>

    <section class="why-section section-shell reveal-on-scroll">
      <div class="section-heading center">
        <h2>为什么客户会愿意打开宝京云维？</h2>
      </div>
      <div class="why-layout">
        <div class="why-column">
          <article v-for="reason in reasons.slice(0, 2)" :key="reason.title">
            <span></span>
            <h3>{{ reason.title }}</h3>
            <p>{{ reason.text }}</p>
          </article>
        </div>
        <figure class="app-shot why-shot">
          <img :src="appHomeUrl" alt="宝京云维客户 App 项目首页" />
        </figure>
        <div class="why-column">
          <article v-for="reason in reasons.slice(2)" :key="reason.title">
            <span></span>
            <h3>{{ reason.title }}</h3>
            <p>{{ reason.text }}</p>
          </article>
        </div>
      </div>
    </section>

    <section class="story-section section-shell">
      <article
        v-for="(story, index) in storyCards"
        :key="story.title"
        class="story-card reveal-on-scroll"
        :class="{ reverse: index % 2 === 1 }"
      >
        <div class="story-visual">
          <figure class="app-shot story-shot">
            <img
              :src="index === 0 ? appRiskUrl : appHomeUrl"
              :alt="index === 0 ? '宝京云维客户 App 风险提醒界面' : '宝京云维客户 App 报告归档界面'"
            />
          </figure>
        </div>
        <div class="story-copy">
          <span class="pill-label">{{ story.label }}</span>
          <h2>{{ story.title }}</h2>
          <p>{{ story.text }}</p>
          <a class="text-link" href="#cta">了解客户 App</a>
        </div>
      </article>
    </section>

    <section id="testimonials" class="testimonial-section section-shell reveal-on-scroll">
      <div class="section-heading center">
        <h2>真实客户，真实反馈</h2>
      </div>
      <div class="testimonial-track">
        <article v-for="item in testimonials" :key="item.name">
          <p>“{{ item.quote }}”</p>
          <div>
            <span>{{ item.name.slice(0, 1) }}</span>
            <strong>{{ item.name }}</strong>
            <small>{{ item.role }}</small>
          </div>
        </article>
      </div>
    </section>

    <section class="client-strip reveal-on-scroll" aria-label="适用客户">
      <p>适用于多类建筑安全服务客户</p>
      <div class="client-window">
        <div class="client-track">
          <span v-for="(client, index) in clientTicker" :key="`${client}-${index}`">
            {{ client }}
          </span>
        </div>
      </div>
    </section>

    <section id="faq" class="faq-section section-shell reveal-on-scroll">
      <div class="faq-aside">
        <h2>Questions<br />and answers</h2>
        <p>客户 App 的建筑信息、风险证据、历史报告和报修方式。</p>
        <a class="button primary" href="#cta">联系我们</a>
      </div>
      <div class="faq-list">
        <details v-for="(faq, index) in faqs" :key="faq.q" :open="index === 0">
          <summary>{{ faq.q }}</summary>
          <p>{{ faq.a }}</p>
        </details>
      </div>
    </section>
  </main>

  <SiteFooter />
</template>
