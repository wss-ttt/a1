<script>
export default {
  onLaunch: function() {
    console.log('App Launch')
  },
  onShow: function() {
    console.log('App Show')
  },
  onHide: function() {
    console.log('App Hide')
  }
}
</script>

<style lang="scss">
/*每个页面公共css */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
	background: #f1f1f1; // 全局设置背景色
}
/*边框*/
.b-b:after,
.b-t:after {
	position: absolute;
	z-index: 3;
	left: 0;
	right: 0;
	height: 0;
	content: '';
	transform: scaleY(0.5);
	border-bottom: 1px solid $border-color-base;
}

.b-b:after {
	bottom: 0;
}

.b-t:after {
	top: 0;
}

/*
		全局公共样式和字体图标
	*/
@font-face {
  font-family: 'yticon';
  font-weight: normal;
  font-style: normal;
  src: url('https://at.alicdn.com/t/font_1078604_w4kpxh0rafi.ttf')
    format('truetype');
}

@mixin clear() {
  &::after {
    content: '';
    display: block;
    clear: both;
  }
}

@font-face {
  font-family: 'wkicon';
  font-weight: normal;
  font-style: normal;
  src: url('https://at.alicdn.com/t/font_1504256_e04hhrjt0i.ttf')
    format('truetype');
}

.icon-daishouhuo:before {
  content: '\e604';
}

.icon-daipingjia:before {
  content: '\e630';
}

.icon-daifahuo:before {
  content: '\e708';
}

.icon-yaoqing:before {
  content: '\e60d';
}

.icon-ad:before {
  content: '\e645';
}

.icon-dingzhi:before {
  content: '\e91b';
}

.icon-shouji:before {
  content: '\e605';
}

.icon-more:before {
  content: '\e86d';
}
.icon-zan:before {
  content: '\e606';
}
.icon-chaping:before {
  content: '\e701';
}
.icon-kefu:before {
  content: '\e621';
}
.__space {
  margin-top: 20rpx !important;
}
.yticon {
  font-family: 'yticon' !important;
  font-size: 16px;
  font-style: normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.icon-yiguoqi1:before {
  content: '\e700';
}

.icon-iconfontshanchu1:before {
  content: '\e619';
}

.icon-iconfontweixin:before {
  content: '\e611';
}

.icon-alipay:before {
  content: '\e636';
}

.icon-shang:before {
  content: '\e624';
}

.icon-shouye:before {
  content: '\e626';
}

.icon-shanchu4:before {
  content: '\e622';
}

.icon-xiaoxi:before {
  content: '\e618';
}

.icon-jiantour-copy:before {
  content: '\e600';
}

.icon-fenxiang2:before {
  content: '\e61e';
}

.icon-pingjia:before {
  content: '\e67b';
}

.icon-daifukuan:before {
  content: '\e68f';
}

.icon-pinglun-copy:before {
  content: '\e612';
}

.icon-dianhua-copy:before {
  content: '\e621';
}

.icon-shoucang:before {
  content: '\e645';
}

.icon-xuanzhong2:before {
  content: '\e62f';
}

.icon-gouwuche_:before {
  content: '\e630';
}

.icon-icon-test:before {
  content: '\e60c';
}

.icon-icon-test1:before {
  content: '\e632';
}

.icon-bianji:before {
  content: '\e646';
}

.icon-jiazailoading-A:before {
  content: '\e8fc';
}

.icon-zuoshang:before {
  content: '\e613';
}

.icon-jia2:before {
  content: '\e60a';
}

.icon-huifu:before {
  content: '\e68b';
}

.icon-sousuo:before {
  content: '\e7ce';
}

.icon-arrow-fine-up:before {
  content: '\e601';
}

.icon-hot:before {
  content: '\e60e';
}

.icon-lishijilu:before {
  content: '\e6b9';
}

.icon-zhengxinchaxun-zhifubaoceping-:before {
  content: '\e616';
}

.icon-naozhong:before {
  content: '\e64a';
}

.icon-xiatubiao--copy:before {
  content: '\e608';
}

.icon-shoucang_xuanzhongzhuangtai:before {
  content: '\e6a9';
}

.icon-jia1:before {
  content: '\e61c';
}

.icon-bangzhu1:before {
  content: '\e63d';
}

.icon-arrow-left-bottom:before {
  content: '\e602';
}

.icon-arrow-right-bottom:before {
  content: '\e603';
}

.icon-arrow-left-top:before {
  content: '\e604';
}

.icon-icon--:before {
  content: '\e744';
}

.icon-zuojiantou-up:before {
  content: '\e605';
}

.icon-xia:before {
  content: '\e62d';
}

.icon--jianhao:before {
  content: '\e60b';
}

.icon-weixinzhifu:before {
  content: '\e61a';
}

.icon-comment:before {
  content: '\e64f';
}

.icon-weixin:before {
  content: '\e61f';
}

.icon-fenlei1:before {
  content: '\e620';
}

.icon-erjiye-yucunkuan:before {
  content: '\e623';
}

.icon-Group-:before {
  content: '\e688';
}

.icon-you:before {
  content: '\e606';
}

.icon-forward:before {
  content: '\e607';
}

.icon-tuijian:before {
  content: '\e610';
}

.icon-bangzhu:before {
  content: '\e679';
}

.icon-share:before {
  content: '\e656';
}

.icon-yiguoqi:before {
  content: '\e997';
}

.icon-shezhi1:before {
  content: '\e61d';
}

.icon-fork:before {
  content: '\e61b';
}

.icon-kafei:before {
  content: '\e66a';
}

.icon-iLinkapp-:before {
  content: '\e654';
}

.icon-saomiao:before {
  content: '\e60d';
}

.icon-shezhi:before {
  content: '\e60f';
}

.icon-shouhoutuikuan:before {
  content: '\e631';
}

.icon-gouwuche:before {
  content: '\e609';
}

.icon-dizhi:before {
  content: '\e614';
}

.icon-fenlei:before {
  content: '\e706';
}

.icon-xingxing:before {
  content: '\e70b';
}

.icon-tuandui:before {
  content: '\e633';
}

.icon-zuanshi:before {
  content: '\e615';
}

.icon-zuo:before {
  content: '\e63c';
}

.icon-shoucang2:before {
  content: '\e62e';
}

.icon-shouhuodizhi:before {
  content: '\e712';
}

.icon-yishouhuo:before {
  content: '\e71a';
}

.icon-dianzan-ash:before {
  content: '\e617';
}
</style>
