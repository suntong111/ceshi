<template>
  <div class="app-container">

<!--    {{this.$route.params.id}}-->
        <el-form ref="form" :model="product" label-width="120px">
          <el-form-item label="商品名称">
                    <el-input v-model="product.username" />
                  </el-form-item>
          <el-form-item label="商品价格">
            <el-input v-model="product.password" />
          </el-form-item>

          <el-form-item>
                    <el-button type="primary" @click="onSubmit">添加</el-button>
<!--                    <el-button @click="onCancel">Cancel</el-button>-->
                  </el-form-item>
        </el-form>

<!--    <el-form ref="form" :model="form" label-width="120px">-->
<!--      <el-form-item label="Activity name">-->
<!--        <el-input v-model="form.name" />-->
<!--      </el-form-item>-->
<!--      <el-form-item label="Activity zone">-->
<!--        <el-select v-model="form.region" placeholder="please select your zone">-->
<!--          <el-option label="Zone one" value="shanghai" />-->
<!--          <el-option label="Zone two" value="beijing" />-->
<!--        </el-select>-->
<!--      </el-form-item>-->
<!--      <el-form-item label="Activity time">-->
<!--        <el-col :span="11">-->
<!--          <el-date-picker v-model="form.date1" type="date" placeholder="Pick a date" style="width: 100%;" />-->
<!--        </el-col>-->
<!--        <el-col :span="2" class="line">-</el-col>-->
<!--        <el-col :span="11">-->
<!--          <el-time-picker v-model="form.date2" type="fixed-time" placeholder="Pick a time" style="width: 100%;" />-->
<!--        </el-col>-->
<!--      </el-form-item>-->
<!--      <el-form-item label="Instant delivery">-->
<!--        <el-switch v-model="form.delivery" />-->
<!--      </el-form-item>-->
<!--      <el-form-item label="Activity type">-->
<!--        <el-checkbox-group v-model="form.type">-->
<!--          <el-checkbox label="Online activities" name="type" />-->
<!--          <el-checkbox label="Promotion activities" name="type" />-->
<!--          <el-checkbox label="Offline activities" name="type" />-->
<!--          <el-checkbox label="Simple brand exposure" name="type" />-->
<!--        </el-checkbox-group>-->
<!--      </el-form-item>-->
<!--      <el-form-item label="Resources">-->
<!--        <el-radio-group v-model="form.resource">-->
<!--          <el-radio label="Sponsor" />-->
<!--          <el-radio label="Venue" />-->
<!--        </el-radio-group>-->
<!--      </el-form-item>-->
<!--      <el-form-item label="Activity form">-->
<!--        <el-input v-model="form.desc" type="textarea" />-->
<!--      </el-form-item>-->
<!--      <el-form-item>-->
<!--        <el-button type="primary" @click="onSubmit">Create</el-button>-->
<!--        <el-button @click="onCancel">Cancel</el-button>-->
<!--      </el-form-item>-->
<!--    </el-form>-->
  </div>
</template>

<script>
export default {
  data() {
    return {
      product: {
        username: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      }
    }
  },
  created() {
    this.fatchDataByid();
  },
  methods: {

    fatchDataByid(){
      var id = this.$route.params.id;
      var vm = this
      console.log(id)
      this.axios({
        method: 'GET',
        url:'http://localhost:8080/user/update?id='+id,

      }).then(function (resp) {

        vm.product = resp.data.data
      })
    },
    onSubmit(){

    }
    // onSubmit() {
    //   this.$message('submit!')
    // },
    // onCancel() {
    //   this.$message({
    //     message: 'cancel!',
    //     type: 'warning'
    //   })
    // }
  }
}
</script>

<style scoped>
.line{
  text-align: center;
}
</style>

