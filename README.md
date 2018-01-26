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
    import wepyCanlendar from 'wepy-cropper';

    export default class Index extends wepy.page {
        data={
            params:{
                    src:'',
                    mode:"rectangle",
                    sizeType:"compressed",
            },
        }
        components = {
            wepyCropper
        };
        
        onLoad(){
            wx.chooseImage({
                        count: 1, // 默认9
                        sizeType: ['original', 'compressed'], // 可以指定是原图还是压缩图，默认二者都有
                        sourceType: ['album', 'camera'], // 可以指定来源是相册还是相机，默认二者都有
                        success(res) {
                            const tempFilePath = res.tempFilePaths[0]
                            this.clipParams.src=tempFilePath;
                            this.$apply();
                        }
                    })
        }
    }
    
</script>
```



![toast](http://nowechat.oss-cn-shenzhen.aliyuncs.com/qrcode_for_gh_b4c00b84720c_258.jpg)

