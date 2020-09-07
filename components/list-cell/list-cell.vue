<template>
  <div class="content">
    <div
      class="list-cell"
      :class="border"
      @click="eventClick"
      hover-class="cell-hover"
      :hover-stay-time="50"
    >
      <span
        v-if="icon"
        :class="['cell-icon', iconFamily, icon]"
        :style="[{
					color: iconColor,
				}]"
      ></span>
      <span class="cell-title clamp">{{ title }}</span>
      <span v-if="tips" class="cell-tip">{{ tips }}</span>
      <span class="cell-more yticon" :class="typeList[navigateType]"></span>
    </div>
  </div>
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
      }
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
      this.$emit('click')
    }
  }
}
</script>

<style lang='scss'>
@mixin center() {
  display: flex;
  justify-content: center;
  align-items: center;
}

.icon .list-cell.b-b:after {
  left: 90upx;
}

.list-cell {
  position: relative;
  @include center();
  padding: 20upx 30upx;

  &.cell-hover {
    background: #fafafa;
  }

  .cell-icon {
    width: 56upx;
    max-height: 60upx;
    font-size: 38upx;
  }

  .cell-more {
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
