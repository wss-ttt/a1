<template>
  <div class="wrapper">
    <news-item :newsItem="item" v-for="(item, index) in list" :key="index" class="item" @close="close(index)"></news-item>
		<div v-if="!list.length" class="no-data">请求中...</div>
    <div v-if="list.length" class="load-more">加载更多...</div>
  </div>
</template>

<script>
import NewsItem from './news-item.vue'
import { friendlyDate } from '@/common/util.js'
export default {
  components: {
    NewsItem
  },
  data() {
    return {
      requestParams: {
				columnId: undefined,
				minId: undefined,
        pageSize: 10
      },
      list: []
    }
  },
  async created() {
    this.requestParams.time = new Date().getTime() + ''
    this.list = await this.getData()
	},
	async onReachBottom() {
		let res = await this.getData()
		this.list = this.list.concat(res)
		
	},
  methods: {
    getData() {
      return new Promise((resolve, reject) => {
        uni.request({
          url: 'https://unidemo.dcloud.net.cn/api/news',
          data: this.requestParams,
          success: res => {
						this.requestParams.minId = res.data[res.data.length - 1].id
            // 处理数据
            let data = res.data.map(news => {
              return {
                id: this.newGuid() + news.id,
                newsid: news.id,
                article_type: 1,
                datetime: friendlyDate(
                  new Date(news.published_at.replace(/\-/g, '/')).getTime()
                ),
                title: news.title,
                imageUrl: news.cover,
                source: news.author_name,
								commentCount: news.comments_count,
                postId: news.post_id
              }
            })
            resolve(data)
          }
        })
      })
    },
    newGuid() {
      let s4 = function() {
        return ((65536 * (1 + Math.random())) | 0).toString(16).substring(1)
      }
      return (
        s4() +
        s4() +
        '-' +
        s4() +
        '-4' +
        s4().substr(0, 3) +
        '-' +
        s4() +
        '-' +
        s4() +
        s4() +
        s4()
      ).toUpperCase()
		},
		close(index) {
			uni.showModal({
				content: '不感兴趣',
				success: res => {
					if(res.confirm) {
						// 删除数据
						this.list.splice(index, 1)
					}
				}
			})
		}
  }
}
</script>

<style scoped lang="scss">
@mixin center {
  display: flex;
  justify-content: center;
  align-items: center;
}
.wrapper {
  padding: 15upx;
  .item {
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
