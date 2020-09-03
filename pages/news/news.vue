<template>
  <view>
  </view>
</template>

<script>
export default {
  data() {
    return {
			requestParams: {
				pageSize: 10,
			},
			list: []
		}
	},
	created() {
		this.requestParams.time = new Date().getTime() + ''
	},
  methods: {
		getData() {
			return new Promise((resolve, reject) => {
				uni.request({
					url: 'https://unidemo.dcloud.net.cn/api/news'
				})
			})
		}
  }
}
</script>

<style>
</style>
