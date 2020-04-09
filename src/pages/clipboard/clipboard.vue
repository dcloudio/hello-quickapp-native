<template>
  <view class="content">
    <view class="uni-list">
      <input class="uni-input" type="text" placeholder="请输入剪贴板内容" :value="data" @change="dataChange"></input>
    </view>
    <view class="uni-btn-v">
      <button class="btn" type="primary" @click="setClipboard">存储数据</button>
      <button class="btn" @click="getClipboard">读取数据</button>
    </view>
    <view>
      <text>{{clipboardValue}}</text>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {
        data: "",
        clipboardValue: ""
      }
    },
    methods: {
      dataChange: function(e) {
        this.data = e.value;
      },
      setClipboard() {
        var data = this.data;
        if (data.length === 0) {
          uni.showModal({
            title: '设置剪贴板失败',
            content: '内容不能为空',
            showCancel: false
          })
          return;
        }
        uni.setClipboardData({
          data: data,
          success: (res) => {
            this.clipboardValue = '设置内容为:' + data;
            console.log("success", res);
          },
          complete: (res) => {
            console.log("complete", res);
          }
        })
      },
      getClipboard() {
        uni.getClipboardData({
          success: (res) => {
            const content = res.data ? '读取内容为:' + res.data : '剪贴板暂无内容';
            this.clipboardValue = content;
          },
          complete: (res) => {
            const content = res.data ? '读取内容为:' + res.data : '剪贴板暂无内容';
            this.clipboardValue = content;
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

  .uni-list {
    margin-bottom: 20px;
  }

  .btn {
    margin-bottom: 15px;
  }
</style>
