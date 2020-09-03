<template>
    <div class="news-item">
      <div class="pic">
        <img :src="newsItem.imageUrl" />
      </div>
      <div class="body">
        <div class="title">
          {{ newsItem.title }}
        </div>
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
      return {
          
      }
    },
    computed: {},
    watch: {},
    created() {},
    mounted() {},
    activated() {},
    deactivated() {},
    updated() {},
    destroyed() {},
    methods: {},
    filters: {}
  }
</script>
<style scoped lang="scss">
.news-item {
  display: flex;
  .pic {
    width: 225upx;
    height: 146upx;
    margin-right: 10upx;
    background: #ccc;
    img {
      width: 100%;
      height: 100%;
      display: block;
    }
  }
  .body {
    flex: 1;

  }
}
</style>