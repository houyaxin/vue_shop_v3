<template>
  <div class="com-page">
    <seller></seller>
  </div>
</template>

<script>
import Seller from '../screen/Seller'
// 导入全局样式表
import '../../assets/css/screen-global.less'
export default {
  name: 'SellerPage',
  components: { Seller }
}
</script>

<style scoped>
</style>
