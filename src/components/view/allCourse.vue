<template>
  <el-table
    :data="tableData4"
    border
    style="width: 100%"
    :row-class-name="tableRowClassName">
    <el-table-column
      prop="date"
      label="日期">
    </el-table-column>
    <el-table-column
      prop="name"
      label="教师姓名">
    </el-table-column>
    <el-table-column
      prop="province"
      label="学院">
    </el-table-column>
    <el-table-column
      prop="address"
      label="教室">
    </el-table-column>
    <el-table-column
      prop="tag"
      label="标签"
      :filters="[{ text: '已选', value: '已选' }, { text: '未选', value: '未选' }]"
      :filter-method="filterTag">
      <template scope="scope">
        <el-tag
          :type="scope.row.tag === '已选' ? 'primary' : 'success'"
          close-transition>{{scope.row.tag}}</el-tag>
      </template>
    </el-table-column>
    <el-table-column
      label="操作">
      <template scope="scope">
        <el-button
          @click.native.prevent="selectRow(scope.$index, tableData4)"
          type="text"
          size="small">
          选择课程
        </el-button>
      </template>
    </el-table-column>
  </el-table>
</template>
<style scoped>
  .el-table .info-row {
    background: #c9e5f5;
  }

  .el-table .positive-row {
    background: #e2f0e4;
  }
</style>
<script>
  export default {
    methods: {
      selectRow(index, rows) {
        // rows.splice(index, 1);
        console.log(index, rows);
      },
      tableRowClassName(row, index) {
        if (index === 1) {
          return 'info-row';
        } else if (index === 3) {
          return 'positive-row';
        }
          return '';
      },
      filterTag(value, row) {
        return row.tag === value;
      }
    },
    data() {
      return {
        tableData4: [{
          date: '2016-05-03',
          name: '王小虎',
          province: '上海',
          address: '上海市普陀区金沙江路 1518 弄',
          tag: '已选'
        }, {
          date: '2016-05-02',
          name: '王小虎',
          province: '上海',
          address: '上海市普陀区金沙江路 1518 弄',
          tag: '已选'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          province: '上海',
          address: '上海市普陀区金沙江路 1518 弄',
          tag: '已选'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          province: '上海',
          address: '上海市普陀区金沙江路 1518 弄',
          tag: '已选'
        }, {
          date: '2016-05-08',
          name: '王小虎',
          province: '上海',
          address: '上海市普陀区金沙江路 1518 弄',
          tag: '未选'
        }, {
          date: '2016-05-06',
          name: '王小虎',
          province: '上海',
          address: '上海市普陀区金沙江路 1518 弄',
          tag: '未选'
        }, {
          date: '2016-05-07',
          name: '王小虎',
          province: '上海',
          address: '上海市普陀区金沙江路 00 弄',
          tag: '未选'
        }]
      }
    }
  }
</script>