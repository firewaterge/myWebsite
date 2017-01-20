#前端部分
###概述：
**目录栏（左）**：
+ 排列文章标题与发布日期
+ 鼠标悬于文章上时右侧图形框对应的标签会改变颜色  
---

**图形框（右）**：
+ 使用js运算使其时刻居中
+ 选择图形框中的标签时，目录栏中文章会过滤  
+ 标签均为圆代替  
+ 每次更新文章时会生成新的图形，各个标签（圆）的大小由该标签下文章数量决定  

###接口：由后端传递json文件，获取目录栏文章列表，图形框标签分布及大小  

##Layer：
整个canvas图像  

####属性: 
+ canvas:  
对应本图层的canvas  
+ Shape[]:  
指向本图层包含的图形  

####方法:
+ draw():  
读取所有shape并绘制

+ clea():   
清空本图层  

+ AddShape(X,Y,range,tag,color):  
为图层添加一个shape，其后是shape初始化参数  

+ DeleteShape():  
将Shape数组某项设为最后一项，并将最后一项设为undefined，并将Shape.length减一(将最后一项的图形移到要删除的项上)

##Shape：
每一个标签所对应的圆形  

####属性:
+ location:  
三维矩阵，代表图形的中心  

+ range:  
圆的半径  

+ tag:  
该图形所对应的标签  

+ color:  
图形绘制时的颜色

+ fill_style(还没有):  
说明shape内部填充方式  

+ stroke_style(还没有):  
说明shape线条样式  

####方法:
+ GetX():  
获取中心X坐标 

+ GetY():  
获取中心Y坐标

+ Transformation(matrix):  
将矩阵location右乘一个矩阵

##TagPool：
所有待处理标签  

####属性:   
+ tags[]:  
标签池中所有的标签  

####方法:  
+ AddTag(tag):  
增添一个新的标签  

+ DeleteTag(tag):  
删除标签池中的参数标签  

+ isInclude(tag):  
判断标签是否在标签池中

---