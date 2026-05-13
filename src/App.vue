<script setup>
import { onBeforeUnmount, onMounted, ref } from "vue"
import SiteFooter from "./components/SiteFooter.vue"
import SiteHeader from "./components/SiteHeader.vue"
import appRiskUrl from "./assets/screenshot-building-detail-risk@2x.png"
import appHomeUrl from "./assets/screenshot-home-normal@2x.png"
import phoneHandFingersUrl from "./assets/phone-hand-2-fingers.png"
import phoneHandUrl from "./assets/phone-hand-2.png"
import phoneShapeUrl from "./assets/phone-shape.svg"
import upwizeCloudUrl from "./assets/upwize-cloud.svg"
import upwizeIconInsightsUrl from "./assets/upwize-icon-insights.svg"
import upwizeIconTrendsUrl from "./assets/upwize-icon-trends.svg"
import upwizePhoneShapeUrl from "./assets/upwize-phone-shape.png"
import upwizeShapeUrl from "./assets/upwize-shape.svg"
import upwizeWhyGridUrl from "./assets/upwize-why-grid.svg"
import avatarJamesUrl from "./assets/upwize-avatar-james.png"
import avatarMichaelUrl from "./assets/upwize-avatar-michael.png"
import avatarTopUrl from "./assets/upwize-avatar-top.png"

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
    visual: "overview",
  },
  {
    title: "风险问题穿透",
    text: "从异常分类进入具体问题点，查看扣分原因、位置描述和现场照片。",
    visual: "risk",
  },
  {
    title: "整改建议明确",
    text: "高危问题优先标记，并给出整改措施、建议时限和专家/AI 综合建议。",
    visual: "advice",
  },
  {
    title: "历史与服务留存",
    text: "历史评估、下次检测提醒、报修入口和资产套餐信息统一留存。",
    visual: "history",
  },
]

const steps = [
  {
    title: "选择建筑",
    text: "客户进入 App 后切换名下园区或建筑，查看对应的最新安全状态。",
    icon: "ri-building-2-line",
    tone: "deep-blue",
  },
  {
    title: "查看风险",
    text: "从评分、异常分类和风险摘要进入问题详情，核对照片、标准和位置。",
    icon: "ri-radar-line",
    tone: "red",
  },
  {
    title: "跟进整改",
    text: "根据建议时限和处理状态持续跟进，并长期保留评估记录。",
    icon: "ri-shield-check-line",
    tone: "blue",
  },
]

