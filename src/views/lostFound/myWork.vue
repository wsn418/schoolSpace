<template>
  <d2-container>
  
      <template slot="header">
      <el-row :gutter="20">
        <el-col :span="8">搜索物品</el-col>
        <el-col :span="6" class="d2-text-center">
          <el-input v-model="input" placeholder="请输入" size="small"></el-input>
        </el-col>
        <el-col :span="6" style="cursor:pointer;margin-top:0px">
          <el-button icon="el-icon-search" type="primary" size="small" @click="getlist()">搜索</el-button>
        </el-col>
               <el-col :span="2" class="d2-text-center" style="cursor:pointer;"> <el-button @click="goToInsert">  我要发布</el-button></el-col>
        <el-col :span="2" class="d2-text-center" style="cursor:pointer;"><el-button @click="goToMy">  我的任务</el-button></el-col>
      </el-row>
    </template>
      尚未完成
    <template slot="footer">加载更多</template>
  </d2-container>
  </template>

<script>
export default {
  name: 'page1',
  data() {
    return{
      input:''
    }
  }
}
</script>
<style>
  .el-col {
    border: 1px solid transparent;
    
  }
</style>