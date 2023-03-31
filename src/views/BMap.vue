<template>
  <v-chart :options="options" />
</template>

<script>
import 'echarts/extension/bmap/bmap'
export default {
  data () {
    return {
      options: {}
    }
  },
  mounted () {
    this.options = {
      bmap: {
        key: 'G1LFyjrNGIkns5OfpZnrCGAKxpycPLwb',
        center: [104, 114129, 37.55039],
        zoom: 5,
        // 可以交互
        roam: true
      }
    }
  }
}
</script>

<style>

</style>
