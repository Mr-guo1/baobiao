<template>
    <div class="sales-view">
        <el-card shadow="hover" :body-style="[ padding='0 0 20px 0']">
          <template v-slot:header>
            <div class="menu-wrapper">
              <el-menu :default-active="activeIndex" mode="horizontal" @selet="onMenuSelect">
                <el-menu-item index="1">销售额</el-menu-item>
                <el-menu-item index="2">访问量</el-menu-item>
              </el-menu>
              <div class="menu-right">
              <el-radio-group v-model="radioSelect" size="small">
              <el-radio-button label="今日"></el-radio-button>
              <el-radio-button label="本周"></el-radio-button>
              <el-radio-button label="本月"></el-radio-button>
              <el-radio-button label="今年"></el-radio-button>
              </el-radio-group>
              <el-date-picker class="sales-view-date-pick" :picker-options="pickerOptions" v-model="value1" type="daterange" range-separator="至" start-placeholder="开始日期" end-placeholder="结束日期">
              </el-date-picker>
              </div>
            </div>
          </template>
          <template>
            <div class="sales-vie-chart-wrapper">
              <v-chart :options="chartOption" />
              <div class="sales-view-list">
                <div class="sales-view-title">排行榜</div>
                <div class="list-item-wrapper">
                  <div class="list-item" v-for="item in rankData" :key="item.no">
                  <div :class="['list-item-no', +item.no <= 4 ? 'top-no' : '']">{{item.no}}</div>
                  <div class="list-item-name">{{item.name}}</div>
                  <div class="list-item-money">{{item.money}}</div>
                  </div>
                </div>
              </div>
            </div>
          </template>
        </el-card>
    </div>
</template>
<script>
export default {
  data () {
    return {
      activeIndex: '1',
      radioSelect: '今日',
      dete: null,
      pickerOptions: {
        shortcuts: [
          {
            text: '最近一周',
            onClick (picker) {
              const end = new Date()
              const start = new Date()
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 7)
              picker.$emit('pick', [start, end])
            }
          },
          {
            text: '最近一个月',
            onClick (picker) {
              const end = new Date()
              const start = new Date()
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 30)
              picker.$emit('pick', [start, end])
            }
          },
          {
            text: '最近三个月',
            onClick (picker) {
              const end = new Date()
              const start = new Date()
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 90)
              picker.$emit('pick', [start, end])
            }
          }
        ]
      },
      chartOption: {
        title: {
          text: '年度销售额',
          textStyle: {
            fontSize: 12,
            color: '#666'
          },
          top: 20,
          left: 25
        },
        xAxis: {
          type: 'category',
          data: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月'],
          axisTick: {
            alignWithLabel: true
          },
          // x轴颜色
          axisLine: {
            lineStyle: {
              color: 'red'
            }
          },
          // x轴字体颜色
          axisLabel: {
            color: 'blue'
          }
        },
        yAxis: {
          // 不显示 Y 轴
          axisLine: {
            show: false
          },
          axisTick: {
            show: false
          },
          // 修改横线颜色
          splitLine: {
            lineStyle: {
              type: 'dotted',
              color: '#eee'
            }
          }
        },
        // 显示图表的数据
        series: [
          {
            type: 'bar',
            // 图表的宽度
            barWidth: '35%',
            // 绘图的数据
            data: [150, 230, 224, 218, 135, 147, 220, 150, 230, 224, 218, 135, 147, 220]
          }
        ],
        color: ['#3398db'],
        // 调整位置
        grid: {
          top: 70,
          bottom: 50,
          left: 60,
          right: 60
        }
      },
      rankData: [
        {
          no: 1,
          name: '麦当劳',
          money: 200
        },
        {
          no: 2,
          name: '麦当劳',
          money: 200
        },
        {
          no: 3,
          name: '麦当劳',
          money: 200
        },
        {
          no: 4,
          name: '麦当劳',
          money: 200
        },
        {
          no: 5,
          name: '麦当劳',
          money: 200
        },
        {
          no: 6,
          name: '麦当劳',
          money: 200
        }
      ]
    }
  },
  methods: {
    onMenuSelect (index) {
      this.activeIndex = index
    }
  }
}

</script>

<style lang="scss">
.sales-view{
  margin-top: 20px;
  .menu-wrapper{
    display: flex;
    position: relative;
    .sales-view-menu{
      width: 100%;
      padding-left: 20px;
      .el-menu-item{
        height: 50px;
        line-height: 50px;
        margin:  0 20px;
      }
    }
  }
}
.menu-right{
  position: absolute;
  top: 0;
  right: 20px;
  align-items: center;
  justify-content: flex-end;
  .sales-view-data-pick{
    margin-left: 20px;
  }
}
.sales-vie-chart-wrapper{
  display: flex;
  height: 270px;
  .echarts{
    flex: 0 0 70%;
    width: 70%;
    height: 100%;
  }
  .sales-view-list{
    flex: 1;
    width: 100%;
    height: 100%;
    overflow: hidden;
    .sales-view-title{
      margin-top: 20px;
      font-size: 12px;
      color: #666;
      font-weight: 500;
    }
    .list-item-wrapper{
      margin-top: 15px;
      .list-item{
      display: flex;
      align-content: center;
      font-size: 12px;
      height: 20px;
      padding: 6px 20px 6px 0;
      .list-item-no{
        display: flex;
        align-items: center;
        justify-content: center;
        width: 20px;
        height: 20px;
        color: #333;
        &.top-no{
          background: #000;
          color: #fff;
          border-radius: 50%;
          font-weight: 500;
        }
  }
        .list-item-name{
          margin-left: 10px;
          color: #333;
        }
        .list-item-money{
          flex: 1;
          text-align: right;
        }
      }
    }
  }
}
</style>
