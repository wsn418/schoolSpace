<template>
  <d2-container>
    <template slot="header">
      <el-row :gutter="20">
        <el-col :span="8">搜索租凭</el-col>
        <el-col :span="6" class="d2-text-center">
          <el-input v-model="input" placeholder="因数据过少，这次并未实现搜索功能" size="small"></el-input>
        </el-col>
        <el-col :span="6" style="cursor:pointer;margin-top:0px">
          <el-button icon="el-icon-search" type="primary" size="small" @click="getlist()">搜索</el-button>
        </el-col>
               <el-col :span="2" class="d2-text-center" style="cursor:pointer;"> <el-button @click="goToInsert">  我要发布</el-button></el-col>
        <el-col :span="2" class="d2-text-center" style="cursor:pointer;"><el-button @click="goToMy">  我的任务</el-button></el-col>
      </el-row>
    </template>

    <work-list :data="formatData" class="work-list" @clickItem="goToWorkDetail"></work-list>

    <template slot="footer">加载更多</template>
  </d2-container>
</template>

<script>
import WorkList from "@/components/worklist/workList";
import { GetWorkList } from "@/api/work/work";
import {formatDataWork} from "@/assets/js/index"
import axios from "axios";
// import axios from
export default {
  name: "page1",
  components: {
    WorkList
  },
  methods: {
    async getWorkLits() {
      const { data } = await axios.get("/api/rental/query/all");
      // console.log(data);
      if (data.status == 200) this.formatData = data.data;
      // console.log(this.formatData);
      // console.log(formatDataWork(this.formatData));
      this.formatData = formatDataWork(this.formatData);
       console.log(this.formatData);
    },
    goToWorkDetail(item) {
     
      this.$router.push({
        name: 'page12',
        params: {
          data: item
        }
      })
    },
    goToInsert(){
      this.$router.push({name:'page6'});
    },
    goToMy(){
    this.$router.push({name:'page7'});
    }
  },
  created() {
    this.getWorkLits();
  },
  data() {
    return {
      input: "",
      formatData: ""
    };
  }
};
</script>
<style lang ="less">
.el-col {
  border: 1px solid transparent;
}
</style>