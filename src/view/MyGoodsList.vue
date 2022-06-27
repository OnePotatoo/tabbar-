<template>
  <table class="table table-bordered table-stripped">
    <!-- 表格标题区域 -->
    <thead>
      <tr>
        <th>#</th>
        <th>商品名称</th>
        <th>价格</th>
        <th>标签</th>
        <th>操作</th>
      </tr>
    </thead>
    <!-- 表格主体区域 -->
    <tbody>
      <tr v-for="item in list" :key="item.id">
        <td>{{ item.id }}</td>
        <td>{{ item.goods_name }}</td>
        <td>{{ item.goods_price }}</td>
        <td><span class="badge bg-warning text-dark">徽章</span></td>
        <td>
          <button class="btn btn-danger btn-sm" @click="del(item.id)">
            删除
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import axios from '@/utils/request.js'
export default {
  name: 'MyTable',
  data() {
    return {
      list: []
    }
  },
  created() {
    this.getlist()
  },
  methods: {
    async getlist() {
      // const data = await axios({ url: '/api/goods' })
      // console.log(data)
      const { data } = await axios({ url: '/api/goods' })
      this.list = data.data
      // console.log(this.list)
    },
    del(id) {
      this.list = this.list.filter((item) => item.id !== id)
    }
  }
}
</script>

<style scoped lang="less">
.my-goods-list {
  .badge {
    margin-right: 5px;
  }
}
</style>
