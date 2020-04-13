<template>
  <view class="content">
    <text class="title">uniCloud 基础示例</text>
    <view class="tips">
      <text>1.在cloudfunctions目录右键创建并关联服务空间</text>
      <text>2.在cloudfunctions目录内db_init.json上右键初始化云数据库</text>
      <text>3.在cloudfunctions目录右键选择“上传所有云函数”</text>
      <text>开始愉快的体验uniCloud吧！</text>
    </view>
    <view class="btn-list">
      <button class="btn" type="primary" @click="add">新增一条数据</button>
      <button class="btn" type="primary" @click="remove">删除一条数据</button>
      <button class="btn" type="primary" @click="update">修改数据</button>
      <button class="btn" type="primary" @click="get">查询前10条数据</button>
      <button class="btn" type="primary" @click="useCommon">使用公用模块</button>
      <!-- <button class="btn" type="primary" @click="upload">上传文件</button> -->
    </view>
  </view>
</template>

<script>
  // 以下填写成自己测试云空间的 spaceId clientSecret,目前仅支持 阿里云
  var myUniCloud = uniCloud.init({
    provider: 'aliyun',
    spaceId: '',
    clientSecret: ''
  })

  export default {
    data() {
      return {}
    },
    methods: {
      add() {
        // uni.showLoading({
        // 	title: '处理中...'
        // })
        myUniCloud.callFunction({
          name: 'add',
          data: {
            name: 'DCloud',
            subType: 'uniCloud',
            createTime: Date.now()
          }
        }).then((res) => {
          //uni.hideLoading()
          uni.showModal({
            content: `成功添加一条数据，文档id为：${res.result.id}`,
            showCancel: false
          })
          console.log(res)
        }).catch((err) => {
          //uni.hideLoading()
          uni.showModal({
            content: `添加数据失败，错误信息为：${err.message}`,
            showCancel: false
          })
          console.error(err)
        })
      },
      remove() {
        // uni.showLoading({
        // 	title: '处理中...'
        // })
        myUniCloud.callFunction({
          name: 'remove'
        }).then((res) => {
          //uni.hideLoading()
          uni.showModal({
            content: res.result.msg,
            showCancel: false
          })
          console.log(res)
        }).catch((err) => {
          //uni.hideLoading()
          uni.showModal({
            content: `删除失败，错误信息为：${err.message}`,
            showCancel: false
          })
          console.error(err)
        })
      },
      update() {
        // uni.showLoading({
        // 	title: '处理中...'
        // })
        myUniCloud.callFunction({
          name: 'update',
          data: {
            name: 'DCloud',
            subType: 'html 5+',
            createTime: Date.now()
          }
        }).then((res) => {
          //uni.hideLoading()
          uni.showModal({
            content: res.result.msg,
            showCancel: false
          })
          console.log(res)
        }).catch((err) => {
          //uni.hideLoading()
          uni.showModal({
            content: `更新操作执行失败，错误信息为：${err.message}`,
            showCancel: false
          })
          console.error(err)
        })
      },
      get() {
        // uni.showLoading({
        // 	title: '处理中...'
        // })
        myUniCloud.callFunction({
          name: 'get'
        }).then((res) => {
          //uni.hideLoading()
          uni.showModal({
            content: `查询成功，获取数据列表为：${JSON.stringify(res.result.data)}`,
            showCancel: false
          })
          console.log(res)
        }).catch((err) => {
          //uni.hideLoading()
          uni.showModal({
            content: `查询失败，错误信息为：${err.message}`,
            showCancel: false
          })
          console.error(err)
        })
      },
      useCommon() {
        console.log('请确保自己已经阅读并按照公用模块文档操作 https://uniapp.dcloud.io/uniCloud/cf-common')
        myUniCloud.callFunction({
          name: 'useCommon'
        }).then((res) => {
          //uni.hideLoading()
          uni.showModal({
            content: '云函数useCommon返回结果：' + JSON.stringify(res.result),
            showCancel: false
          })
          console.log(res)
        }).catch((err) => {
          //uni.hideLoading()
          uni.showModal({
            content: `云函数useCommon执行失败，错误信息为：${err.message}`,
            showCancel: false
          })
          console.error(err)
        })
      },
      upload() {
        new Promise((resolve, reject) => {
          uni.chooseImage({
            chooseImage: 1,
            success: res => {
              const path = res.tempFilePaths[0]
              let ext
              // #ifdef H5
              ext = res.tempFiles[0].name.split('.').pop()
              // #endif
              // #ifndef H5
              // 字节跳动小程序ios端选择文件会带query
              ext = res.tempFilePaths[0].split('?')[0].split('.').pop()
              // #endif
              const options = {
                filePath: path,
                cloudPath: Date.now() + '.' + ext
              }
              resolve(options)
            },
            fail: () => {
              reject(new Error('Fail_Cancel'))
            }
          })
        }).then((options) => {
          // uni.showLoading({
          // 	title: '文件上传中...'
          // })
          return myUniCloud.uploadFile({
            ...options,
            onUploadProgress(e) {
              console.log(e)
            }
          })
        }).then(res => {
          uni.hideLoading()
          console.log(res);
          uni.showModal({
            content: '图片上传成功，fileId为：' + res.fileID,
            showCancel: false
          })
        }).catch((err) => {
          uni.hideLoading()
          console.log(err);
          if (err.message !== 'Fail_Cancel') {
            uni.showModal({
              content: `图片上传失败，错误信息为：${err.message}`,
              showCancel: false
            })
          }
        })
      }
    }
  }
</script>

<style>
  .content {
    padding-bottom: 30px;
  }

  .title {
    font-weight: bold;
    text-align: center;
    padding: 20px 0px;
    font-size: 30px;
  }

  .tips {
    color: #999999;
    font-size: 14px;
    padding: 20px 30px;
  }

  .btn-list {
    padding: 0px 30px;
  }

  .btn-list .btn {
    margin-bottom: 20px;
  }

  .upload-preview {
    width: 100%;
  }
</style>
