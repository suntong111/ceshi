<template>
  <div class="app-container">
    <div>
      <el-button type="success">添加商品</el-button>
    </div>
    <el-table
      :data="list"
      border
      fit
      highlight-current-row
    >

            <el-table-column align="center" label="序号" width="95">
              <template slot-scope="scope">
                {{ scope.$index+1 }}
              </template>
            </el-table-column>

      <el-table-column label="商品id" width="95">-->
                <template slot-scope="scope">
                  {{ scope.row.id }}
                </template>
              </el-table-column>

            <el-table-column label="商品名称" width="110" align="center">
              <template slot-scope="scope">
                <span>{{ scope.row.username }}</span>
              </template>
            </el-table-column>

      <el-table-column label="操作" align="center" width="230" class-name="small-padding fixed-width">
        <template slot-scope="scope">
          <el-button type="primary" size="mini" @click="editpro(scope.row.id)">
            编辑
          </el-button>

          <el-button  size="mini" type="danger" @click="delpro(scope.row.id)">
            删除
          </el-button>
        </template>
      </el-table-column>

<!--      <el-table-column align="center" label="ID" width="95">-->
<!--        <template slot-scope="scope">-->
<!--          {{ scope.$index }}-->
<!--        </template>-->
<!--      </el-table-column>-->
<!--      <el-table-column label="Title">-->
<!--        <template slot-scope="scope">-->
<!--          {{ scope.row.title }}-->
<!--        </template>-->
<!--      </el-table-column>-->
<!--      <el-table-column label="Author" width="110" align="center">-->
<!--        <template slot-scope="scope">-->
<!--          <span>{{ scope.row.author }}</span>-->
<!--        </template>-->
<!--      </el-table-column>-->
<!--      <el-table-column label="Pageviews" width="110" align="center">-->
<!--        <template slot-scope="scope">-->
<!--          {{ scope.row.pageviews }}-->
<!--        </template>-->
<!--      </el-table-column>-->
<!--      <el-table-column class-name="status-col" label="Status" width="110" align="center">-->
<!--        <template slot-scope="scope">-->
<!--          <el-tag :type="scope.row.status | statusFilter">{{ scope.row.status }}</el-tag>-->
<!--        </template>-->
<!--      </el-table-column>-->
<!--      <el-table-column align="center" prop="created_at" label="Display_time" width="200">-->
<!--        <template slot-scope="scope">-->
<!--          <i class="el-icon-time" />-->
<!--          <span>{{ scope.row.display_time }}</span>-->
<!--        </template>-->
<!--      </el-table-column>-->
    </el-table>
  </div>
</template>

<script>
import { getList } from '@/api/table'

export default {

  data() {
    return {
      list: null,

    }
  },
  created() {
    this.fetchData();
  },
  methods: {
    editpro(id) {
      console.log(this.$router.push("/editproduct/index"+id))
      this.$router.push("/editproduct/index/"+id)
    },
    fetchData() {
      var vm = this;
      this.axios({
           method:"GET",
        url:'http://localhost:8080/user'
      }).then(function(res){
        vm.list = res.data.data
        console.log(res)
      })
    },
    delpro(id){
      var vm = this;
      this.axios({
        method:"GET",
        url:'http://localhost:8080/user/delete?id='+id
      }).then(function(res){
        console.log(res)
        if(res.data.msg=="success"){
            vm.$message({
              message:'删除成功',
              type:'success'
            });
          vm.fetchData();
        }
        // console.log(res)
      }).catch(function (error) {
      vm.$message.error('删除失败')
      });

    }
  }
}
</script>
