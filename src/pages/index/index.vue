<template>
  <view class="content">
    <text class="group-text">uni 组件</text>
    <button class="btn" v-for="item in components" @click="handleButton(item.path)">{{item.name}}</button>
    <text class="group-text">uni API</text>
    <button class="btn" v-for="item in apis" @click="handleButton(item.path)">{{item.name}}</button>
    <view class="split"></view>
    <text class="group-text">quickapp 组件</text>
    <button class="btn" @click="handleButton('/pages/quickapp-component/image/image')">image</button>
    <text class="group-text">quickapp API</text>
    <button class="btn" @click="handleButton('/pages/quickapp-api/scan-code/scan-code')">Scan Code</button>
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
          },
          {
            name: "clipboard",
            path: "/pages/api/clipboard/clipboard"
          },
          {
            name: "uniCloud",
            path: "/pages/uni-cloud/uni-cloud"
          }
        ]
      }
    },
    methods: {
      handleButton(e) {
        uni.navigateTo({
          url: e
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

  .split {
    height: 50px;
  }
</style>
