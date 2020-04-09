<template>
  <view class="content">
    <button class="btn" @click="handleButton">Button</button>
    <button class="btn" @click="handleClipboard">Clipboard</button>
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
      handleClipboard() {
        uni.navigateTo({
          url: '/pages/clipboard/clipboard'
        });
      },
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
