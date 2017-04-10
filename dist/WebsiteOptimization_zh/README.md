# 网站性能优化项目

##知识体系
网站性能优化课程相关内容
1、优化关键渲染路径
2、浏览器渲染优化
## 优化目标
1、index.html 在移动设备和桌面上的 PageSpeed 分数至少为90分。
2、views/pizza.html 在滚动时保持 60fps 的帧速。
3、views/pizza.html 页面上的 pizza 尺寸滑块调整 pizza 大小的时间小于5毫秒。

## 优化步骤
### index.html
1、print.css 使用媒体查询
2、外部字体，font.css下载到本地
3、perfmatters.js 使用异步加载，并放到body的最下面
4、把无用的第三方js删除
5、压缩了css文件
6、使用PS压缩图片大小，并使用PageSpeed提供的压缩无损的图片
7、使用http缓存Cache-Control
### pizza.html
1、html、css、js文件压缩
2、main.js
   2.1 updatePositions() 方法中 把document.body.scrollTop / 1250 提到for循环外，去除了强制同步布局
   2.2 updatePositions() 把取模运算去掉了，因对计算影响不大，把parse * 100，提到上一行，计算样式时，只考虑加法
   2.3 changePizzaSizes(size) 方法中 修改了冗余代码，简化方法
   2.4 pizzaElementGenerator ()方法中，pizzaImage 添加了属性 width = 100%，为了适应压缩后的图片
   2.5 初始化页面，生成披萨滑窗时，会出现强制同步布局，将计算图片left的方法放到前面，就不用去调用updatePositions
   
   3、压缩图片
4、http缓存Cache-Control  
## 优化效果
1、index.html 在PageSpeed 中的分数为96分
2、pizza.html 滚动时，帧率有一半在60fps,但不是全部
3、pizza.html 切换pizza大小，时间控制在2ms之内
## 优化提升
1、希望再改进 updatePositions方法，使滚动帧率都在60fps。