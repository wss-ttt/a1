<template>
  <div class="wrapper">
    <div class="item" v-for="(item, index) in list" :key="index">
      <news-item :newsItem="item"></news-item>
    </div>
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
        pageSize: 10
      },
      list: []
    }
  },
  async created() {
    this.requestParams.time = new Date().getTime() + ''
    this.list = await this.getData()
    console.log(this.list)
  },
  methods: {
    getData() {
      return new Promise((resolve, reject) => {
        uni.request({
          url: 'https://unidemo.dcloud.net.cn/api/news',
          data: this.requestParams,
          success: res => {
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
    }
  }
}
</script>

<style scoped lang="scss">
.item {
	margin-bottom: 10upx;
}
</style>
