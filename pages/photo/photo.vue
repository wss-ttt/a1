<template>
  <view class="wrapper">
    <div v-for="(item, index) in list" :key="index">好好学习 {{ item }}</div>
  </view>
</template>

<script>
export default {
  data() {
    return {
      list: []
    }
  },
  onPullDownRefresh() {
    this.loadData()
  },
  methods: {
    loadData() {
      setTimeout(() => {
        for (let i = 0; i < 5; i++) {
          this.list.unshift(i)
        }
        // 数据请求完成之后停止下拉刷新
        uni.stopPullDownRefresh()
      }, 1000)
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  height: 100%;
  overflow: auto;
  background: #ccc;
}
uni-page-body,
uni-page-refresh {
  height: 100%;
}
</style>
