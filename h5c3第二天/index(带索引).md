---
typora-copy-images-to: medias
---



# 1. H5第2天

颜色补充：

#### 1. HSL 颜色

HSL 就是色调(Hue)、饱和度(Saturation)和亮度(Lightness)的缩写

H：0(或360)表示红色，120表示绿色，240表示蓝色，也可取其他数值来指定颜色。取值为：0 - 360。
S：取值为：0.0% - 100.0%；0% 意味着灰色，而 100% 是全彩
L：取值为：0.0% - 100.0%；0% 是黑色，100% 是白色。

rgba

hsla   透明效果



晚上练习：

1. 日本国旗
2. wifi

##  学习目标

- 理解

  - 掌握线性渐变的设置
  - 理解和使用过渡属性实现常见效果
  - 理解和使用2d转换实现常见效果

- 应用
1. 实现安卓渐变机器人

   ![1524967125415](medias/1524967125415.png)

   ​





## 1. 线性渐变 linear-gradient（理解）

![1524909587675](medias/1524909587675.png)

**渐变分4种，分别是**

- **线性渐变**
- 径向渐变 了解
- 重复线性渐变 了解
- 重复径向渐变 了解

因为线性渐变可能使用， 我们学习**线性渐变**即可，其他只需了解

### 注意

只能给以下属性添加渐变

- background-image
- background

给 `backgroundColor` 添加没有效果！



### 语法

`background: linear-gradient(方向？，颜色 颜色开始的位置，颜色 颜色结束的位置，，，);`

```css
 background: linear-gradient(black,red);   或者
 background-image: linear-gradient(black,red);
```

#### 方向

- 系统内置方向  `to top|to bottm|to left|to right|to right top ` 默认值是 `to bottom` 
- 自定义方向 `0deg或者1deg`等

```css
 background-image: linear-gradient( to right top, black,red);
```

![1524909829171](medias/1524909829171.png)

####  颜色 开始的位置 ,颜色 结束的位置

- 颜色  `red或者#000或者rgba`等
- 开始位置（省略了 默认就是0） 单位是 `px或者百分比（相对于自身的宽或者高）`   


- 结束的位置（省略了 默认就是百分100%）

```css
 background-image: linear-gradient( black 5%,red 10%,yellow 100%);
```

![1525227928494](medias/1525227928494.png)

**实际开发完整的写法：**

