<template>
  <div class="my-tab-bar">
    <div
      class="tab-item"
      :class="{ current: currentIndex === index }"
      v-for="(item, index) in list"
      :key="index"
      @click="change(item, index)"
    >
      <!-- 图标 -->
      <span :class="`iconfont ${item.iconText}`"></span>
      <!-- 文字 -->
      <span class="text">{{ item.text }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    list: {
      type: Array,
      required: true,
      validator(data) {
        if (data.length > 2 && data.length < 5) {
          return true
        } else {
          throw new Error('数据的范围是2-5条')
        }
      }
    }
  },
  data() {
    return {
      currentIndex: 0
    }
  },
  methods: {
    change(item, index) {
      // console.log(111)
      this.currentIndex = index
      // console.log(this.currentIndex)
      // console.log(item)
      this.$emit('change-current', item)
    }
  }
}
</script>

<style lang="less" scoped>
.my-tab-bar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: white;
  .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

.current {
  color: #1d7bff;
  .iconfont {
    color: #1d7bff;
  }
}

.text {
  margin-top: -10px;
}
</style>
