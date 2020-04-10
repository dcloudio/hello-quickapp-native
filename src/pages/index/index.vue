<template>
  <view class="content">
    <button class="btn" v-for="item in pages" @click="handleButton(item)">{{item.name}}</button>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        title: 'Hello',
        pages: [{
            name: "button",
            path: "/pages/button/button"
          },
          {
            name: "clipboard",
            path: "/pages/clipboard/clipboard"
          },
          {
            name: "invoke-platform-api",
            path: "/pages/invoke-platform-api/invoke-platform-api"
          }
        ]
      }
    },
    onLoad() {},
    methods: {
      handleButton(e) {
        uni.navigateTo({
          url: e.path
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

  .btn {
    margin-bottom: 15px;
  }
</style>
