<template>
  <view class="content">
    <text class="group-text">组件</text>
    <button class="btn" v-for="item in components" @click="handleButton(item)">{{item.name}}</button>
    <text class="group-text">API</text>
    <button class="btn" v-for="item in apis" @click="handleButton(item)">{{item.name}}</button>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        title: 'Hello',
        components: [{
          name: "button",
          path: "/pages/component/button/button"
        }],
        apis: [{
            name: "request",
            path: "/pages/api/request/request"
          }, {
            name: "clipboard",
            path: "/pages/api/clipboard/clipboard"
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

  .group-text {
    margin: 10px 0;
  }

  .btn {
    margin-bottom: 15px;
  }
</style>
