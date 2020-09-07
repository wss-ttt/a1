<template>
  <view class="wrapper">
    地址管理
    <button class="add-address">新增地址</button>
  </view>
</template>

<script>
export default {
  data() {
    return {}
  },
  methods: {}
}
</script>

<style lang="scss" scoped>
.wrapper {
	.add-address {
		position: fixed;
		left: 30upx;
		right: 30upx;
		bottom: 16upx;
		z-index: 95;
		display: flex;
		align-items: center;
		justify-content: center;
		width: 690upx;
		height: 80upx;
		font-size: 32upx;
		color: #fff;
		background-color: $uni-color-success;
		border-radius: 10upx;
		box-shadow: 1px 2px 5px rgba(219, 63, 96, 0.4);
	}
}
</style>
