<template>
  <div class="Msite">
    <el-menu
      :default-active="activeIndex2"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b"
    >
      <el-menu-item index="1" class="workbench">工作台</el-menu-item>
      <el-menu-item class="menu-manage">菜单管理</el-menu-item>
      <el-submenu index="2" class="order-manage">
        <div slot="title" class="title">订单管理</div>
        <el-menu-item index="2-1">用户评价</el-menu-item>
        <el-menu-item index="2-2">交易记录</el-menu-item>
        <el-menu-item index="2-3">选项3</el-menu-item>
        <el-submenu index="2-4">
          <template slot="title">选项4</template>
          <el-menu-item index="2-4-1">选项1</el-menu-item>
          <el-menu-item index="2-4-2">选项2</el-menu-item>
          <el-menu-item index="2-4-3">选项3</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="3" class="message" disabled>消息中心</el-menu-item>
    </el-menu>
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="date" label="日期" width="180"> </el-table-column>
      <el-table-column prop="name" label="食物" width="180" > </el-table-column>
      <el-table-column prop="address" label="数量" > </el-table-column>
      <el-table-column prop="pay" label="支付"> </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  mounted () {
    this.axios.get('/admins/orders?shop_name=' + this.shop_name).then((res) => {
      console.log(res.data)
      this.tableData.name = 123
      this.tableData.address = res.data[0].count
      // console.log(this.tableData)
    })
  },
  data () {
    return {
      activeIndex: '1',
      activeIndex2: '1',
      tableData: [
        {
          date: '2016-05-02',
          name: '',
          address: '',
          pay: ''
        }
      ],
      shop_name: '板烧厨房'
    }
  },
  methods: {
    handleSelect (key, keyPath) {
      console.log(key, keyPath)
    }
  }
}
</script>

<style lang="scss" scoped>
.Msite {
  .el-menu-demo {
    height: 80px;
    text-align: center;
    display: flex;
    align-items: center;
    .workbench {
      font-size: 20px;
    }
    .menu-manage {
      font-size: 20px;
    }
    .order-manage {
      .title {
        font-size: 20px;
      }
    }
    .message {
      font-size: 20px;
    }
  }
}
</style>
