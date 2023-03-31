<template>
  <div class="top-view">
    <el-row :gutter="20">
        <el-col :span="6">
            <el-card shadow="hover">
                <total-sales></total-sales>
            </el-card>
        </el-col>
        <el-col :span="6">
            <el-card shadow="hover">
                <total-orders></total-orders>
            </el-card>
        </el-col>
        <el-col :span="6">
            <el-card shadow="hover">
                <totady-users></totady-users>
            </el-card>
        </el-col>
        <el-col :span="6">
            <el-card shadow="hover">
                <total-users></total-users>
            </el-card>
        </el-col>
    </el-row>
  </div>
</template>

<script>
import TotalUsers from '../TotalUsers/TotalUsers.vue'
import TotalSales from '../TotalSales/TotalSales.vue'
import TotalOrders from '../TotalOrders/TotalOrders.vue'
import TotadyUsers from '../TotadyUsers/TotadyUsers.vue'

export default {
  components: {
    TotalUsers,
    TotalSales,
    TotalOrders,
    TotadyUsers
  }
}
</script>

<style>
</style>
