# 麦芒-阅读统计

## 1.综述      
我们搭建自己的博客、或者个人网站，往往需要统计服务。统计服务分为两种，一种是类似百度、友盟的统计，可以根据数据来看 PV/UV 或者人群画像。但是有时候也需要展示每一篇文章的阅读数给“读者”看。麦芒的阅读统计服务是服务后者的。效果如下：  

![image.png](https://cdn.nlark.com/yuque/0/2020/png/362990/1588676881425-5fdc540e-216a-4112-bcad-c7fe6b1c2931.png#align=left&display=inline&height=157&margin=%5Bobject%20Object%5D&name=image.png&originHeight=314&originWidth=1118&size=106460&status=done&style=none&width=559)
使用服务很简单，直接拷贝代码的形式，或者请求接口形式都可以。目前提供两种服务：

- 单篇文章阅读统计
- 所有文章阅读累计



## 2.单篇文章阅读统计             
**第1步：将数字需要显示的位置确定好**      
```html
<span id="serverless80_read_count"></span>
```
**第2步：拷贝下面代码到需要统计的页面**
```javascript
<script type="text/javascript" src="https://dxzd-js-css.oss-cn-hangzhou.aliyuncs.com/zepto.min.js"></script>
<script type="text/javascript">
  (function(){
    var url = 'https://api.serverless80.com/read_count?host=' + encodeURIComponent(location.host) + '&path=' + encodeURIComponent(location.pathname)
    $.get(url, function(res){
      $('#serverless80_read_count').text(res.count)
    })
  })()
</script>
```


## 3.所有文章阅读累计    
**第1步：将数字需要显示的位置确定好**
```html
<span id="serverless80_read_count_tj"></span>
```
**第2步：拷贝下面代码到需要统计的页面**
```javascript
<script type="text/javascript">
    (function(){
      var url = 'https://api.serverless80.com/read_count_tj?host=' + encodeURIComponent(location.host)
      $.get(url, function(res){
        $('#serverless80_read_count_tj').text(res.total_count)
      })
    })()
  </script>
```
## 4.自定义
该服务提供2个接口，可以根据情况自行适配    

**4.1 单篇文章阅读统计**       
接口：[https://api.serverless80.com/read_count](https://api.serverless80.com/read_count)        
输入参数：host（一般为被统计的页面域名）、path（文章的路径）

**4.2 所有文章阅读累计**         
接口：[https://api.serverless80.com/read_count_tj](https://api.serverless80.com/read_count_tj)        
输入参数：host（一般为被统计的页面域名）

## 问题反馈 
**关注 **[**https://github.com/serverless80/tongji**](https://github.com/serverless80/tongji)** 项目并提 issues.**
