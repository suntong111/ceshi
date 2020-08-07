<template>
  <div class="app-container">

    <HotTable :root="root" ref="testHot" :settings="hotSettings"></HotTable>
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
  import { HotTable } from '@handsontable/vue';
  export default {
    data: function() {
      return {
        root: '变电站两证及前期手续',
        hotSettings: {
          // data: [['sample', 'data']],
          data: [        //数据可以是二维数组，也可以是数组对象

            // [false,'20080101', 10, 11, 12, 13,true],
            //
            // [false,'20090101', 20, 11, 14, 13,true],
            //
            // [false,'20010101', 30, 15, 12, 13,true],
            //
            // [false,'20010101', 32, 213, 21, 312,true],
            //
            // [false,'20010201', 32, 213, 21, 312,true],
            //
            // [false,'20010301', 32, 213, 21, 312,true],
            //
            // [false,'20010401', 32, 213, 21, 312,true],
            //
            // [false,'20010501', 32, 213, 21, 312,true],
            //
            // [false,'20010601', 32, 213, 21, 312,true]

          ],
          // colHeaders: true,
          startRows: 17,//行列范围

          startCols: 6,

          minRows: 5,  //最小行列

          minCols: 5,

          maxRows: 20,  //最大行列

          maxCols: 20,
          rowHeaders: true,//行表头，可以使布尔值（行序号），可以使字符串（左侧行表头相同显示内容，可以解析html），也可以是数组（左侧行表头单独显示内容）。

          colHeaders:   [ '变电站','前期资料移交', '用地指标报批', '建设用地规划许可证', '土地划拨决定书', '不动产权土地证','建设工程规划许可','建设工程规划许可','建设工程规划许可证','施工设计审图（含清防设计审计图）','施工许可（备案）','消防验收','竣工验收','竣工验收档案归档','不动产证','存在问题','备注'],//自定义列表头or 布尔值
          minSpareCols: 3, //列留白

          minSpareRows: 2,//行留白
          // currentRowClassName: 'currentRow', //为选中行添加类名，可以更改样式
          // currentColClassName: 'currentCol',//为选中列添加类名
          autoWrapRow: true, //自动换行
          contextMenu:{
            items:{
              "row_above": {
                name:'上方插入一行'
              },
              "row_below": {
                name:'下方插入一行'
              },
              "col_left": {
                name:'左方插入列'
              },
              "col_right": {
                name:'右方插入列'
              },
              "hsep1": "---------", //提供分隔线
              "remove_row": {
                name: '删除行',
              },
              "remove_col": {
                name: '删除列',
              },
              "make_read_only": {
                name: '只读',
              },
              "borders":{
                name:'表格线'
              },
              "copy":{
                name:'复制'
              },
              "cut":{
                name:'剪切'
              },
              "commentsAddEdit": {
                name: '添加备注',
              },
              "commentsRemove": {
                name: '取消备注',
              },
              "freeze_column": {
                name: '固定列',
              },
              "unfreeze_column": {
                name: '取消列固定',
              },
              "hsep2": "---------",
            }
          },
          manualColumnFreeze: true, //手动固定列  ?
          manualColumnMove: true, //手动移动列
          manualRowMove: true,   //手动移动行
          manualColumnResize: true,//手工更改列距
          manualRowResize: true,//手动更改行距
          comments: true, //添加注释  ?
          cell: [  //???
            {row: 1, col: 1, comment: {value: 'this is test'}},
          ],
          customBorders:[],//添加边框
          columnSorting: true,//排序
          stretchH: 'all',//根据宽度横向扩展，last:只扩展最后一列，none：默认不扩展
          fillHandle: true, //选中拖拽复制 possible values: true, false, "horizontal", "vertical"
          fixedColumnsLeft: 2,//固定左边列数
          fixedRowsTop: 2,//固定上边列数
          mergeCells: [   //合并
            // {row: 1, col: 1, rowspan: 3, colspan: 3},  //指定合并，从（1,1）开始行3列3合并成一格
            // {row: 3, col: 4, rowspan: 2, colspan: 2}
          ],
          columns: [     //添加每一列的数据类型和一些配置
            // {type: 'checkbox'},  //多选框
            {
              type: 'date',   //时间格式
              dateFormat: 'YYYY-MM-DD',
              correctFormat: true,
              defaultDate: '19000101'
            },
            {
              type: 'dropdown', //下拉选择
              source: ['BMW', 'Chrysler', 'Nissan', 'Suzuki', 'Toyota', 'Volvo'],
              strict: false   //是否严格匹配
            },
            {type: 'numeric'},  //数值
            {type: 'numeric',
              readOnly: true  //设置只读
            },
            { type: 'numeric',
              format: '$ 0,0.00'},  //指定的数据格式
            {},

          ],
        }
      };
    },
    methods:{
      testFunc:function(){
        //this.$refs.hotTable.table就是当前的表格的对象
        console.log(this.$refs.hotTable.table)
      }
    },
    components: {
      HotTable
    }
  }
</script>
<style src="../../../node_modules/handsontable/dist/handsontable.full.css"></style>
<style scoped>
.line{
  text-align: center;
}
</style>

