<template>
  <div>
    <common-card
      title="累计订单量"
      value="2,157,420"
    >
      <!-- <template>
        <div id="total-orders-chart" :style="{width: '100%', height: '100%'}"></div>
      </template> -->
      <v-chart :options="getOptions() "/>
      <template v-slot:footer>
          <span>昨日订单量</span>
          <span class="emphasis">2,000,000</span>
      </template>
    </common-card>
  </div>
</template>
<script>
import CommonCardMixin from '../mixins/commonCardMixin'
export default {
  mixins: [CommonCardMixin],
  methods: {
    getOptions () {
      return {
        xAxis: {
          type: 'category',
          // 每一个分类的数据
          data: [],
          // 隐藏X轴的数据
          show: false,
          // 图标默认是对两边的轴有间距的 设置为false，可以让间距消失
          boundaryGap: false
        },
        yAxis: {
          // 隐藏Y轴的数据
          show: false
        },
        series: [{
          type: 'line',
          // 绘图的数据
          data: [620, 432, 220, 534, 790, 430, 220, 320, 532, 320, 834, 690, 530, 220, 620],
          // 显示面积
          areaStyle: {
            color: 'purple'
          },
          // 隐藏折线 -- 但是每个峰值的点(item)还在
          lineStyle: {
            width: 0
          },
          // 隐藏items
          itemStyle: {
            opacity: 0
          },
          // 显示的更平缓
          smooth: true
        }],
        // 调整位置
        grid: {
          top: 0,
          bottom: 0,
          left: 0,
          right: '10px'
        }
      }
    }
  }
  // mounted () {
  //   const chartDom = document.getElementById('total-orders-chart')
  //   console.log(chartDom)
  //   const chart = this.$echarts.init(chartDom)
  //   chart.setOption({
  //   })
  // }
}
</script>
<style scoped lang="scss">

</style>
