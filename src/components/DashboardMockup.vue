<script setup>
const menuItems = ["概览", "客户建筑", "检测工单", "检测计划", "整改跟踪", "报告中心"]
const metrics = [
  { label: "待检建筑", value: "128", delta: "+18.4%" },
  { label: "进行中工单", value: "46", delta: "-6.2%", warning: true },
  { label: "已发现风险", value: "312", delta: "+11.8%" },
  { label: "报告归档", value: "860", delta: "+9.1%" },
]
const barHeights = ["44%", "78%", "52%", "64%", "38%", "59%", "74%", "33%", "45%", "66%", "24%", "55%"]
const rows = [
  { name: "华南商务中心幕墙检查", tag: "高风险", level: "high", due: "今天" },
  { name: "星河公寓消防通道复核", tag: "中风险", level: "mid", due: "明天" },
  { name: "云湖园区地下车库巡检", tag: "轻微", level: "low", due: "5 月 16 日" },
]
</script>

<template>
  <div class="dashboard-shell" aria-label="宝京云维后台概览示意图">
    <aside class="dash-sidebar">
      <div class="dash-logo">
        <span class="brand-mark small"></span>
        <strong>宝京云维</strong>
      </div>
      <span
        v-for="(item, index) in menuItems"
        :key="item"
        class="side-item"
        :class="{ active: index === 0 }"
      >
        {{ item }}
      </span>
      <div class="side-footer">
        <span>本周完成率</span>
        <strong>92%</strong>
      </div>
    </aside>

    <div class="dash-main">
      <div class="dash-topbar">
        <div>
          <span class="muted">上午好，运营团队</span>
          <h2>建筑安全检测看板</h2>
        </div>
        <div class="search-pill">搜索建筑、工单、客户</div>
      </div>

      <div class="metric-grid">
        <article v-for="metric in metrics" :key="metric.label">
          <span>{{ metric.label }}</span>
          <strong>{{ metric.value }}</strong>
          <em :class="{ warning: metric.warning }">{{ metric.delta }}</em>
        </article>
      </div>

      <div class="dashboard-row">
        <section class="chart-card">
          <div class="card-head">
            <strong>风险趋势</strong>
            <span>近 12 个月</span>
          </div>
          <div class="bar-chart" aria-hidden="true">
            <span v-for="height in barHeights" :key="height" :style="{ '--h': height }"></span>
          </div>
        </section>

        <section class="quick-card">
          <strong>快捷操作</strong>
          <button type="button">创建工单</button>
          <button type="button">上传照片</button>
          <button type="button">生成报告</button>
          <button type="button">通知整改</button>
        </section>
      </div>

      <section class="table-card">
        <div class="card-head">
          <strong>正在处理</strong>
          <span>8 个工单</span>
        </div>
        <div v-for="row in rows" :key="row.name" class="table-row">
          <span>{{ row.name }}</span>
          <b class="tag" :class="row.level">{{ row.tag }}</b>
          <em>{{ row.due }}</em>
        </div>
      </section>
    </div>
  </div>
</template>
