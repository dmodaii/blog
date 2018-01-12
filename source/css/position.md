
# absolute
绝对定位元素相对于最近的非 static 祖先元素定位。当这样的祖先元素不存在时，则相对于根级容器定位（document.documentElement(根元素/HTML元素)）

- html,body的宽高和背景色
  - 宽高
  ```
  html,body{
    height:100%;
  }
  ```
  浏览器负责分配块级元素宽度，那么浏览器也一定可以分配高度(只是没有做)，那么浏览器本身是有宽度和高度的，设置html的height:100%，就可以获取浏览器的定高了，后面的body和div也就有了依赖。

  - 背景色
  当html或body设置了背景色时候会被浏览器捕获，显示浏览器的背景色

- 定位距离
 从content-border 开始， 所以父级定位元素的margin和border会影响top，left，必须指定 left ， right ， top ， bottom 属性中的至少一个

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>Document</title>
    <style type="text/css">
        /* 给html加高度但是文档还是*/
        html{
            height: 80%;
            background: red;
            margin-top: 300px;
        }
        body{
            border:30px solid #093;
            height: 600px;
            /* background: red; */
        }
        #test1{
            /* position: relative; */
            width: 800px;
            height: 6000px;
            /* background: red url('./list_img_head_def@2x') top 20% right 10%; */
            /* background: url('./list_img_head_def@2x.png') no-repeat top 10% right 20% red; */
            /* background-position:  top 50% right 10%; */
        }
        #test_absolute{
            position: absolute;
            width: 200px;
            height: 200px;
            bottom: 0;
            left: 0;
            /*  相对于viewport高度的百分比，在滚动屏幕时仍随屏幕滚动* */
            /* top: 10%;   */
            /* top: 70px; */
            background-color: yellow;
        }
        #test_fixed{
            position: fixed;
            width: 200px;
            height: 200px;
            bottom: 0;
            right: 0;
            /* 于屏幕视口（viewport）的位置来指定元素位置， 定位方式常用于创建在滚动屏幕时仍固定在相同位置的元素*/
            /* top: 10%;; */
            background-color: rgb(75, 211, 48);
        }
    </style>
</head>
<body>
    <div id ='test1'>
        <div id="test_absolute">
            test_absolute
        </div>
        <div id="test_fixed">
            test_fixed
        </div>
    </div>
</body>
</html>
```

# fixed
不为元素预留空间，而是通过指定元素相对于屏幕视口（viewport）的位置来指定元素位置。
Viewport(HTML元素的容器/父元素)
固定定位与绝对定位相似，但元素的包含块为 viewport 视口。该定位方式常用于创建在滚动屏幕时仍固定在相同位置的元素


# relative


# note
Note : 绝对(absolute)定位对象在可视区域之外会导致滚动条出现。而放置相对(relative)定位对象在可视区域之外，滚动条不会出现。

- relative
设置属性值为 relative 会保持对象在正常的HTML流中，但是它的位置可以根据它的前一个对象进行偏移。
在相对(relative)定位对象之后的文本或对象占有他们自己的空间而不会覆盖被定位对象的自然空间。
（会占用该元素在文档中初始的页面空间，即在使用top，bottom，left，right进行移动位置之后依旧不会改变其所占用空间的位置）

- absolute
与此不同的，在绝对(absolute)定位对象之后的文本或对象在被定位对象被拖离正常文档流之前会占有它的自然空间。
放置绝对(absolute)定位对象在可视区域之外会导致滚动条出现。
而放置相对(relative)定位对象在可视区域之外，滚动条不会出现。

http://blog.csdn.net/cyyax/article/details/50607066