~~~css
background: -webkit-linear-gradient(to right, #00b4ff, #0080e2);
background: -moz-linear-gradient(to right, #00b4ff, #0080e2);
background: -ms-linear-gradient(to right, #00b4ff, #0080e2);
background: -o-linear-gradient(to right, #00b4ff, #0080e2);
background: linear-gradient(to right, #00b4ff, #0080e2);
~~~



## 2. 径向渐变 radial-gradient（了解）

1. background: radial-gradient(red, blue);     /* 标准的语法 */

2. 设置形状  ellipse表示椭圆形，circle表示圆形  background: radial-gradient(circle, red, yellow)

3. 设置方向    利用 at  来设置位置    background: radial-gradient(at left top , circle, red, yellow)

4. closest-side：最近边； farthest-side：最远边； closest-corner：最近角； farthest-corner：最远角。默认是最远的角farthest-corner

5. 多个颜色    background: radial-gradient(red 5%, green 15%, blue 60%); 

   日本国旗

## 3 重复渐变  repeating（了解）

圆圈：

 background: repeating-radial-gradient(circle, #fff, #fff 10%, #000 10%, #000 20%);

WIFI:

 background: repeating-radial-gradient(circle at left bottom, #ccc 0%, #ccc 10%, transparent 10%, transparent 20%);  

## 2. 背景（重点）

背景 **background** 一共拥有8个子属性 

![1525009882812](C:\Users\andy\Desktop\H5C3\02 css3\总结笔记\medias\1525009882812.png)



先从最简单的开始 学习&复习

1. `background-color:`  指定背景颜色
2. `background-image:`  指定要使用的背景图片 或者  **渐变**
3. `background-repeat:`  设置背景图片的平铺方式    
4. `background-attachment:` 设置背景图像是随对象内容滚动还是固定的  默认是滚动
5. `background-position:` 设置背景图片的偏移值 

那么 还剩下三个需要我们重点讲解的   **size** 、**origin**  和 **clip**

### 2.1 background-repeat 新增属性 

round：

背景图像自动缩放直到适应且填充满整个容器。（CSS3）

space：

背景图像以相同的间距平铺且填充满整个容器或某个方向。（CSS3）

### 2.2  background-attachment 新增属性 

fixed：

背景图像相对于窗体固定。

scroll：

背景图像相对于元素固定，也就是说当元素内容滚动时背景图像不会跟着滚动，因为背景图像总是要跟着元素本身。但会随元素的祖先元素或窗体一起滚动。

local：

背景图像相对于元素内容固定，也就是说当元素随元素滚动时背景图像也会跟着滚动，因为背景图像总是要跟着内容。（CSS3）

### 2.3 backgorund-size（重点）

设置背景图片的大小  有两种设置方法 ，一种是自定义 如  `background-size:100px 100px` 

1. background-size:100px 200px     把背景缩图片放为 宽度 100像素  高度  200像素
2. background-size:100px ；    把背景图片缩放为 宽度 100像素  高度  根据宽度自动等比例缩放
3. background-size:100px auto ；    把背景图片缩放为 宽度 100像素  高度  根据宽度自动等比例缩放
4. background-size: 50%  50%;   把背景图片缩放为 盒子的  百分之 50%

 **另外一种是系统提供的值（重点学习）**  

- cover 等比放大到容器大小，直到最短边触底
- contain 等比放大到容器大小，直到最长边触底

![1525011623369](C:\Users\andy\Desktop\H5C3\02 `css3\总结笔记\medias\1525011623369.png)

```html
  <style>
        /* 公共样式 */
    div { width: 200px; height: 200px; display: inline-block; margin: 10px; border: 1px solid #000; background-image: url("./1.png"); background-repeat: no-repeat; }

    div:nth-child(1) {
      /* 默认值 相当于不设置 */
      background-size: auto;
    }

    div:nth-child(2) {
      /* 等比放大到容器大小，直到最短边触底 */
      background-size: cover;
    }

    div:nth-child(3) {
      /* 等比放大到容器大小，直到最长边触底 */
      background-size: contain;
    }
  </style>
</head>

<body>
  <div></div>
  <div></div>
  <div></div>
</body>
```

精灵图有个缺点， 要求盒子必须和  精灵图 图标一样大。  

但是，我们移动端点击的时候，要求盒子大一些方便点击。

问题来了，盒子如果比精灵图标大了，会显示 其余 的图标。

以下是解决方案：



### 2.4 backgrund-origin

设置背景图片从哪里开始显示    我们把一个元素分为三个部分 **border** **padding** **content-width** 这个属性就是用来设置背景图片 三个部分开始显示的

- border-box 从边框部分开始显示
- padding-box 从padding部分开始显示  **默认值**
- content-box 从内容部分开始显示

![1525012566010](C:\Users\andy\Desktop\H5C3\02 css3\总结笔记\medias\1525012566010.png)

```html
  <style>
    /* 公共样式 */
    div { width: 200px; height: 200px; display: inline-block; box-sizing: border-box; margin: 10px; background-image: url("./1.png"); background-repeat: no-repeat; background-color: red; border: 10px dashed #000; padding: 30px; }

    div:nth-child(1) {
      /* 从padding部分开始显示 */
      background-origin: padding-box;
    }

    div:nth-child(2) {
      /*从边框部分开始显示 */
      background-origin: border-box;
    }

    div:nth-child(3) {
      /* 从内容部分开始显示 */
      background-origin: content-box;
    }
  </style>
</head>
<body>
  <div></div>
  <div></div>
  <div></div>
</body>
```

### 2.5 backgorund-clip

背景裁剪， 一个元素分为三个部分 **border** **padding** **content-width**  

该属性控制背景从哪个部分 **开始 向外裁剪**

- border-box 从边框部分开始显示  **默认值** 
- padding-box 从padding部分开始显示 
- content-box 从内容部分开始显示

![1525013097543](C:\Users\andy\Desktop\H5C3\02 css3\总结笔记\medias\1525013097543.png)

```html
  <style>
    /* 公共样式 */
    div { width: 200px; height: 200px; display: inline-block; box-sizing: border-box; margin: 10px; background-image: url("./1.png"); background-repeat: no-repeat; background-color: red; border: 10px dashed #000; padding: 30px; background-origin: content-box; }

    div:nth-child(1) {
      /* 从边框部分开始显示  默认值  */
      background-clip: border-box;
    }

    div:nth-child(2) {
      /* padding-box 从padding部分开始显示  */
      background-clip: padding-box;
    }

    div:nth-child(3) {
      /* content-box 从内容部分开始显示 */
      background-clip: content-box;
    }
  </style>
</head>

<body>
  <div></div>
  <div></div>
  <div></div>
</body>	
```

### 2.6 多背景写法

现在可以给盒子添加多个背景。

```
background:url(demo.gif) no-repeat ,url(demo1.gif) no-repeat；
```


## 3. 过渡 transition（重点）

| 属性                       | 描述                                         |
| -------------------------- | -------------------------------------------- |
| transition                 | 简写属性，用于在一个属性中设置四个过渡属性。 |
| transition-property        | 规定应用过渡的 CSS 属性的名称。              |
| transition-duration        | 定义过渡效果花费的时间。默认是 0。           |
| transition-timing-function | 规定过渡效果的时间曲线。默认是 "ease"。      |
| transition-delay           | 规定过渡效果何时开始。默认是 0。             |

1. **要过渡的属性**  

   > 如width，height  `transition-property: width;`   写`all`代表全部

2. **持续时间** 

   > 设置过渡的持续时间  如 `transition-duration:10s`

3. **速度曲线**

   设置变化的速度曲线 如匀速等  

   - linear： 匀速
   - ease： 慢-快-慢  默认值
   - ease-in： 慢-快。
   - ease-out： 快-慢。
   - ease-in-out： 慢-快-慢。

4. **延迟时间**

   设置产生过渡时的延迟时间 如   `transition-delay: 10s;`



​	可以使用复合写法

```css
 /* 过渡的属性为width 持续3s 匀速 延迟0s */
   transition: width 3s linear 0s;
```

### 3.1 多个过渡写法

可以同时对一个元素的多个属性添加过渡   对宽度和高度设置不同的过渡

```css
  transition: 
        width 1s ease-in 1s,
        height 10s ease-in-out 2s;
```

### 3.2  过渡结束事件

元素在执行过渡结束之后，会自动触发的事件 **transitionend**   

```javascript
    var div = document.querySelector("div");
    div.addEventListener("transitionend", function () {
      console.log("div的过渡结束之后，触发");
    })
```



## 4. 2D转换（变换）transform（重点）

2d转换是改变标签在**2维平面**上的**位置和形状**的一种技术，先来学习2维坐标系

### 4.1  2维坐标系

**2维坐标系**其实就是指布局的时候的坐标系 如图

![1524965494414](medias/1524965494414.png)

### 4.2. 2d移动 translate

2d移动是2d转换里面的一种功能，可以改变元素在页面中的位置，类似 **定位**

使用2d移动的步骤：

1. 给元素添加 **转换属性**  `transform`
2. 属性值为 `translate(x,y)`  如  `transform:translate(50px,50px)`;

```css
  div{
    transform: translate(50px,50px);
  }
```

![1524965782388](medias/1524965782388.png)

#### 小结

1. **translate**中的百分比单位是相对于自身元素的  `translate:(50%,50%);`
2. **translate**类似定位，不会影响到其他元素的位置
3. 对行内标签没有效果

### 4.3. 2d旋转 rotate

2d旋转指的是让元素在2维平面内顺时针旋转或者逆时针旋转

使用步骤：

1. 给元素添加转换属性 `transform`
2. 属性值为 `rotate(角度)`  如 `transform:rotate(30deg)`  顺时针方向旋转**30度**

```css
div{
      transform: rotate(0deg);
}
```

在浏览器中手动修改 **rotate**

![4](medias/4.gif)

观察过后，2d旋转有以下特点

1. 角度为正时 顺时针 负时 为逆时针
2. 默认旋转的中心点是元素的中心点


**CSS 三角箭头的做法**



### 4.4. 2d缩放 scale

缩放，顾名思义，可以放大和缩小。 只要给元素添加上了这个属性就能控制它放大还是缩小 

步骤：

1. 给元素添加转换属性 `transform`
2. 转换的属性值为 `scale(宽的倍数,高的倍数)`    如 宽变为两倍，高变为3倍 `transform:scale(2,3)`

```css
div{
    transform:scale(2,3);
}
```

![1524966701225](medias/1524966701225.png)

####  小结

1. transform:scale(1,1) 放大一倍 相对于没有放大
2. transform:scale(2,2) 宽和高都放大了2倍
3. transform:scale(2)  只写一个参数 第二个参数则和第一个参数一样 相当于 scale(2,2)
4. transform:scale(0.5,0.5)  缩小 
5. transform:scale(-2,-2) 反向放大2倍    很少用负数 容易让人产生误解


### 4.6. 2D 倾斜skew

skew()：能够让元素倾斜显示。它可以将一个对象以其中心位置围绕着X轴和Y轴按照一定的角度倾斜。这与rotate()函数的旋转不同，rotate()函数只是旋转，而不会改变元素的形状。skew()函数不会旋转，而只会改变元素的形状



### 4.7. 转换中心 transform-origin 了解

该属性可以修改元素旋转的时候的中心点

1. transform-origin:**50% 50%;**  默认值  元素的中心位置 百分比是相对于自身的宽度和高度

2. transform-origin:**top left;**  左上角   和 transform-origin：0 0;相同

3. transform-origin:**50px 50px;**  距离左上角 50px 50px 的位置

4. transform-origin：**0**;  只写一个值的时候  第二个值默认为 50%;

   ​

### 4.8 transform 可以多个

但是注意他们有先后顺序

里面用空格隔开.

transform: skewY(-30deg) rotate(60deg);

先倾斜  后再倾斜的基础上旋转

transform:none 取消样式.

### 4.9 让一个盒子水平居中垂直居中

~~~
position: absolute;
/*定位的百分比是参照父容器的宽高*/
left: 50%;
top: 50%;
/*使用transform实现元素的居中  百分比是参照元素本身的宽高*/
 transform: translate(-50%,-50%);

~~~

我们得出结论：

* translate(50px)   里面如果是 绝对值 px  则直接移动相应距离
* translate(50%)  里面如果是百分比， 则相对于 自己宽度或者高度 来说的

