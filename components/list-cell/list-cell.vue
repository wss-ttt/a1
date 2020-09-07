<template>
	<view class="content">
		<view class="mix-list-cell" :class="border" @click="eventClick" hover-class="cell-hover" :hover-stay-time="50">
			<text v-if="icon" :class="['cell-icon', iconFamily, icon]" :style="[{
					color: iconColor,
				}]"></text>
			<text class="cell-title clamp">{{ title }}</text>
			<text v-if="tips" class="cell-tip">{{ tips }}</text>
			<text class="cell-more yticon" :class="typeList[navigateType]"></text>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				typeList: {
					left: 'icon-zuo',
					right: 'icon-you',
					up: 'icon-shang',
					down: 'icon-xia'
				},
			}
		},
		props: {
			icon: {
				type: String,
				default: ''
			},
			title: {
				type: String,
				default: '标题'
			},
			tips: {
				type: String,
				default: ''
			},
			navigateType: {
				type: String,
				default: 'right'
			},
			border: {
				type: String,
				default: 'b-b'
			},
			hoverClass: {
				type: String,
				default: 'cell-hover'
			},
			iconColor: {
				type: String,
				default: '#333'
			},
			iconFamily: {
				type: String,
				default: 'yticon'
			}
		},
		methods: {
			eventClick() {
				this.$emit('eventClick');
			}
		},
	}
</script>

<style lang='scss'>
	.icon .mix-list-cell.b-b:after {
		left: 90upx;
	}

	.mix-list-cell {
		display: flex;
		align-items: center;
		padding: 20upx 30upx;
		line-height: 60upx;
		position: relative;

		&.cell-hover {
			background: #fafafa;
		}

		&.b-b:after {
			left: 30upx;
		}

		.cell-icon {
			align-self: center;
			width: 56upx;
			max-height: 60upx;
			font-size: 38upx;
		}

		.cell-more {
			align-self: center;
			font-size: 30upx;
			margin-left: 2oupx;
			color: #505050;
		}

		.cell-title {
			flex: 1;
			font-size: 28upx;
			color: #303133;
			margin-right: 10upx;
		}

		.cell-tip {
			font-size: 24upx;
			color: #505050;
		}
	}
</style>
