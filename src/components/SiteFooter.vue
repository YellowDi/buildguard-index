<script setup>
import appHomeUrl from "../assets/screenshot-home-normal@2x.png"
import phoneShapeUrl from "../assets/upwize-phone-shape.png"
</script>

<template>
  <footer id="cta" class="site-footer">
    <section class="footer-cta reveal-on-scroll">
      <div class="footer-cta-bg" aria-hidden="true"></div>
      <div class="footer-cta-grid" aria-hidden="true"></div>

      <div class="footer-copy">
        <div class="footer-copy-stack">
          <h2>让客户下一次打开 App，就看清建筑安全状态</h2>
          <p>把建筑检测报告、风险提醒、整改建议和历史评估做成更适合客户使用的移动端体验。</p>
        </div>

        <div class="footer-check-list" aria-label="客户 App 核心能力">
          <span><i class="ri-check-line" aria-hidden="true"></i>一眼看清安全评分</span>
          <span><i class="ri-check-line" aria-hidden="true"></i>一键查看风险详情</span>
        </div>

        <div class="footer-actions">
          <a class="store-button footer-store-button" href="mailto:ops@buildguard.cn" aria-label="获取 iOS 客户 App">
            <i class="ri-apple-fill store-button__icon" aria-hidden="true"></i>
            <strong>获取 iOS 客户端</strong>
          </a>
          <a class="store-button footer-store-button" href="mailto:ops@buildguard.cn" aria-label="获取 Android 客户 App">
            <i class="ri-google-play-fill store-button__icon" aria-hidden="true"></i>
            <strong>获取 Android</strong>
          </a>
        </div>
      </div>

      <figure class="footer-phone" aria-label="宝京云维客户 App 建筑安全状态界面">
        <div class="footer-phone-frame">
          <img class="footer-phone-screen" :src="appHomeUrl" alt="宝京云维客户 App 建筑安全首页" />
          <img class="footer-phone-shell" :src="phoneShapeUrl" alt="" aria-hidden="true" />
        </div>
      </figure>
    </section>

    <div class="footer-main reveal-on-scroll">
      <div>
        <a class="brand footer-brand" href="#top">
          <span class="brand-mark"></span>
          <span>宝京云维</span>
        </a>
        <p>客户 App 端建筑安全检测服务入口。</p>
      </div>

      <nav class="footer-links" aria-label="页脚导航">
        <div>
          <strong>Quick links</strong>
          <a href="#top">首页</a>
          <a href="#features">功能</a>
          <a href="#workflow">流程</a>
          <a href="#testimonials">客户反馈</a>
        </div>
        <div>
          <strong>Support</strong>
          <a href="#faq">常见问题</a>
          <a href="mailto:ops@buildguard.cn">联系我们</a>
          <a href="/privacy-policy.html">隐私政策</a>
          <a href="/user-agreement.html">用户协议</a>
        </div>
        <div>
          <strong>Contact us</strong>
          <a href="mailto:ops@buildguard.cn">ops@buildguard.cn</a>
          <a href="tel:+8613800000000">+86 138 0000 0000</a>
        </div>
      </nav>
    </div>

    <div class="footer-bottom">
      <p>© 2026 宝京云维. All rights reserved.</p>
      <a href="#top">回到顶部</a>
    </div>
  </footer>
</template>
