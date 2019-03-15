#### element ui 前端静态数据表格分页
1. 当导入element ui库后，获取到所有数据，使用表格显示，并进行分页

html代码

```
<template>
  <div>
    <el-table :data="tableData.slice((currentPage-1)*pageSize,currentPage*pageSize)" style="width: 100%">
      <el-table-column v-for="item in tableHeader" :key="item.key" :prop="item.key" :label="item.name" show-overflow-tooltip=true>
      </el-table-column>
    </el-table>
    <el-pagination :current-page.sync="currentPage" :page-size="pageSize" layout="total, prev, pager, next,jumper"
       :total="tableData.length">
    </el-pagination>
  </div>
</template>
```
 js代码

```angular2html
<script>
export default {
  name: 'field-demo',
  data () {
    return {
      tableHeader: [{
        name: '姓名',
        key: 'name'
      }, {
        name: '性别',
        key: 'gender'
      }, {
        name: '年龄',
        key: 'age'
      }, {
        name: '地址',
        key: 'address'
      }],
      tableData: [{
        name: '小明1',
        gender: '男',
        age: 20,
        address: '深圳'
      }, {
        name: '小明2',
        gender: '女',
        age: 30,
        address: '上海'
      }, {
        name: '小明3',
        gender: '男',
        age: 22,
        address: '北京'
      }, {
        name: '小张1',
        gender: '女',
        age: 20,
        address: '深圳'
      }, {
        name: '小王',
        gender: '男',
        age: 25,
        address: '深圳'
      }, {
        name: '小李',
        gender: '女男',
        age: 20,
        address: '深圳'
      }],
      pageSize: 5,
      currentPage: 1
    }
  }
}
</script>
```

