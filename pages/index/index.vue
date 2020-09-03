<template>
  <div class="home">
    <div class="search-box">
      <div class="left">
        <span class="city">武汉</span>
        <span class="icon"></span>
      </div>
      <input type="text" focus placeholder="搜索" />
    </div>
    <div class="swiper">
      <view class="uni-padding-wrap">
        <view class="page-section swiper">
          <view class="page-section-spacing">
            <swiper class="swiper" :indicator-dots="indicatorDots">
              <swiper-item v-for="(item, index) in swiperList" :key="index">
                <div class="swiper-item">
                  <img :src="item.src" alt />
                </div>
              </swiper-item>
            </swiper>
          </view>
        </view>
      </view>
    </div>
    <div class="outlets">
      <div class="title">预约网点</div>
      <div class="list-item" v-for="(item, index) in list" :key="index">
        <div class="top" :class="classType[item.state]">{{ item.title }}</div>
        <div class="content">
          <p class="name">{{ item.name }}</p>
          <p class="address">
						<span>地址：{{ item.address }}</span>
            <span class="distance">距离：{{ item.distance }}</span>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      indicatorDots: true,
      swiperList: [
        {
          title: '1',
          src: '../../static/images/notice_02.jpg'
        },
        {
          title: '2',
          src: '../../static/images/notice_02.jpg'
        },
        {
          title: '3',
          src: '../../static/images/notice_02.jpg'
        }
			],
			list: [{
				title: '可预约',
				state: 0,
				name: '西藏昌都市工商行政管局',
				address: '西藏自治区昌都市昌都路4号',
				distance: '1.2km'
			}, {
				title: '已满',
				state: 1,
				name: '西藏昌都市工商行政管局',
				address: '西藏自治区昌都市昌都路4号',
				distance: '2.2km'
			}],
			classType: ['reservation', 'no-reservation']
    }
  },
  onLoad() {
	},
  methods: {}
}
</script>

<style lang="scss" scope>
@mixin center {
  display: flex;
  justify-content: center;
  align-items: center;
}
.home {
  .search-box {
    width: 100%;
    height: 100upx;
    padding: 25upx;
    display: flex;
    align-items: center;
    .left {
      display: flex;
      align-items: center;
      margin-right: 40upx;
      .city {
        font-size: 32upx;
        font-weight: 600;
        color: #272727;
      }
      .icon {
        width: 18upx;
        height: 12upx;
        margin-left: 17upx;
        background: url(../../static/images/selectArrow.png) no-repeat;
        background-size: 100% 100%;
      }
    }
    input {
      flex: 1;
      height: 64upx;
      background-color: #f0f0f0;
      border-radius: 32upx;
      font-size: 27upx;
      padding-left: 62upx;
      position: relative;
      &::before {
        content: '';
        position: absolute;
        background-image: url(../../static/images/search.png);
        background-size: 100%;
        width: 30upx;
        height: 30upx;
        left: 25upx;
        top: 50%;
        transform: translateY(-50%);
      }
    }
  }
  .swiper {
    height: 320upx;
    .swiper-item {
      height: 100%;
      img {
        display: block;
        height: 100%;
        width: 100%;
        background-size: cover;
      }
    }
  }
  .outlets {
    padding: 50upx 25upx;
    background: #f9f9f9;
    .title {
      font-size: 34upx;
      font-weight: 700;
    }
    .list-item {
      position: relative;
      margin-top: 25upx;
      padding: 85upx 20upx 50upx;
      background-color: #fff;
      box-shadow: 4px 4px 8px #ebecf2;
      .top {
        position: absolute;
        font-size: 26upx;
        left: 50%;
        transform: translate(-50%, -50%);
        top: 0rpx;
        width: 144upx;
				height: 64upx;
				color: #fff;
        @include center();
        box-shadow: 4px 4px 10px #ebecf2;
        &::after,
        &::before {
          content: '';
          position: absolute;
          width: 0;
          height: 0;
          top: 0;
          z-index: 1;
          border: 10upx solid transparent;
        }
        &::after {
					left: -9px;
        }
        &::before {
					right: -10px;
					transform: rotate(90deg);
				}
				&.reservation {
					background-color: #4381ed;
				}
        &.reservation::before,
        &.reservation::after {
          border-right: 10upx solid #2f5fb1;
          border-bottom: 10upx solid #2f5fb1;
				}
				&.no-reservation {
					background-color: #ed5a55;
				}
				&.no-reservation::before, &.no-reservation::after {
					border-right: 10upx solid #ac2525;
          border-bottom: 10upx solid #ac2525;
				}
      }
      .content {
				>p {
					line-height: 55upx;
				}
        .name {
          font-size: 30upx;
          font-weight: 700;
        }
        .address {
          font-size: 28upx;
          font-weight: 500;
					color: #5a5a5a;
					display: flex;
					justify-content: space-between;
					.distance {
						font-size: 26upx;
            color: #b9b9b9;
					}
        }
      }
    }
  }
}
</style>
