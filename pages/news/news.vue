<template>
  <div class="news">
    <div class="header">
      <div class="title">全部</div>
    </div>
    <div class="item" v-for="(item, index) in record" :key="index">
      <div class="content">
        <div class="title">
          <span class="name">{{ item.name }}</span>
          <span class="state" :class="classType[item.state]">{{ state[item.state] }}</span>
        </div>
        <div class="time-address">
					<p class="time">时间: {{ item.dateTime }}</p>
					<p class="address">地址: {{ item.address }}</p>
				</div>
        <div class="info">
					<p class="service-type">
						业务类型: {{ item.serviceType }}
					</p>
					<p class="ident">
						身份证号: {{ item.IDnumber }}
					</p>
				</div>
      </div>
      <div class="btn-box" v-if="item.state !== 3">
				<template v-if="item.state === 0">
					<span class="cancel">取消预约</span>
				</template>
				<template v-else-if="item.state === 1 || item.state === 4">
					<span class="again">再次预约</span>
				</template>
				<template v-else-if="item.state === 2">
					<span class="again">再次预约</span>
					<span class="evaluate">立即评价</span>
				</template>
			</div>
    </div>
  </div>
</template>

<script>
/**
 *	0. 未赴约 -> 取消预约
 *	1. 爽约  -> 再次预约
 *  2. 已赴约 -> 再次预约 | 立即评价
 *  3. 办理中 -> 不显示
 *  4. 已取消 -> 再次预约
 * **/
export default {
  data() {
    return {
			state: ['未赴约', '爽约', '已赴约', '办理中', '已取消'],
			classType: ['no-appointment', 'break-appointment', 'appointment', 'in-process', 'cancelled'],
      record: [
        {
          name: '西藏昌都市工商行政管理局',
          dateTime: '2018/7/01 11:00~13:00',
          address: '西藏自治区昌都市昌都路4号',
          serviceType: '业务类型一',
          IDnumber: '413980********2541',
          state: 0
        },
        {
          name: '西藏昌都市工商行政管理局',
          dateTime: '2018/7/01 11:00~13:00',
          address: '西藏自治区昌都市昌都路4号',
          serviceType: '业务类型一',
          IDnumber: '413980********2541',
          state: 1
        },
        {
          name: '西藏昌都市工商行政管理局',
          dateTime: '2018/7/01 11:00~13:00',
          address: '西藏自治区昌都市昌都路4号',
          serviceType: '业务类型一',
          IDnumber: '413980********2541',
          state: 2
        },
        {
          name: '西藏昌都市工商行政管理局',
          dateTime: '2018/7/01 11:00~13:00',
          address: '西藏自治区昌都市昌都路4号',
          serviceType: '业务类型一',
          IDnumber: '413980********2541',
          state: 3
        },
        {
          name: '西藏昌都市工商行政管理局',
          dateTime: '2018/7/01 11:00~13:00',
          address: '西藏自治区昌都市昌都路4号',
          serviceType: '业务类型一',
          IDnumber: '413980********2541',
          state: 4
        },
        {
          name: '西藏昌都市工商行政管理局',
          dateTime: '2018/7/05 11:00~13:00',
          address: '西藏自治区昌都市昌都路4号',
          serviceType: '业务类型一',
          IDnumber: '413980********2541',
          state: 2
        },
        {
          name: '西藏昌都市工商行政管理局',
          dateTime: '2018/7/05 11:00~13:00',
          address: '西藏自治区昌都市昌都路4号',
          serviceType: '业务类型一',
          IDnumber: '413980********2541',
          state: 1
        },
        {
          name: '西藏昌都市工商行政管理局',
          dateTime: '2018/7/05 11:00~13:00',
          address: '西藏自治区昌都市昌都路4号',
          serviceType: '业务类型一',
          IDnumber: '413980********2541',
          state: 2
        }
      ]
    }
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
.news {
  padding: 40upx 22upx;
  background: #f6f6f7;
  .header {
    font-size: 38upx;
  }
  .item {
    width: 100%;
    background: #fff;
    box-shadow: 4px 4px 8px #ebecf2;
    margin-top: 15upx;
    .content {
			padding: 38upx 24upx;
      .title {
        display: flex;
        justify-content: space-between;
        span.name {
          font-size: 30upx;
          font-weight: 600;
        }
        span.state {
					font-size: 26upx;
					width: 128upx;
					height: 48upx;
					color: #fff;
					@include center();
					border-top-left-radius: 24upx;
					border-bottom-left-radius: 24upx;
					// 未赴约
					&.no-appointment {
						background-color: #f66767;
					}
					// 爽约
					&.break-appointment {
						background-color: #f4943e;
					}
					// 已赴约
					&.appointment {
						background-color: #3174e9;
					}
					// 办理中
					&.in-process {
						background-color: #b4b4b4;
					}
					// 已取消
					&.cancelled {
						background-color: #18cbcf;
					}
        }
			}
			.time-address {
				font-size: 24upx;
				color: #6e6e6e;
				margin-top: 30upx;
        margin-bottom: 60upx;
				>p.time {
					margin-bottom: 15upx;
				}
			}
			.info {
				font-size: 26upx;
				>p.service-type {
					margin-bottom: 15upx;
				}
			}
    }
		.btn-box {
			border-top: 1px solid #f1f1f1;
			display: flex;
			justify-content: center;
			> span {
				height: 79upx;
				@include center();
				flex: 1;
				text-align: center;
				font-size: 30upx;
				position: relative;
				&.evaluate::before {
					content: '';
					width: 1px;
					height: 48upx;
					background-color: #f1f1f1;
					position: absolute;
					left: 0;
				}
				&.cancel {
					color: #f66767;
				}
				&.again {
					color: #3174e9;
				}
				&.evaluate {
					color: #f4943e;
				}
			}
		}
  }
}
</style>
