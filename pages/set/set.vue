<template>
  <view class="wrapper">
    <list-cell title="个人资料"></list-cell>
    <list-cell title="收获地址"></list-cell>

    <view class="log-out" @click="logOut">退出登录</view>
  </view>
</template>

<script>
import ListCell from '@/components/list-cell/list-cell'
export default {
  data() {
    return {}
  },
  methods: {
    logOut() {
      uni.showModal({
        content: '确定要退出登录吗',
        success: res => {
          if (res.concfirm) {
            setTimeout(() => {
              uni.navigateBack()
            }, 200)
          }
        }
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  .content {
    background: #fff;
  }
  .log-out {
    margin-top: 40upx;
    font-size: 32upx;
    color: red;
    @include center();
    background: #fff;
    padding: 20upx 0;
  }
}
</style>
