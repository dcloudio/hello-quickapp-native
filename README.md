# test-quickapp-native
快应用测试工程

1. 安装 [快应用调试器](https://statres.quickapp.cn/quickapp/quickapp/201806/file/quickapp_debugger.apk)

2. 打开快应用调试器，下载平台（快应用预览版：版本号1060）

3. yarn install

4. 编译快应用 `rpk`
```
npm run dev:quickapp-native
```
5. 开启debug在线更新服务
```
npm run serve:quickapp-native
```

6. 打开快应用调试器，扫码安装或右上角设置服务器地址(注意带上`http://`，关闭USB调试可看到扫码)
- 修改代码后，会主动通知调试器更新，或者手动点击在线更新（调试可以点击右下角开始调试）
