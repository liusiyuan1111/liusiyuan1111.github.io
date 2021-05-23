---
title:  媒体查询+rem布局
date: 2021-05-14 13:25:53
tags:
- HTML5
- CSS3
- 前端
- 布局
---

## 媒体查询+rem布局

### 一、rem单位是什么？

​		rem（font size of the root element)是一个相对单位，指的是相对于根元素的字体大小的单位，常用于移动端布局，使用相对单位的优势在于可以自适应不同分辨率大小的屏幕。要了解rem单位，可以先理解em这个相对单位。

### 二、em单位

​		em单位是最常见的相对长度单位，基准值是当前元素的字号大小（如果当前元素没有设置字号，则继承父元素的字号大小），在css中，1em表示当前元素的字号大小，例如：p元素字号为16px，宽高使用em这个相对单位，则此时宽高应该相对于字号等于16px*10=160px

```css

        p {
            /* 宽高设为10em，由于字号是16px，则此时宽高应为10*16px=160px */
            font-size: 16px;
            width: 10em;
            height: 10em;
            background-color: aquamarine;
        }
```

​		可以看到此时的p元素大小为160px*160px

![image-20210514123306092](https://i.loli.net/2021/05/14/hWPOgrf3nHjlMaw.png)

### 三、rem单位的使用

​		在了解什么是em单位和相对单位后，就很好理解rem单位了，em是相对于当前元素字体大小的单位，而rem是相对于根元素的字体大小的单位，根元素也就是html元素。

```css
        html {
            /* 设置根元素的字号为15px */
            font-size: 15px;
        }

        p {
            /* 宽高设为10em，由于根元素字号是15px，则此时宽高应为10*15px=150px */
            width: 10em;
            height: 10em;
            background-color: aquamarine;
        }
```

![image-20210514123618613](https://i.loli.net/2021/05/14/3inN1MWgHhDfAcT.png)

### 四、媒体查询

​		我们已经知道了rem是相对于根元素的字号来说的，那具体怎么适配不同屏幕大小呢？这个时候就要用到媒体查询了，rem一般和媒体查询搭配使用。

​		媒体查询（Media Query）是CSS3的新语法，使用@media 查询，可以针对不同的媒体类型定义不同的样式，常用于针对不同的设备尺寸设置不同的样式。详细可以浏览mdn：[使用媒体查询 - CSS（层叠样式表） | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Media_Queries/Using_media_queries)

### 五、媒体查询+rem实现大小自适应变化

​		我们已经知道了rem是相对于根元素大小来说的，也知道了可以通过媒体查询来实现不同的设备尺寸设置不同的样式，那么我们可以通过媒体查询来设置根元素的字号，从而使用rem单位来实现页面元素大小的自适应变化。例如：

```css
        * {
            margin: 0;
            padding: 0;
        }
        /* 媒体查询，当设备宽度大于等于640px时，使用此样式 */
        @media screen and (min-width:640px) {
            html {
                font-size: 50px;
            }
        }
        /* 媒体查询，当设备宽度大于等于1260px时，使用此样式 */
        @media screen and (min-width:1260px) {
            html {
                font-size: 100px;
            }
        }

        p {
            /* 根据不同设备尺寸设置了不同的根元素字号 */
            /* 所以实现不同设备尺寸的屏幕元素大小自适应变化 */
            /* 没有设置width，则元素宽度由浏览器页面决定 */
            height: 10rem;
            font-size: 1rem;
            background-color: aquamarine;
        }
```

​		此时浏览器页面宽度为861px，当设备宽度大于等于640px时，元素高度应该是50px * 10rem=500px  元素内字体应该是50p * 1rem=50px

![image-20210514133257112](https://i.loli.net/2021/05/14/uHTYnCVc3iSfgqy.png)

​		此时浏览器页面宽度为1385px，当设备宽度大于等于1260px时，元素高度应该是100px * 10rem=1000px  元素内字体应该是100p * 1rem=100px 

![image-20210514133641144](https://i.loli.net/2021/05/14/sm65SnlyqfLxdP1.png)

### 六、注意事项

1. rem常用于移动端布局，PC端很少使用
2. rem常和媒体查询搭配使用
3. rem是过去移动端适配的一个过渡方式，随着vm/vh/vmax/vmin这种布局方式的兼容性越来越好，已经逐渐取代了rem布局





