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
  { value: "17k+", label: "整改进度同步" },
  { value: "2k+", label: "项目客户使用" },
]

const analyticsItems = [
  {
    title: "风险进度",
    text: "检测结论、风险等级和整改节点同步呈现。",
  },
  {
    title: "报告归档",
    text: "历史报告和现场照片随时查看，不再翻找文件。",
  },
]

const featureCards = [
  {
    title: "检测报告随时看",
    text: "客户在手机端查看评估结论、风险项、现场照片和整改建议。",
    tone: "blue",
  },
  {
    title: "整改节点不遗漏",
    text: "每个问题都有处理状态、责任人和时间线，闭环过程清晰可追踪。",
    tone: "red",
  },
  {
    title: "消息提醒及时到达",
    text: "报告出具、风险升级、整改更新都能第一时间触达客户。",
    tone: "green",
  },
  {
    title: "项目资料统一沉淀",
    text: "建筑档案、检测记录和后续服务都收在一个 App 里。",
    tone: "violet",
  },
]

const steps = [
  {
    title: "绑定项目",
    text: "客户通过手机号或项目码绑定建筑项目，快速进入专属服务空间。",
  },
  {
    title: "查看进度",
    text: "检测排期、现场执行、报告生成和整改处理都能在 App 中实时查看。",
  },
  {
    title: "完成闭环",
    text: "客户确认问题、跟踪整改结果，并长期保留所有检测资料。",
  },
]

const reasons = [
  {
    title: "客户视角清晰",
    text: "把专业检测过程转成客户能快速理解的进度、评分和风险说明。",
  },
  {
    title: "实时同步状态",
    text: "工单、报告和整改更新后，客户 App 端立即同步最新状态。",
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
    title: "发现高风险问题时，客户马上知道",
    text: "App 会把风险等级、问题位置、现场照片和建议动作放在同一张卡片里，客户无需等待人工汇总。",
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
    role: "检测机构运营",
  },
  {
    quote: "我们最看重历史档案。后续复查时，客户能快速回看上次问题和整改结果。",
    name: "林女士",
    role: "资产管理方",
  },
]

const clientLogos = ["物业集团", "园区运营", "业委会", "商业楼宇", "资产管理", "城市更新", "检测机构"]
const clientTicker = [...clientLogos, ...clientLogos]

const faqs = [
  {
    q: "客户 App 主要给谁使用？",
    a: "面向业主、物业负责人、资产方和项目客户，用来查看检测进度、报告、风险项和整改结果。",
  },
  {
    q: "报告内容会和后台同步吗？",
    a: "会。后台生成或更新检测报告后，客户 App 端会同步展示结论、图片、风险等级和建议。",
  },
  {
    q: "客户能看到整改进度吗？",
    a: "可以。每个风险项都能呈现处理状态、更新时间和结果说明，便于客户持续跟进。",
  },
  {
    q: "是否支持多项目客户？",
    a: "支持。客户可在 App 内切换不同建筑项目，分别查看资料、报告和服务状态。",
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
            <span>客户验房</span>
            <span>就在掌上</span>
          </h1>
        </div>

        <div class="hero-lower">
          <div class="hero-proof hero-enter enter-2">
            <p>把检测报告、风险提醒和整改进度，交给客户随时查看。</p>
            <div class="avatar-row" aria-label="客户使用者">
              <span v-for="avatar in heroAvatars" :key="avatar">{{ avatar }}</span>
            </div>
            <strong>Trusted by</strong>
            <small>2,000+ 项目客户持续使用</small>
          </div>

          <div class="hero-phone-stage hero-enter enter-3" aria-label="客户 App 手持截图展示">
            <img class="phone-hand" :src="phoneHandUrl" alt="" aria-hidden="true" />
            <div class="hero-mock-phone">
              <img
                class="mock-phone-screen"
                :src="appHomeUrl"
                alt="宝京云维客户 App 首页巡检报告界面"
              />
              <img class="mock-phone-shape" :src="phoneShapeUrl" alt="" aria-hidden="true" />
            </div>
            <span class="hero-badge badge-left">真实 App 截图</span>
            <span class="hero-badge badge-right">风险实时同步</span>
          </div>

          <div class="hero-actions hero-enter enter-4">
            <p>客户不需要理解后台流程，只需要打开 App，就能看清每一步。</p>
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
        <h2>让客户持续看见服务价值</h2>
        <p>从检测开始到整改闭环，客户 App 把专业服务过程变成清晰、可信、可追踪的体验。</p>
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
        <h2>实时数据，让客户放心跟进</h2>
        <p>客户随时查看检测进展、风险数量、报告状态和整改进度，不再依赖人工转述。</p>
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
        <a class="text-link" href="#cta">Explore more features</a>
        <h2>客户 App 的核心功能</h2>
        <p>参考 Upwize 的功能卡节奏，用更轻的界面把客户最关心的信息放到前面。</p>
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
        <span class="pill-label">Get started</span>
        <h2>三步完成客户服务闭环</h2>
        <p>让客户 App 只承接必要动作，流程越简单，客户越愿意持续使用。</p>
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
          <a class="text-link" href="#cta">Explore more features</a>
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
        <p>客户 App 的定位、同步和项目管理方式。</p>
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
