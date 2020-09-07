<template>
  <div class="wrapper">
    <div class="header">
			<div class="pic" @click="toLoginPage">
    	  <img src="../../static/images/pic_person@2x_s1.png" alt />
				<p class="txt">登录/注册</p>
			</div>
    </div>
    <div class="body">
			<list-cell v-for="(item, index) in listCell" :key="index" :icon="item.icon" :icon-color="item.iconColor" :title="item.title" @click="goLink(item.url)"></list-cell>
		</div>
  </div>
</template>

<script>
import ListCell from '@/components/list-cell/list-cell';
export default {
	components: {
		ListCell
	},
  data() {
    return {
			listCell: [{
				icon: 'icon-iconfontweixin',
				iconColor: '#e07472',
				title: '成长值',
				url: '/pages/point/point'
			}, {
				icon: 'icon-dizhi',
				iconColor: '#5fcda2',
				title: '地址管理',
				url: '/pages/address/address'
			}, {
				icon: 'icon-shezhi1',
				iconColor: '#9789f7',
				title: '个人设置',
				url: '/pages/set/set'
			}]
		}
  },
  methods: {
		goLink(url) {
			uni.navigateTo({
				url: url
			})
		},
		// 跳转到login页面
		toLoginPage() {
			uni.navigateTo({
				url: '/pages/login/login'
			})
		}
	}
}
</script>

<style lang="scss" scope>
@mixin center {
	display: flex;
	align-items: center;
	justify-content: center;
}
.wrapper {
	background: #f6f6f7;
  .header {
    height: 292upx;
    background: #5188e9;
    background: url(../../static/images/person-x2_01.jpg) no-repeat;
		background-size: 100%;
		@include center();
		.pic {
			img {
				width: 160upx;
				height: 160upx;
				border-radius: 50%;
			}
			.txt {
				color: #fff;
				font-size: 28upx;
				text-align: center;
			}
		}
  }
  .body {
  }
}
</style>
