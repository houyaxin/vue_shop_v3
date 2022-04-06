<template>
  <div>
    <!-- 面包屑导航区域 -->
    <el-breadcrumb separator-class="el-icon-arrow-right">
      <el-breadcrumb-item :to="{ path: '/home' }">首页</el-breadcrumb-item>
      <el-breadcrumb-item>数据统计</el-breadcrumb-item>
      <el-breadcrumb-item>数据报表</el-breadcrumb-item>
    </el-breadcrumb>
    <!-- 卡片视图区域 -->
    <el-card class="echart-box">
      <div><el-button type="primary" size="mini" @click="toEchart">电商平台实时监控系统</el-button></div>
    </el-card>
    <el-card>
      <!-- 2. 为 Echarts准备一个具备大小（宽高）的DOM -->
      <div id="main" style="width: 750px; height: 400px"></div>
    </el-card>
  </div>
</template>
<script>
// 1. 导入 Echarts
import * as echarts from 'echarts'
import _ from 'lodash'

export default {
  data() {
    return {
      // 需要合并的数据
      options: {
        title: {
          text: '用户来源'
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross',
            label: {
              backgroundColor: '#E9EEF3'
            }
          }
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        xAxis: [
          {
            boundaryGap: false
          }
        ],
        yAxis: [
          {
            type: 'value'
          }
        ]
      }
    }
  },

  created() {},
  // 此时页面上的元素已经被渲染完毕了
  async mounted() {
    // 3. 基于准备好的dom，初始化echarts实例
    var myChart = echarts.init(document.getElementById('main'))

    const { data: res } = await this.$http.get('reports/type/1')
    console.log(res, 'res')
    if (res.meta.status !== 200) {
      return this.$message.error('获取折线图数据失败！')
    }
    // 4. 准备数据和配置项
    const result = _.merge(res.data, this.options)
    // 5. 绘制图标
    myChart.setOption(result)
  },
  methods: {
    toEchart() {
      this.$router.push('/screenpage')
    }
  }
}
</script>
<style lang="less" scoped>
.echart-box {
  margin-bottom: 10px;
}
</style>
