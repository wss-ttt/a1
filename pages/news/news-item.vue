<template>
  <div class="news-item" @click="click">
    <div class="content">
      <div class="pic">
        <img :src="newsItem.imageUrl" />
      </div>
      <div class="body">
        <div class="title">{{ newsItem.title }}</div>
      </div>
    </div>
    <div class="footer-info">
      <span>{{newsItem.source}}</span>
      <span>{{newsItem.commentCount}}条评论</span>
      <span>{{newsItem.datetime}}</span>
      <span class="close" @click.stop="close">&times;</span>
    </div>
  </div>
</template>

<script>
export default {
  components: {},
  props: {
    newsItem: {
      type: Object,
      default: () => {
        return {}
      }
    }
  },
  data() {
    return {}
  },
  computed: {},
  watch: {},
  created() {},
  mounted() {},
  activated() {},
  deactivated() {},
  updated() {},
  destroyed() {},
  methods: {
    click() {
      this.$emit('click')
    },
    close() {
      this.$emit('close')
    }
  },
  filters: {}
}
</script>
<style scoped lang="scss">
@mixin center {
  display: flex;
  justify-content: center;
  align-items: center;
}
.news-item {
  padding: 20upx 30upx 20upx 30upx;
  position: relative;
  &::before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 30upx;
    right: 30upx;
    height: 1px ;
    background: #ebebeb;
  }
  .content {
    display: flex;
    .pic {
      width: 225upx;
      height: 146upx;
      margin-right: 15upx;
      background: #ccc;
      img {
        width: 100%;
        height: 100%;
        display: block;
      }
    }
    .body {
      flex: 1;
      .title {
        color: #555;
        font-size: 30upx;
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
        font-weight: 700;
      }
    }
  }
  .footer-info {
    display: flex;
    align-items: center;
    padding: 10upx 0;
    span {
      color: #999;
      font-size: 24upx;
      margin-right: 20upx;
    }
    .close {
      margin-left: auto;
      width: 40upx;
      height: 30upx;
      border: 1px solid #aaa;
      @include center();
      border-radius: 4px;
    }
  }
}
</style>