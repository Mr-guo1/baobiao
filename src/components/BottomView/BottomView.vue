<template>
  <div class="bottom-view">
    <div class="view">
        <el-card shadow="hover">
            <template>
                <div class="title-wrapper">关键词搜索</div>
            </template>
            <template>
                <div class="chart-wrapper">
                    <div class="chart-inner">
                    <div class="chart">
                        <div class="chart-title">搜索用户数</div>
                        <div class="chart-data">93,634</div>
                        <v-chart :options="searchUserOptions() "/>
                    </div>
                    <div class="chart">
                        <div class="chart-title">搜索量</div>
                        <div class="chart-data">93,897</div>
                        <v-chart :options="searchUserOptions() "/>
                    </div>
                    </div>
                </div>
                <div class="table-wrapper">
                    <el-table :data="tableData">
                        <el-table-column prop="date" label="日期" width="180"></el-table-column>
                        <el-table-column prop="date" label="姓名" width="180"></el-table-column>
                        <el-table-column fixed prop="date" label="日期" width="180"></el-table-column>
                        <el-table-column prop="name" label="姓名" width="120"></el-table-column>
                        <el-table-column prop="province" label="省份" width="120"></el-table-column>
                        <el-table-column prop="city" label="市区" width="120"></el-table-column>
                        <el-table-column prop="address" label="地址" width="300"></el-table-column>
                        <el-table-column prop="zip" label="邮编" width="120"></el-table-column>
                    </el-table>
                </div>
                <div class="tol-wrapper">
                    <el-pagination background
                    layout="prev, pager, next"
                    :total="500"
                    :page-size="5"
                    >></el-pagination>
                </div>
            </template>
        </el-card>
    </div>
    <!-- 右面 -->
    <div class="view">
        <el-card shadow="hover">
            <template>
                <div class="title-wrapper">
                    <div class="title">分类销售排行</div>
                    <div class="radio-wrapper">
                        <el-radio-group v-model="radioSelect" size="small">
                            <el-radio-button label="品类"></el-radio-button>
                            <el-radio-button label="商品"></el-radio-button>
                        </el-radio-group>
                    </div>
                </div>
            </template>
            <template>
                <div class="charts-wrapper">
                  <v-chart :options="categoryOptions"/>
                </div>
            </template>
        </el-card>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }, {
        date: '2016-05-02',
        name: '王小虎',
        province: '上海',
        city: '普陀区',
        address: '上海市普陀区金沙江路 1518 弄',
        zip: 200333
      }
      ],
      radioSelect: '品类',
      categoryOptions: {}
    }
  },
  methods: {
    searchUserOptions () {
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
          data: [600, 432, 780, 884, 790, 830, 620, 820, 732, 620, 834, 690, 530, 820, 620],
          // 显示面积
          areaStyle: {
            color: 'yellowgreen'
          },
          // 隐藏折线 -- 但是每个峰值的点(item)还在
          lineStyle: {
            // width: 0
            color: 'yellowgreen'
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
    },
    onPageChang (page) {
      console.log(page)
    },
    renderPieChart () {
      const mockData = [
        {
          lengendname: '粉面粥店',
          value: 67,
          percent: '15.40%',
          // 定制颜色
          itemStyle: {
            color: 'rgb(92,213,217)'
          },
          // 最后实现lenged的时候在写
          name: '粉面粥店 | 15.40'
        },
        {
          lengendname: '简餐便当',
          value: 97,
          percent: '22.30%',
          // 定制颜色
          itemStyle: {
            color: 'rgb(255,122,122)'
          },
          // 最后实现lenged的时候在写
          name: '简餐便当 | 22.30%'
        },
        {
          lengendname: '汉堡披萨',
          value: 92,
          percent: '25.40%',
          // 定制颜色
          itemStyle: {
            color: 'rgb(255,220,96)'
          },
          // 最后实现lenged的时候在写
          name: '汉堡披萨 | 25.40%'
        }
      ]
      this.categoryOptions = {
        title: [
          {
            text: '品类分布',
            textStyle: {
              fontSize: 22,
              color: '#666'
            },
            left: 20,
            top: 20
          }, {
            // 副标题
            text: '累计订单量',
            subtext: '320',
            x: '50%',
            y: '46%',
            // 文本样式
            textStyle: {
              fontSize: 24,
              color: '#999'
            },
            subtextStyle: {
              fontSize: 24,
              color: '#333'
            },
            // 文本居中
            textAlign: 'center'
          }
        ],
        series: [
          {
            name: '品类分布',
            type: 'pie',
            data: mockData,
            label: {
              normal: {
                show: true,
                fontSize: 20,
                position: 'outside',
                formatter: function (params) {
                  return `${params.data.lengendname} | ${params.data.percent}`
                }
              }
            },
            // 图表位置
            center: ['50%', '50%'],
            radius: ['80%', '50%'],
            // 控制文字和图标的距离
            labelLine: {
              normal: {
                length: 100,
                length2: 80,
                smooth: true
              }
            },
            // true按照顺时针排列
            clockwise: true,
            itemStyle: {
              borderWidth: 4,
              borderColor: '#fff'
            }
          }
        ],
        legend: {
          type: 'scroll',
          orient: 'vertical',
          left: '80%',
          height: 400,
          top: 'center',
          textStyle: {
            color: 'red'
          }
        },
        tooltip: {
          trigger: 'item',
          formatter: function (params) {
            // return '111'
            const str = params.seriesName + '<br />' + params.marker + params.data.lengendname + '<br />' + '数量:' + params.data.value + '<br />' + '占比:' + params.data.percent
            return str
          }
        }
      }
    }
  },
  mounted () {
    this.renderPieChart()
  }
}
</script>

<style lang="scss">
.bottom-view{
    display: flex;
    margin-top: 15px;
    .view{
        flex: 1;
        width: 30%;
        box-sizing: border-box;
        &:first-child{
            padding: 0 10px 0 0;
        }
        &:last-child{
             padding: 0  0 0 10px;
        }
        .title-wrapper{
            display: flex;
            align-content: center;
            height: 60px;
            box-sizing: border-box;
            border-bottom: 1px solid #eee;
            font-size: 14px;
            font-weight: 500;
            .radio-wrapper{
                flex: 1;
                display: flex;
                justify-content: flex-end;
                padding-left: 20px;
            }
        }
        .chart-wrapper{
            display: flex;
            flex-direction: column;
            height: 120px;
            .chart-inner{
                display: flex;
                padding: 0 10px;
                margin-top: 20px;
                .chart{
                    flex: 1;
                    padding: 0 10px;
                    .chart-title{
                        color: #999;
                        font-size: 14px;
                    }
                    .chart-data{
                        font-size: 22px;
                        color: #333;
                        font-weight: 500;
                        letter-spacing: 2px;
                    }
                    .echarts{
                        height: 50px;
                    }
                }
            }
        }
        .tol-wrapper{
            display: flex;
            padding: 20px 0 0 400px;
        }
        .charts-wrapper{
          display: flex;
            height: 580px;
        }
    }
}
</style>
