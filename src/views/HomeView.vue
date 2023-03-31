<template>
  <div class="home">
    <top-view></top-view>
    <sales-view></sales-view>
    <map-view></map-view>
    <bottom-view></bottom-view>
  </div>
</template>

<script>
import TopView from '../components/TopView/TopView.vue'
import SalesView from '../components/SalesView/SalesView.vue'
import MapView from '../components/MapView/MapView.vue'
import BottomView from '../components/BottomView/BottomView.vue'

export default {
  name: 'HomeView',
  components: {
    TopView,
    SalesView,
    MapView,
    BottomView
  }
}
</script>
<style>
.home{
margin: 0;
padding: 20px;
box-sizing: border-box;
width: 100%;
height: 100%;
background: #eee;
}
</style>
