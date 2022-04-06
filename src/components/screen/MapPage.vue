<template>
  <div class="com-page">
    <simple-map></simple-map>
  </div>
</template>

<script>
import Map from '@/components/screen/Map'
// 导入全局样式表
import '../../assets/css/screen-global.less'
export default {
  name: 'Mappage',
  components: {
    'simple-map': Map
  }
}
</script>

<style lang="less" scoped>
</style>