const reasons = [
  {
    title: "客户视角清晰",
    text: "把专业检测结论转成客户能快速理解的评分、风险说明和整改重点。",
    icon: "ri-fingerprint-line",
    tone: "blue",
  },
  {
    title: "风险状态清楚",
    text: "报告、风险项和整改结果更新后，客户 App 端展示最新状态。",
    icon: "ri-equalizer-line",
    tone: "red",
  },
  {
    title: "一键查看报告",
    text: "核心结论、图片证据和后续建议集中呈现，减少反复沟通。",
    icon: "ri-file-search-line",
    tone: "orange",
  },
  {
    title: "长期服务档案",
    text: "每一次检测和整改都会进入项目档案，方便后续复查。",
    icon: "ri-archive-stack-line",
    tone: "deep-blue",
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

const testimonialItems = [
  {
    quote: "风险项展示比 PDF 更直观，照片、位置、整改建议都在一起，客户沟通效率明显提高。",
    name: "Michael Bennett",
    role: "App Designer",
    avatar: avatarMichaelUrl,
  },
  {
    quote: "使用宝京云维的数据分析后，我们更清楚项目风险趋势，也更有把握推动整改决策。",
    name: "Top Clofen",
    role: "product Designer",
    avatar: avatarTopUrl,
  },
  {
    quote: "过去业主总要在群里追问报告进度，现在他们打开 App 就能看到检测状态和预计交付时间。",
    name: "James Thompson",
    role: "product Designer",
    avatar: avatarJamesUrl,
  },
]

const testimonials = [...testimonialItems, ...testimonialItems, ...testimonialItems]
const testimonialBaseCount = testimonialItems.length

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
let testimonialTimer
const testimonialTrack = ref(null)

function updateHeroProgress() {
  const progress = Math.min(window.scrollY / 620, 1)
  document.documentElement.style.setProperty("--hero-scroll", progress.toFixed(3))
}

function getTestimonialStep() {
  const track = testimonialTrack.value
  if (!track) return 0

  const card = track.querySelector(".testimonial-card")
  const gap = Number.parseFloat(window.getComputedStyle(track).columnGap) || 0
  return card ? card.getBoundingClientRect().width + gap : track.clientWidth * 0.82
}

function normalizeTestimonialPosition() {
  const track = testimonialTrack.value
  const step = getTestimonialStep()
  if (!track || !step) return

  const loopWidth = step * testimonialBaseCount
  const minLeft = loopWidth * 0.5
  const maxLeft = loopWidth * 1.5

  if (track.scrollLeft < minLeft) {
    track.scrollLeft += loopWidth
  }

  if (track.scrollLeft > maxLeft) {
    track.scrollLeft -= loopWidth
  }
}

function resetTestimonialPosition() {
  const track = testimonialTrack.value
  const step = getTestimonialStep()
  if (!track || !step) return

  track.scrollLeft = step * testimonialBaseCount
}

function scrollTestimonials(direction) {
  const track = testimonialTrack.value
  const distance = getTestimonialStep()
  if (!track || !distance) return

  normalizeTestimonialPosition()

  track.scrollBy({
    left: distance * direction,
    behavior: "smooth",
  })

  window.setTimeout(normalizeTestimonialPosition, 520)
}

function startTestimonialAutoplay() {
  window.clearInterval(testimonialTimer)
  testimonialTimer = window.setInterval(() => {
    scrollTestimonials(1)
  }, 3200)
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
  window.requestAnimationFrame(resetTestimonialPosition)
  startTestimonialAutoplay()
})

onBeforeUnmount(() => {
  window.removeEventListener("scroll", updateHeroProgress)
  window.clearInterval(testimonialTimer)
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
              <img class="phone-hand-fingers" :src="phoneHandFingersUrl" alt="" aria-hidden="true" />
              <span class="hero-badge badge-new"><span>New!</span></span>
              <span class="hero-badge badge-left">真实 App 截图</span>
              <span class="hero-badge badge-right">风险清晰呈现</span>
            </div>
          </div>

          <div class="hero-actions hero-enter enter-4">
            <p>帮助业主、物业和资产方清晰了解建筑安全状态。</p>
            <div>
              <a class="store-button" href="#cta" aria-label="获取 iOS 客户 App">
                <i class="ri-apple-fill store-button__icon" aria-hidden="true"></i>
                <strong>iOS 客户端</strong>
              </a>
              <a class="store-button android" href="#cta" aria-label="获取 Android 客户 App">
                <i class="ri-android-fill store-button__icon" aria-hidden="true"></i>
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
        <img class="analytics-cloud" :src="upwizeCloudUrl" alt="" aria-hidden="true" />
        <img class="analytics-shape" :src="upwizeShapeUrl" alt="" aria-hidden="true" />
        <figure class="analytics-shot">
          <img class="analytics-screen" :src="appRiskUrl" alt="宝京云维客户 App 风险详情页" />
          <img class="analytics-phone-shape" :src="upwizePhoneShapeUrl" alt="" aria-hidden="true" />
        </figure>
      </div>
      <div class="analytics-copy">
        <h2>关键风险，让客户<br />放心跟进</h2>
        <p>客户随时查看安全评分、风险数量、问题位置、现场照片和整改建议，不再依赖零散沟通。</p>
        <div class="analytics-items">
          <article v-for="(item, index) in analyticsItems" :key="item.title">
            <span>
              <b>
                <img :src="index === 0 ? upwizeIconTrendsUrl : upwizeIconInsightsUrl" alt="" aria-hidden="true" />
              </b>
            </span>
            <strong>{{ item.title }}</strong>
            <p>{{ item.text }}</p>
          </article>
        </div>
        <a class="button muted-button" href="#app-features">查看 App 功能</a>
      </div>
    </section>

    <section id="app-features" class="feature-section section-shell">
      <div class="section-heading reveal-on-scroll">
        <h2>核心功能</h2>
        <p>围绕客户最关心的建筑状态、风险证据、整改建议和历史服务记录组织信息。</p>
      </div>
      <div class="feature-card-grid" aria-label="客户 App 核心功能列表">
        <div class="feature-row feature-row-top">
          <article
            v-for="(feature, index) in featureCards.slice(0, 2)"
            :key="feature.title"
            class="feature-card reveal-on-scroll"
            :class="[`feature-card-${index + 1}`, `visual-${feature.visual}`]"
            :style="{ '--delay': `${index * 90}ms` }"
          >
            <div class="feature-title-wrapper">
              <h3>{{ feature.title }}</h3>
              <p>{{ feature.text }}</p>
            </div>
            <div class="feature-card-image-wrapper" aria-hidden="true"></div>
          </article>
        </div>
        <div class="feature-row feature-row-bottom">
          <article
            v-for="(feature, index) in featureCards.slice(2)"
            :key="feature.title"
            class="feature-card reveal-on-scroll"
            :class="[`feature-card-${index + 3}`, `visual-${feature.visual}`]"
            :style="{ '--delay': `${(index + 2) * 90}ms` }"
          >
            <div class="feature-title-wrapper">
              <h3>{{ feature.title }}</h3>
              <p>{{ feature.text }}</p>
            </div>
            <div class="feature-card-image-wrapper" aria-hidden="true"></div>
          </article>
        </div>
      </div>
    </section>

    <section id="workflow" class="steps-section section-shell reveal-on-scroll">
      <div class="section-heading center">
        <span class="pill-label">使用路径</span>
        <h2>三步看清建筑安全状态</h2>
        <p>客户打开 App 后，即可从建筑概览进入风险详情，再持续跟进整改结果。</p>
      </div>
      <div class="steps-grid">
        <article v-for="step in steps" :key="step.title">
          <span class="step-icon" :class="`tone-${step.tone}`">
            <i :class="step.icon" aria-hidden="true"></i>
          </span>
          <h3>{{ step.title }}</h3>
          <p>{{ step.text }}</p>
        </article>
      </div>
    </section>

    <section class="why-section section-shell reveal-on-scroll">
      <div class="why-panel">
        <img class="why-grid-bg" :src="upwizeWhyGridUrl" alt="" aria-hidden="true" />
        <h2>为什么客户会愿意打开宝京云维？</h2>
        <div class="why-layout">
          <div class="why-column">
            <article v-for="reason in reasons.slice(0, 2)" :key="reason.title">
              <span class="why-icon" :class="`tone-${reason.tone}`">
                <i :class="reason.icon" aria-hidden="true"></i>
              </span>
              <h3>{{ reason.title }}</h3>
              <p>{{ reason.text }}</p>
            </article>
          </div>
          <figure class="why-device" aria-label="宝京云维客户 App 项目首页">
            <img class="why-device-screen" :src="appHomeUrl" alt="宝京云维客户 App 项目首页" />
            <img class="why-device-shape" :src="upwizePhoneShapeUrl" alt="" aria-hidden="true" />
          </figure>
          <div class="why-column">
            <article v-for="reason in reasons.slice(2)" :key="reason.title">
              <span class="why-icon" :class="`tone-${reason.tone}`">
                <i :class="reason.icon" aria-hidden="true"></i>
              </span>
              <h3>{{ reason.title }}</h3>
              <p>{{ reason.text }}</p>
            </article>
          </div>
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
        <div class="story-visual" :class="index === 0 ? 'risk-story-visual' : 'report-story-visual'">
          <template v-if="index === 0">
            <span class="story-chip story-chip-blue">高风险问题</span>
            <span class="story-chip story-chip-red">优先处理</span>
            <figure class="story-device story-device-primary">
              <img :src="appRiskUrl" alt="宝京云维客户 App 风险提醒界面" />
            </figure>
            <article class="story-floating-card risk-alert-card">
              <span>风险等级</span>
              <strong>高风险</strong>
              <small>幕墙连接件松动，建议 24 小时内安排复核。</small>
            </article>
            <article class="story-floating-card risk-photo-card">
              <b></b>
              <div>
                <strong>现场照片</strong>
                <small>3 张证据已同步</small>
              </div>
            </article>
          </template>

          <template v-else>
            <span class="story-chip story-chip-blue">在线报告</span>
            <span class="story-chip story-chip-orange">长期留存</span>
            <article class="story-report-card">
              <div class="story-report-head">
                <span>检测报告</span>
                <strong>已完成</strong>
              </div>
              <div class="story-report-metrics">
                <b>86</b>
                <span>安全评分</span>
              </div>
              <div class="story-report-lines">
                <i></i>
                <i></i>
                <i></i>
              </div>
            </article>
            <figure class="story-device story-device-secondary">
              <img :src="appHomeUrl" alt="宝京云维客户 App 报告归档界面" />
            </figure>
            <article class="story-floating-card archive-card">
              <strong>历史记录</strong>
              <small>报告、照片、整改建议自动归档</small>
            </article>
          </template>
        </div>
        <div class="story-copy">
          <span class="pill-label">{{ story.label }}</span>
          <h2>{{ story.title }}</h2>
          <p>{{ story.text }}</p>
        </div>
      </article>
    </section>

    <section id="testimonials" class="testimonial-section reveal-on-scroll" aria-labelledby="testimonial-title">
      <div class="testimonial-inner">
        <div class="testimonial-heading">
          <h2 id="testimonial-title">真实客户，真实反馈</h2>
          <div class="testimonial-controls" aria-label="客户反馈切换">
            <button type="button" aria-label="上一组反馈" @click="scrollTestimonials(-1)">
              <i class="ri-arrow-left-line" aria-hidden="true"></i>
            </button>
            <button type="button" aria-label="下一组反馈" @click="scrollTestimonials(1)">
              <i class="ri-arrow-right-line" aria-hidden="true"></i>
            </button>
          </div>
        </div>
        <div class="testimonial-window">
          <div ref="testimonialTrack" class="testimonial-track" tabindex="0" aria-label="客户反馈列表">
            <article
              v-for="(item, index) in testimonials"
              :key="`${item.name}-${index}`"
              class="testimonial-card"
            >
              <p>“{{ item.quote }}”</p>
              <footer>
                <img :src="item.avatar" :alt="`${item.name} 头像`" />
                <div>
                  <strong>{{ item.name }}</strong>
                  <small>{{ item.role }}</small>
                </div>
              </footer>
            </article>
          </div>
        </div>

        <section class="client-strip" aria-label="适用客户">
          <p>适用于多类建筑安全服务客户</p>
          <div class="client-window">
            <div class="client-track">
              <span v-for="(client, index) in clientTicker" :key="`${client}-${index}`">
                {{ client }}
              </span>
            </div>
          </div>
        </section>
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
