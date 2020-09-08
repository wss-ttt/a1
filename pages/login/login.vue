<template>
  <div class="wrapper">
    <view class="uni-common-mt">
      <view class="uni-form-item uni-column">
        <view class="title">可自动聚焦的input</view>
        <input class="uni-input" focus placeholder="自动获得焦点" />
      </view>
      <view class="uni-form-item uni-column">
        <view class="title">键盘右下角按钮显示为搜索</view>
        <input class="uni-input" confirm-type="search" placeholder="键盘右下角按钮显示为搜索" />
      </view>
    </view>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      title: 'input',
      focus: false,
      inputValue: '',
      changeValue: ''
    }
  },
  methods: {
    onKeyInput: function(event) {
      this.inputValue = event.target.value
    },
    replaceInput: function(event) {
      var value = event.target.value
      if (value === '11') {
        this.changeValue = '2'
      }
    },
    hideKeyboard: function(event) {
      if (event.target.value === '123') {
        uni.hideKeyboard()
      }
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
