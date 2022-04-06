<template>
  <div class="com-container">
    <div class="com-chart" ref="trend_ref"></div>
  </div>
</template>

<script>
import * as echarts from 'echarts'
export default {
  name: 'Trend',
  data() {
    return {
      chartInstance: null,
      allData: null // 从服务器中获取所有的数据
    }
  },
  mounted() {
    this.initChart()
    this.getData()
    window.addEventListener('resize', this.screenAdapter)
    this.screenAdapter()
  },
  destroyed() {
    window.removeEventListener('resize', this.adapter)
  },
  methods: {
    initChart() {
      this.chartInstance = echarts.init(this.$refs.trend_ref)
      const initOption = {}
      this.chartInstance.setOption(initOption)
    },
    async getData() {
      const res = await this.$httpScreen.get('')
      this.allData = res
      this.updateChart()
    },
    updateChart() {
      // 处理数据
      const updateOption = {}
      this.chartInstance.setOption(updateOption)
    },
    screenAdapter() {
      const adapterOption = {}
      this.chartInstance.setOption(adapterOption)
      this.chartInstance.resize()
    }
  }
}
</script>

<style scoped>
</style>
