<template>
  <view class="page-padding-lr">
    <button @click="handleScan">Scan</button>
    <view>
      <input :value="scanResult" />
    </view>
  </view>
</template>

<script>
  // 注意 manifest 权限配置
  var barcode = $app_require$("@app-module/system.barcode");
  export default {
    data() {
      return {
        scanResult: ""
      }
    },
    methods: {
      handleScan() {
        barcode.scan({
          success: (data) => {
            this.scanResult = data.result;
            console.log(`handling success: ${data.result}`)
          },
          fail: function(data, code) {
            console.log(`handling fail, code = ${code}`)
          }
        })
      }
    }
  }
</script>

<style>

</style>
