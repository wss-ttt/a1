<template>
  <view class="wrapper">
    <div class="item" v-for="(item, index) in list" :key="index">姓名: {{ item }}</div>
    <div v-if="!list.length" class="no-data">请求中...</div>
    <div v-if="list.length" class="load-more">加载更多...</div>
  </view>
</template>

<script>
export default {
  data() {
    return {
      list: []
    }
  },
  mounted() {
    this.loadData()
  },
  onPullDownRefresh() {
    this.loadData()
  },
  onReachBottom() {
    this.loadData()
  },
  methods: {
    loadData(time) {
      setTimeout(() => {
        for (let i = 0; i < 5; i++) {
          this.list.push(i)
        }
        // 数据请求完成之后停止下拉刷新
        uni.stopPullDownRefresh()
      }, time || 1000)
    }
  }
}
</script>

<style lang="scss" scoped>
@mixin center {
  display: flex;
  justify-content: center;
  align-items: center;
}
.wrapper {
  .item {
    height: 300upx;
    @include center;
    border: 1px solid #ccc;
    margin-bottom: 10upx;
  }
  .no-data {
    @include center;
  }
  .load-more {
    height: 80upx;
    @include center;
  }
}
</style>
