# 微信小程序 wepyjs 第三方 日历组件

![toast](http://nowechat.oss-cn-shenzhen.aliyuncs.com/TIM%E5%9B%BE%E7%89%8720180116113203.png)


## 说明
实现方法网上找的，代码比较烂，别介意，第一次写npm模块。我只是一搬运工。
基本实现功能：
1. 日历显示
2. 选择时间
3. 打卡日期


## 使用

### 安装组件
```
npm install wepy-calendar --save
```

### 引入组件
```javascript
// index.wpy
<template>
    <wepyCanlendar></wepyCanlendar>
</template>
<script>
    import wepy from 'wepy';
    import wepyCanlendar from 'wepy-calendar';

    export default class Index extends wepy.page {
        components = {
            wepyCanlendar
        };
    }
    
</script>
```

### 自定义参数
```javascript
// index.wpy
<template>
    <wepyCanlendar 
        :currentDate.sync="currentDate"//日历当前时间
        :startDate.sync="startDate"//日历选择器picker的最小时间
        :endDate.sync="endDate"//日历选择器picker的最大时间
        :hasIconList.sync="hasIconList"//打卡天数数组
    ></wepyCanlendar>
</template>
<script>
    import wepy from 'wepy';
    import wepyCanlendar from 'wepy-calendar';

    export default class Index extends wepy.page {
        components = {
            wepyCanlendar
        };
        
        onLoad(){
            this.$broadcast("startRenderCalendar");//通知日历组件可以开始渲染
        }
        
        data = {
              currentDate:"2017-08-09",
              startDate:'2017-01-01',
              endDate:'2018-02-01',
              hasIconList:[1,2,3,4,10,12,14]
        };  // 页面所需数据均需在这里声明，可用于模板数据绑定
        
        events = {
              calChangeCurrentDate:function (date,e) {
                 //日历当前时间改变回调
              },
              calChangeSelectedDay:function (date,e) {
                //点击日历选择天回调
              }
            };  // 声明组件之间的事件处理函数
    }
    
</script>
```




| 属性/方法   | 必填    |  默认值  |备注|
| --------   | -----   | ---- |---- |
| currentDate | 否      |   new Date() |日历当前时间|
| startDate    否      |   null    |日历时间选择picker最小时间|
| endDate    | 否      |   null    |日历时间选择picker最大时间|
| hasIconList  | 否      |   []    |日历打入天数组|
| calChangeCurrentDate  | 否      |   (date,e)    |日历当前时间改变回调
| calChangeSelectedDay  | 否      |   (date,e)    |声明组件之间的事件处理函数
| this.$broadcast("startRenderCalendar");  | 是      |   ‘’    |通知组件可以开始渲染

![toast](http://nowechat.oss-cn-shenzhen.aliyuncs.com/qrcode_for_gh_b4c00b84720c_258.jpg)

