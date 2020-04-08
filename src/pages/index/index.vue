<template>
  <view class="content">
    <button @click="handleButton">Button</button>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        title: 'Hello'
      }
    },
    onLoad() {
    },
    methods: {
      handleButton() {
        uni.navigateTo({
            url: '/pages/button/button'
        });
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

</style>
