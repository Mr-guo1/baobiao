<template>
  <div class="common-card">
     <common-card
     title="累计用户数"
     value="1,087,503"
     >
     <!-- <template>
      <div id="total-users-chart" :style="{width: '100%', height: '100%'}"></div>
     </template> -->
     <v-chart :options="getOptions() "/>
     <template v-slot:footer>
      <div class="total-users-footer">
                <span>日同比</span>
                <span class="emphasis">7.33%</span>
                <div class="increase"></div>
                <span class="month">月同比</span>
                <span class="emphasis">7.33%</span>
                <div class="decrease"></div>
          </div>
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
        series: [{
          type: 'bar',
          data: [200],
          barWidth: 10,
          stack: '总量',
          itemStyle: {
            color: '#45c946'
          }
        },
        {
          type: 'bar',
          data: [250],
          // stack可以让两条线合成一条线
          stack: '总量',
          // 线的宽度
          barWidth: 10,
          // 线的颜色
          itemStyle: {
            color: '#eee'
          }
        },
        {
          type: 'custom',
          // 需要有数据 没有数据渲染不出来
          data: [200],
          stack: '总量',
          // custom 系列需要开发者自己提供图形渲染的逻辑。这个渲染逻辑一般命名为 renderItem
          renderItem: (params, api) => {
            // console.log(params, api)
            const value = api.value(0)
            // console.log(value)
            // 传入坐标点 coord方法会自动计算坐标点
            const endPoint = api.coord([value, 0]) // 图形是居中显示的
            // console.log(endPoint)
            // 返回值中就是绘制的图形
            return {
              // 线段 -- 可以传入一个svg图形
              type: 'group',
              // 坐标系
              position: endPoint,
              children: [
                {
                  type: 'path',
                  // 形状
                  shape: {
                    // svg图形的参数
                    // 去阿里图标库 找到相应的图标，找path 复制 d中的值拿过来即可
                    d: 'M512 128l384 768H128z',
                    // x轴和y轴偏移量 -- 可以修改位置
                    x: 0,
                    y: 10,
                    // 宽度和高度
                    width: 10,
                    height: 10,
                    layout: 'cover'
                  },
                  style: {
                    // 填充色
                    fill: '#45c946'
                  }
                },
                {
                  type: 'path',
                  // 形状
                  shape: {
                    // svg图形的参数
                    // 去阿里图标库 找到相应的图标，找path 复制 d中的值拿过来即可
                    d: 'M524.096 753.088l342.912-395.584a16 16 0 0 0-12.032-26.496H169.024a16 16 0 0 0-12.032 26.496l343.04 395.52a16 16 0 0 0 24.064 0z',
                    // x轴和y轴偏移量 -- 可以修改位置
                    x: 0,
                    y: -20,
                    // 宽度和高度
                    width: 10,
                    height: 10,
                    layout: 'cover'
                  },
                  style: {
                    // 填充色
                    fill: '#45c946'
                  }
                }
              ]
            }
          }
        }
        ],
        xAxis: {
          type: 'value',
          // 隐藏坐标系
          show: false
        },
        yAxis: {
          type: 'category',
          // 隐藏坐标系
          show: false
        },
        grid: {
          top: 0,
          bottom: 0,
          left: 0,
          right: 0
        }
      }
    }
  }
  // mounted () {
  //   const chartDom = document.getElementById('total-users-chart')
  //   const chart = this.$echarts.init(chartDom)
  //   chart.setOption({
  //   })
  // }
}
</script>
<style scoped lang="scss">
.compare{
height: 100%;
// background: yellow;
}
span{
font-size: 12px;
}
.money{
margin-left: 5px;
color: #333;
font-weight: 700;
}
.total-users-footer{
  font-size: 8px;
  display: flex;
  align-items: center;
}
.month{
  margin-left: 10px;
}
</style>
