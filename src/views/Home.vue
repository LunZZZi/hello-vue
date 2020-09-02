<template>
  <div class="home">
    <div>
      <el-button @click="handleAdd">新增</el-button>
    </div>
    <el-table
      :data="tableData"
      style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
        width="180">
        <template slot-scope="scope">
          <span>{{ showDate(scope.row) }}</span>
        </template>
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address"
        label="地址">
      </el-table-column>
      <el-table-column
        label="操作"
        width="100"
      >
        <template slot-scope="scope">
          <el-button @click="handleEdit(scope.row)" type="text" size="small">编辑</el-button>
          <el-popconfirm
            title="这是一段内容确定删除吗？"
            @onConfirm="handleClick(scope.row)"
          >
            <el-button slot="reference" type="text" size="small" style="margin-left: 5px">删除</el-button>
          </el-popconfirm>
        </template>
      </el-table-column>
    </el-table>

    <el-dialog title="收货地址" :visible.sync="dialogFormVisible">
      <el-form :model="form">
        <el-form-item label="姓名" :label-width="formLabelWidth">
          <el-input v-model="form.name" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="地址" :label-width="formLabelWidth">
          <el-input v-model="form.address" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="日期" :label-width="formLabelWidth">
          <el-date-picker v-model="form.date" type="date" />
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button @click="dialogFormVisible = false">取 消</el-button>
        <el-button type="primary" @click="handleDialogConfirm">确 定</el-button>
      </div>
    </el-dialog>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {},
  methods: {
    showDate(row) {
      if (row.date instanceof Date) {
        return row.date.toLocaleDateString()
      } else {
        return row.date;
      }
    },
    handleAdd() {
      this.form = {
        name: '',
        address: '',
        date: ''
      }
      this.dialogFormVisible = true;
      this.currentRow = null;
    },
    handleClick(row) {
      const index = this.tableData.findIndex(x => x.id === row.id)
      this.tableData.splice(index, 1);
    },
    handleEdit(row) {
      this.form = {
        name: row.name || '',
        address: row.address || '',
        date: row.date
      };
      this.currentRow = row;
      this.dialogFormVisible = true;
    },
    handleDialogConfirm() {
      const row = this.currentRow;
      if (row) {
        const index = this.tableData.findIndex(x => x.id === row.id);
        console.log(this.tableData[index]);
        this.tableData[index].name = this.form.name;
        this.tableData[index].address = this.form.address;
        this.tableData[index].date = this.form.date;
      } else {
        this.tableData.push({
          ...this.form
        })
        console.log(this.tableData[this.tableData.length - 1].date)
      }
      this.dialogFormVisible = false;
    }
  },
  data() {
    return {
      tableData: [{
        id: 1,
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        id: 2,
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1517 弄'
      }, {
        id: 3,
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1519 弄'
      }, {
        id: 4,
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1516 弄'
      }],
      form: {
        name: '',
        address: '',
        date: ''
      },
      formLabelWidth: '120px',
      dialogFormVisible: false,
      currentRow: null
    }
  }
}

</script>

<style>
.home {
  padding: 20px;
}
</style>
