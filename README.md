# 微信小程序 wepyjs 第三方 图片裁剪组件

![toast](https://raw.githubusercontent.com/tomfriwel/welCropper/master/documents/result.gif)


## 说明
我只是一搬运工。搬运于原生小程序图片裁剪组件 [welCropper](https://github.com/tomfriwel/welCropper)



## 使用

### 安装组件
```
npm install wepy-cropper --save
```

### 引入组件
```javascript
// index.wpy
<template>
    <wepyCropper :params.sync="params"></wepyCropper>
</template>
<script>
    import wepy from 'wepy';
    import wepyCropper from 'wepy-cropper';

    export default class Index extends wepy.page {
        data={
            params:{
                    src:'', //字符串, 图片path 必填
                    mode:"rectangle", //选填,默认rectangle
                    /* 两种模式
                    通过的mode设定
                    mode:'rectangle' 返回图片
                    mode:'quadrangle' 并不返回图片，只返回在图片中的四个点，用于perspective correction（可以查找OpenCV相关资料）
                    */
                    sizeType:["compressed"],//数组,选填 ['original', 'compressed'], 默认original
            },
        }
        components = {
            wepyCropper
        };
        
        onLoad(){
            let chooseImage=new Promise((resolve,reject)=>{
                wx.chooseImage({
                    count: 1, // 默认9
                    sizeType: ['original', 'compressed'], // 可以指定是原图还是压缩图，默认二者都有
                    sourceType: ['album', 'camera'], // 可以指定来源是相册还是相机，默认二者都有
                    success(res) {
                        resolve(res.tempFilePaths[0]);
                    }
                })
            })
            chooseImage.then((path)=>{
                this.clipParams.src=tempFilePath;
                this.$apply();
            })
        }
        
        events = {
              //裁剪完的图片
              wepyCropperFinsh(path){
                
              }
            };  // 声明组件之间的事件处理函数
    }
    
</script>
```



![toast](http://nowechat.oss-cn-shenzhen.aliyuncs.com/qrcode_for_gh_b4c00b84720c_258.jpg)

