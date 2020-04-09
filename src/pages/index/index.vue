<template>
  <view class="content">
    <button class="btn" @click="handleButton">Button</button>
    <button class="btn" @click="handleGetClipboard">Get Clipboard</button>
    <button class="btn" @click="handleSetClipboard">Set Clipboard</button>
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
      handleButton() {
        uni.navigateTo({
          url: '/pages/button/button'
        });
      },
      handleGetClipboard() {
        uni.getClipboardData({
          success: (res) => {
            console.log("success", res);
          },
          complete: (res) => {
            console.log("complete", res);
          }
        })
      },
      handleSetClipboard() {
        uni.setClipboardData({
          data: "test-clipboard",
          success: (res) => {
            console.log("success", res);
          },
          complete: (res) => {
            console.log("complete", res);
          }
        })
      }
    }
  }
</script>

<style>
  .content {
    display: flex;
    flex-direction: column;
    padding: 15px;
  }

  .btn {
    margin-bottom: 15px;
  }
</style>
