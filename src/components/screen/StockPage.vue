<template>
  <div class="com-page">
    <stock></stock>
  </div>
</template>

<script>
import Stock from '@/components/screen/Stock'
// 导入全局样式表
import '../../assets/css/screen-global.less'
export default {
  name: 'Stockpage',
  components: { Stock }
}
</script>

<style lang="scss" scoped>
</style>
