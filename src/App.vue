<template>
  <div class="app">
    <MyHeader title="案例-tabbar" background="tomato"></MyHeader>
    <component :is="isShow"></component>
    <MyFooter :list="tabList" @change-current="changeCurrent"></MyFooter>
  </div>
</template>

<script>
import MyHeader from '@/components/MyHeader.vue'
import MyFooter from '@/components/MyFooter.vue'
import MyGoodsList from '@/view/MyGoodsList.vue'
import MyGoodsSearch from '@/view/MyGoodsSearch.vue'
import MyUserInfo from '@/view/MyUserInfo.vue'
export default {
  components: {
    MyHeader,
    MyFooter,
    MyGoodsList,
    MyGoodsSearch,
    MyUserInfo
  },
  data() {
    return {
      tabList: [
        {
          iconText: 'icon-shangpinliebiao',
          text: '商品列表',
          componentName: 'MyGoodsList'
        },
        {
          iconText: 'icon-sousuo',
          text: '商品搜索',
          componentName: 'MyGoodsSearch'
        },
        {
          iconText: 'icon-user',
          text: '我的信息',
          componentName: 'MyUserInfo'
        }
      ],
      isShow: 'MyGoodsList'
    }
  },
  methods: {
    changeCurrent(item) {
      // console.log(item.componentName)
      this.isShow = item.componentName
      // console.log(this.isShow)
    }
  }
}
</script>

<style scoped>
.app {
  padding: 50px 0;
}
</style>
