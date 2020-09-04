<template>
  <div class="details">
    <div class="banner">
      <img :src="item.imageUrl" alt />
      <div class="title-text">{{ this.item.title }}</div>
    </div>
    <div class="article-meta">
      <span>{{ item.source }}</span>
      <span>发表于{{ item.datetime}}</span>
    </div>
		<div class="article-content">
			<rich-text :nodes="content" style="font-size: 14px;"></rich-text>
		</div>
  </div>
</template>

<script>
import htmlParser from '@/common/html-parser'
export default {
  data() {
    return {
			item: {},
			content: []
    }
  },
  onLoad(event) {
    // 获取列表页面传递过来的参数
    this.item = JSON.parse(decodeURIComponent(event.query))
    // 动态设置标题
    uni.setNavigationBarTitle({
      title: this.item.title
		})
		// 获取详情信息
		this.getDetails()
  },
  methods: {
		getDetails() {
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news/36kr/' + this.item.postId,
				success: res => {
					let content = res.data.content
					this.content = htmlParser(content)
				}
			})
		}
	}
}
</script>

<style lang="scss" scoped>
.details {
  .banner {
    position: relative;
    img {
      width: 100%;
      display: block;
    }
    .title-text {
      position: absolute;
      left: 40upx;
      right: 40upx;
      bottom: 40upx;
			color: #fff;
			font-size: 32upx;
			font-weight: 400;
			overflow: hidden;
    }
  }
  .article-meta {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    font-size: 28upx;
		color: gray;
		font-size: 26upx;
		padding: 20upx 30upx;
		span {
			margin-right: 30upx;
		}
	}
	.article-content {
		font-size: 30upx;
		padding: 0 30upx;
		margin-bottom: 30upx;
		overflow: hidden;
	}
}
</style>
