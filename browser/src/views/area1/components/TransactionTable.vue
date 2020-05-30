<template>
  <el-table :data="list" style="width: 100%;padding-top: 15px;">
    <!--<el-table-column label="Order_No" min-width="200">-->
    <el-table-column label="区域" min-width="200">
      <template slot-scope="scope">
        {{ scope.row.order_no | orderNoFilter }}
      </template>
    </el-table-column>
    <!--<el-table-column label="Price" width="195" align="center">-->
    <!--<template slot-scope="scope">-->
    <!--¥{{ scope.row.price | toThousandFilter }}-->
    <!--</template>-->
    <!--</el-table-column>-->
    <!--<el-table-column label="Status" width="100" align="center">-->
    <el-table-column label="状态" width="100" align="center">
      <template slot-scope="{row}">
        <el-tag :type="row.status | statusFilter">
          {{ row.status }}
        </el-tag>
      </template>
    </el-table-column>
  </el-table>
</template>

<script>
import { transactionList } from '@/api/remote-search'

export default {
  filters: {
    statusFilter(status) {
      const statusMap = {
        '正常': 'success',
        '无信号': 'danger'
      }
      return statusMap[status]
    },
    orderNoFilter(str) {
      return str.substring(0, 30)
    }
  },
  data() {
    return {
      list: null
    }
  },
  created() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      transactionList().then(response => {
        // this.list = response.data.items.slice(0, 8)
        this.list = [{
          'order_no': '区域1',
          'status': '正常'
        },
        {
          'order_no': '区域2',
          'status': '无信号'
        },
        {
          'order_no': '区域3',
          'status': '无信号'
        },
        {
          'order_no': '区域4',
          'status': '无信号'
        },
        {
          'order_no': '区域5',
          'status': '无信号'
        }]
      })
    }
  }
}
</script>
