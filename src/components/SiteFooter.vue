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
      <nav class="footer-top" aria-label="页脚导航">
        <div class="footer-column">
          <strong>Quick links</strong>
          <a href="#top">首页</a>
          <a href="#features">功能</a>
          <a href="#workflow">流程</a>
          <a href="#testimonials">客户反馈</a>
          <a href="#faq">常见问题</a>
        </div>

        <div class="footer-column">
          <strong>建筑安全服务</strong>
          <a href="#app-features">客户 App</a>
          <a href="#features">风险详情</a>
          <a href="#workflow">整改跟进</a>
          <a href="#faq">历史评估</a>
          <a href="mailto:ops@buildguard.cn">在线报修</a>
        </div>

        <div class="footer-column">
          <strong>Support & resources</strong>
          <a href="mailto:ops@buildguard.cn">Help Center</a>
          <a href="#workflow">How It Works</a>
          <a href="/privacy-policy.html">隐私政策</a>
          <a href="/user-agreement.html">用户协议</a>
          <a href="mailto:ops@buildguard.cn">联系我们</a>
        </div>

        <div class="footer-column footer-contact">
          <strong>Contact us</strong>
          <p>Address: 上海市建筑安全服务中心</p>
          <p>Email: <a href="mailto:ops@buildguard.cn">ops@buildguard.cn</a></p>
          <p>Phone: <a href="tel:+8613800000000">+86 138 0000 0000</a></p>
        </div>
      </nav>

      <a class="footer-wordmark" href="#top" aria-label="宝京云维首页">
        <span class="footer-wordmark-mark" aria-hidden="true"></span>
        <span>宝京云维</span>
      </a>

      <div class="footer-bottom">
        <div class="footer-bottom-left">
          <a href="mailto:ops@buildguard.cn">Support</a>
          <a href="/privacy-policy.html">Privacy</a>
          <a href="/user-agreement.html">Agreement</a>
          <a href="#top">Back to top</a>
        </div>
        <div class="footer-bottom-right">
          <a href="/user-agreement.html">Terms of use</a>
          <span>宝京云维 © 2026</span>
        </div>
      </div>
    </div>
  </footer>
</template>
