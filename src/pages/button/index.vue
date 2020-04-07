<template>
  <view class="content">
    <view class="uni-padding">
      <button class="button" type="primary">页面主操作 Normal</button>
      <button class="button" type="primary" :loading="loading">页面主操作 Loading</button>
      <button class="button" type="primary" disabled="true">页面主操作 Disabled</button>

      <button class="button" type="default">页面次要操作 Normal</button>
      <button class="button" type="default" disabled="true">页面次要操作 Disabled</button>

      <button class="button" type="warn">警告类操作 Normal</button>
      <button class="button" type="warn" disabled="true">警告类操作 Disabled</button>

      <view class="button-sp-area1">
        <button type="primary" plain="true">按钮</button>
        <button type="primary" disabled="true" plain="true">不可点击的按钮</button>

        <button type="default" plain="true">按钮</button>
        <button type="default" disabled="true" plain="true">按钮</button>

        <button class="mini-btn" type="primary" size="mini">按钮</button>
        <button class="mini-btn" type="default" size="mini">按钮</button>
        <button class="mini-btn" type="warn" size="mini">按钮</button>
      </view>
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
  .content {}

  .uni-padding {
    padding-left: 15px;
    padding-right: 15px;
  }
</style>
