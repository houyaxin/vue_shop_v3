<template>
  <div class="com-page">
    <trend></trend>
  </div>
</template>

<script>
import Trend from './Trend.vue'
// 导入全局样式表
import '../../assets/css/screen-global.less'
export default {
  name: 'TrendPage',
  components: { Trend }
}
</script>

<style scoped>
</style>
