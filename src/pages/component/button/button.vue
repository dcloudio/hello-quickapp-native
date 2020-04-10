<template>
  <view class="content">
    <button class="button" type="primary">页面主操作 Normal</button>
    <!-- <button class="button" type="primary" :loading="loading">页面主操作 Loading</button> -->
    <button class="button" type="primary" disabled="true">页面主操作 Disabled</button>

    <button class="button" type="default">页面次要操作 Normal</button>
    <button class="button" type="default" disabled="true">页面次要操作 Disabled</button>

    <button class="button" type="warn">警告类操作 Normal</button>
    <button class="button" type="warn" disabled="true">警告类操作 Disabled</button>

    <view class="button-sp-area">
      <button class="button" type="primary" plain="true">按钮</button>
      <button class="button" type="primary" disabled="true" plain="true">不可点击的按钮</button>

      <button class="button" type="default" plain="true">按钮</button>
      <button class="button" type="default" disabled="true" plain="true">按钮</button>
    </view>
    <view class="button-sp-area button-mini-area">
      <button class="mini-btn" type="primary" size="mini">按钮</button>
      <button class="mini-btn" type="default" size="mini">按钮</button>
      <button class="mini-btn" type="warn" size="mini">按钮</button>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        title: 'Hello'
      }
    },
    onLoad() {},
    methods: {

    }
  }
</script>

<style>
  .content {
    padding-left: 30px;
    padding-right: 30px;
    padding-bottom: 40px;
  }

  .button {
    margin-bottom: 30rpx;
  }

  .button-sp-area {
    width: 80%;
    margin: auto;
  }

  .button-mini-area {
    display: flex;
    flex-direction: row;
  }

  .mini-btn {
    margin: 4px;
  }
</style>
