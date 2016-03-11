### CSS 3中弹性盒布局的最新版概述
在CSS 3中，CSS Flexible Box模块为一个非常重要的模块，该模块用于以非常灵活的方式实现页面布局处理。

虽然可以使用其他CSS样式属性来实现页面布局处理，但是如果使用CSS Flexible Box模块中定义的弹性盒布局技术，可以根据屏幕尺寸或浏览器窗口尺寸自动调整页面中各局部区域的显示方式，即实现非常灵活的布局处理。

虽然CSS Flexible Box模块已经被公布了好几年，但是自开始公布以来，该模块中所定义的内容已经经过了几次重大修改。目前公布的正式版本为[◦CSS Flexible Box Layout Module - W3C Candidate Recommendation, 18 September 2012](http://www.w3.org/TR/css3-flexbox/)。

目前为止，Opera 12.10版本以上，IE 11版本以上、Chrome 21版以上、Firefox 22版本以上的浏览器均支持该最新版本。

### 从示例页面开始学习最新版本的弹性盒布局

接下来开始通过一个示例页面开始学习最新版本的弹性盒布局。该示例页面中的body元素中的代码如下所示。
```
<body>
<div id="main">
    <div class="content">
        <section>
            <h1>section 1</h1>
            <p>示例文字</p>
        </section>
        <section>
            <h1>section 2</h1>
            <p>示例文字</p>
        </section>
        <section>
            <h1>section 3</h1>
            <p>示例文字</p>
        </section>
        <section>
            <h1>section 4</h1>
            <p>示例文字</p>
        </section>
    </div>
    <div class="content">
        <section>
            <h1>section 5</h1>
            <p>示例文字</p>
            <section>
                <h1>section 6</h1>
                <p>示例文字</p>
            </section>
            <section>
                <h1>section 7</h1>
                <p>示例文字</p>
            </section>
            <section>
                <h1>section 8</h1>
                <p>示例文字</p>
            </section>
    </div>
    <div class="content">
        <section>
            <h1>section 9</h1>
            <p>示例文字</p>
        </section>
        <section>
            <h1>section 10</h1>
            <p>示例文字</p>
        </section>
        <section>
            <h1>section 11</h1>
            <p>示例文字</p>
        </section>
        <section>
            <h1>section 12</h1>
            <p>示例文字</p>
        </section>
    </div>
</div>
</body>
```

接下来，首先对该页面中各div元素及section元素指定边框样式，代码如下所示。
```
<style>
#main {
    border: 1px dotted #f0f;
    padding: 1em;
}
.content {
    border: 1px dotted #0ff;
    padding: 1em;
}
section {
    border: 1px dotted #f00;
    padding: 1em;
}
</style>
```

在浏览器中打开目前为止的示例页面，页面中各元素从上往下纵向排列，如下图所示。


![](http://upload-images.jianshu.io/upload_images/201324-aadd6edef84b1466.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 对示例页面使用弹性盒布局
弹性盒布局的指定方法为：对需要布局的元素的容器元素使用display:flex;样式属性。在CSS Flexible Box模块中，该容器元素中的每一个元素均被称为“Flex item”，将该容器元素称为“Flex container”。

弹性盒布局方式与使用float等样式属性进行的布局方式的一个主要区别为，当使用float等样式属性时，需要对容器中每一个元素指定样式属性，当使用弹性盒布局时，只需对容器元素指定样式属性。

接下来，我们首先对所有样式类名为content的div元素使用弹性盒布局，这些div元素的容器元素为id属性值为main的div元素，修改该元素的样式代码如下所示：
```
#main {
    border: 1px dotted #f0f;
    padding: 1em;
    display: flex;
}
```
在浏览器中打开示例页面，页面中所有样式类名为content的div元素的排列方式被修改为横向排列，如下图所示。

![](http://upload-images.jianshu.io/upload_images/201324-6a32c9a5ae91ecf3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 设置元素排列方向

可以通过flex-direction样式属性的使用来控制容器中所有子元素的排列方向，可指定值如下所示。

- row:横向排列（默认值）
- row-reverse:横向反向排列
- column:纵向排列
- column-reverse:纵向反向排列

修改id属性值为main的div元素的样式代码如下所示：
```
#main {
    border: 1px dotted #f0f;
    padding: 1em;
    display: flex;
    flex-direction: row-reverse;
}
```
在浏览器中打开示例页面，页面中所有样式类名为content的div元素的排列方式被修改为从容器元素，即id属性值为main的div元素的右端开始横向反向排列，如下图所示。

![](http://upload-images.jianshu.io/upload_images/201324-8aa98ee74bc783cc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
接下来首先恢复所有样式类名为content的div元素的排列方式为横向正向排列，修改id属性值为main的div元素的样式代码如下所示：
```
#main {
    border: 1px dotted #f0f;
    padding: 1em;
    display: flex;
}

```
然后对所有样式类名为content的div元素指定flex-direction: column-reverse;样式属性，代码如下所示：
```
.content {
    border: 1px dotted #0ff;
    padding: 1em;
    display: flex;
    flex-direction: column-reverse;
}
```
在浏览器中打开示例页面，页面中所有content的div元素的所有section子元素的排列方式被修改为纵向反向排列（不包含section子元素中的section孙元素），如下图所示。
![Paste_Image.png](http://upload-images.jianshu.io/upload_images/201324-1ac6e9216bb36ed1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 使用order样式属性指定排列顺序
使用弹性盒布局的时候，可以通过order属性来改变各元素的显示顺序。可以在每个元素的样式中加入order属性，该属性使用一个表示序号的整数属性值，浏览器在显示的时候根据该序号从小到大来显示这些元素。

接下来首先设置所有样式类名为content的div元素的所有section子元素的排列方式为纵向正向排列，修改所有样式类名为content的div元素的样式代码如下所示：
```
.content {
    border: 1px dotted #0ff;
    padding: 1em;
    display: flex;
    flex-direction: column;
}

```
　接下来通过将所有样式类名为content的div元素中的第2个section子元素的order样式属性值设置为-1的方法设置这些section子元素被优先显示在其他section子元素之前，代码如下所示：
```
.content section:nth-child(2) {
    order: -1;
}
```
在浏览器中打开示例页面，页面中所有样式类名为content的div元素中的第2个section子元素被显示在其他section子元素之前，如下图所示。

![](http://upload-images.jianshu.io/upload_images/201324-eaa32493e3189573.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
### 设置元素宽度及高度
接下来首先介绍如何设置被横向排列的每一个元素的宽度。

可以通过flex属性值的使用使所有子元素的总宽度等于容器宽度。

接下来通过将所有样式类名为content的div元素的flex属性值设置为1的方法使所有样式类名为content的div元素的总宽度等于容器元素，即id属性值为main的div元素的宽度，代码如下所示。当所有样式类名为content的div元素的flex属性值都被设置为1时，这些div元素的宽度均等。
```
.content {
    border: 1px dotted #0ff;
    padding: 1em;
    display: flex;
    flex-direction: column;
    flex:1;
}
```
在浏览器中打开示例页面，所有样式类名为content的div元素的宽度自动增长，这些元素的总宽度等于容器元素，即id属性值为main的div元素的宽度,每一个样式类名为content的div元素的宽度均等，如下图所示。
![](http://upload-images.jianshu.io/upload_images/201324-e5998822d2bd3a01.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
接下来，我们设置第二个样式类名为content的div元素的flex属性值为2，代码如下所示。
```
.content:nth-child(2) {
    flex:2;
}
```
为了更清晰地计算元素宽度，我们取消所有元素的边框设置及内边距设置，修改后的完整样式代码如下所示。
```
<style>
#main {
    display: flex;
}
.content {
    display: flex;
    flex-direction: column;
    flex:1;
}
.content section:nth-child(2) {
    order: -1;
}
.content:nth-child(2) {
    flex:2;
}
</style>
```
在浏览器中打开示例页面，第二个样式类名为content的div元素宽度为其他样式类名为content的div元素宽度的两倍，假设这些元素的容器元素，即id属性值为main的div元素的宽度等于600px，则第一个与第三个样式类名为content的div元素宽度的宽度均等于150px，第二个样式类名为content的div元素宽度的宽度等于300px。

可以使用flex-grow属性来指定元素宽度，但是该样式属性对于元素宽度的计算方法与flex样式属性对于元素宽度的计算方法有所不同。

接下来指定所有样式类名为content的div元素的flex-grow样式属性值为1，宽度为150px,指定第二个样式类名为content的div元素的flex-grow样式属性值为为3。修改后的完整样式代码如下所示。
```
<style>
#main {
    display: flex;
}
.content {
    display: flex;
    flex-direction: column;
    width:150px;
    flex-grow:1;
}
.content section:nth-child(2) {
    order: -1;
}
.content:nth-child(2) {
    flex-grow:3;
}
</style>
```
在浏览器中打开示例页面，假设这些元素的容器元素，即id属性值为main的div元素的宽度等于600，则第一个与第三个样式类名为content的div元素宽度的宽度均等于180px，第二个样式类名为content的div元素宽度的宽度等于240px。对于每个样式类名为content的div元素宽度的计算步骤如下所示：

1. 600(容器宽度)-150*3（三个样式类名为content的div元素宽度的总宽度）=150
2. 150/5(三个样式类名为content的div元素宽度的flex-grow样式属性值的总和)=30
3. 第一个与第三个样式类名为content的div元素宽度的宽度均等于150（其width样式属性值+）+30*1（其flew-grow样式属性值）=180px
4. 第二个样式类名为content的div元素宽度的宽度等于150（其width样式属性值+）+30*3（其flew-grow样式属性值）=240px

可以使用flex-shrink属性来指定元素宽度，该样式属性与flex-grow样式属性的区别在于：当子元素的width样式属性值的总和小于容器元素的宽度值时，必须通过flex-grow样式属性来调整子元素宽度，当子元素的width样式属性值的总和大于容器元素的宽度值时，必须通过flex-shrink样式属性来调整子元素宽度。

接下来指定所有样式类名为content的div元素的flex-shrink样式属性值为1，宽度为250px,指定第二个样式类名为content的div元素的flex-shrink样式属性值为为3。修改后的完整样式代码如下所示。
```
<style>
#main {
    display: flex;
}
.content {
    display: flex;
    flex-direction: column;
    width:250px;
    flex-shrink:1;
}
.content section:nth-child(2) {
    order: -1;
}
.content:nth-child(2) {
    flex-shrink:3;
}
</style>
```
在浏览器中打开示例页面，假设这些元素的容器元素，即id属性值为main的div元素的宽度等于600，则第一个与第三个样式类名为content的div元素宽度的宽度均等于220px，第二个样式类名为content的div元素宽度的宽度等于160px。对于每个样式类名为content的div元素宽度的计算步骤如下所示：
1. 250*3（三个样式类名为content的div元素宽度的总宽度）-600(容器宽度)=150
2. 150/5(三个样式类名为content的div元素宽度的flex-shrink样式属性值的总和)=30
3. 第一个与第三个样式类名为content的div元素宽度的宽度均等于250（其width样式属性值+）-30*1（其flew-shrink样式属性值）=220px
4. 第二个样式类名为content的div元素宽度的宽度等于250（其width样式属性值+）-30*3（其flew-grow样式属性值）=160px

在使用flex-grow样式属性或flex-shrink样式属性调整子元素宽度时，也可以使用flex-basis样式属性指定调整前的子元素宽度，该样式属性与width样式属性的作用完全相同。

可以将flex-grow、flex-shrink以及flex-basis样式属性值合并写入flex样式属性中，方法如下所示。

```
flex:flex-grow样式属性值 flex-shrink样式属性值 flex-basis样式属性值;
```
在使用flex样式属性值时，flex-grow、flex-shrink以及flex-basis样式属性值均为可选用样式属性值，当不指定flex-grow、flex-shrink样式属性值时，默认样式属性值均为1，当不指定flex-basis样式属性值时，默认样式属性值为0px。

修改本示例中的样式代码如下所示：
```
<style>
#main {
    display: flex;
}
.content {
    display: flex;
    flex-direction: column;
    width:250px;
    flex:250px;
}
.content section:nth-child(2) {
    order: -1;
}
.content:nth-child(2) {
    flex:1 3 250px;
}
</style>
```
在浏览器中打开示例页面，假设这些元素的容器元素，即id属性值为main的div元素的宽度等于600，则第一个与第三个样式类名为content的div元素宽度的宽度均等于220px，第二个样式类名为content的div元素宽度的宽度等于160px。

在子元素为横向排列时，flex、flex-grow、flex-shrink以及flex-basis样式属性均用于指定或调整子元素宽度，当子元素为纵向排列时，flex、flex-grow、flex-shrink以及flex-basis样式属性均用于指定或调整子元素高度。

### 单行布局与多行布局
可以使用flex-wrap样式属性来指定单行布局或多行布局，可指定样式属性值如下所示：

- nowrap:不换行
- wrap:换行
- wrap-reverse:虽然换行，但是换行方向与使用
- wrap样式属性值时的换行方向相反

接下来首先恢复页面内各div元素的边框与内边距(padding)的指定，同时指定所有样式类名为content的div元素的宽度为250px，代码如下所示。
```
<style>
#main {
    border: 1px dotted #f0f;
    padding: 1em;
    display: flex;
}
.content {
    border: 1px dotted #0ff;
    padding: 1em;
    display: flex;
    flex-direction: column;
    flex:250px;
}
section {
    border: 1px dotted #f00;
    padding: 1em;
}
.content section:nth-child(2) {
    order: -1;
}
</style>
```
然后指定容器元素，即id属性值为main的div元素的flex-wrap样式属性值为wrap，以指定允许对所有样式类名为content的div元素进行换行布局，代码如下所示。
```
#main {
    border: 1px dotted #f0f;
    padding: 1em;
    display: flex;
    flex-wrap: wrap;
}
```
在浏览器中打开示例页面，当浏览器窗口宽度不足以容纳三个样式类名为content的div元素时，最右边的样式类名为content的div元素被换行显示，如下图所示。

![](http://upload-images.jianshu.io/upload_images/201324-04efc379086d0063.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

可以将flex-direction样式属性值与flex-wrap样式属性值合并书写在flex-flow样式属性中。以下两段代码的作用完全相同。
```
//使用flex-direction样式属性与flex-wrap样式属性
.content {
    flex-direction: row;
    flex-wrap: wrap;
}
//使用flex-flow样式属性
.content {
    flex-flow: row wrap;
}
```
### 弹性盒布局中的一些专用术语
接下来首先介绍弹性盒布局中的一些专用术语，在进行布局时这些术语的含义如下图所示。
![](http://upload-images.jianshu.io/upload_images/201324-e6ce1b483848ffa4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- main axis:进行布局时作为布局基准的轴，在横向布局时为水平轴，在纵向布局时为垂直轴。
- main-start / main-end:进行布局时的布局起点与布局终点。在横向布局时为容器的左端与右端，在纵向布局时为容器的顶端与底端。
- cross axis:与main axis垂直相交的轴，在横向布局时为垂直轴，在纵向布局时为水平轴。
- cross-start / cross-end:cross axis轴的起点与终点。在横向布局时为容器的顶端与底端，在纵向布局时为容器的左端与右端。将flex-wrap属性值指定为wrap且进行横向多行布局时，按从cross-start到cross-end方向，即从上往下布局，将flex-wrap属性值指定为wrap-reverse且进行横向多行布局时，按从cross-end到cross-start方向，即从下往上布局。
### justify-content属性

justify-content属性用于指定如何布局容器中除了子元素之外的main axis轴方向（横向布局时main axis轴方向为水平方向，纵向布局时main axis轴方向为垂直方向）上的剩余空白部分。

当flex-grow属性值不为0时，各子元素在main axis轴方向上自动填满容器，所以justify-content属性值无效。

可指定justify-content属性值如下所示：
- flex-start：从main-start开始布局所有子元素（默认值）。
- flex-end：从main-end开始布局所有子元素。
- center：居中布局所有子元素。
- space-between：将第一个子元素布局在-main-start处，将最后一个子元素布局在main-end处，将空白部分平均分配在所有子元素与子元素之间。
- space-around：将空白部分平均分配在以下几处：main-start与第一个子元素之间、各子元素与子元素之间、最后一个子元素与main-end之间。

上述各属性值的区别如下图所示(灰色代表空白部分)。
![](http://upload-images.jianshu.io/upload_images/201324-4894b8e23f9e911a.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### align-items属性与align-self属性
align-items属性与justify-content属性类似，用于指定子元素的对齐方式，但是align-items属性指定的是cross axis轴方向（横向布局时cross axis轴方向为垂直方向，纵向布局时cross axis轴方向为水平方向）上的对齐方式，可指定属性值如下所示。
- flex-start：从cross-start开始布局所有子元素（默认值）。
- flex-end：从cross-end开始布局所有子元素。
- center：居中布局所有子元素。
- baseline：如果子元素的布局方向与容器的布局方向不一致，则该值的作用等效于flex-start属性值的作用。如果子元素的布局方向与容器的布局方向保持一致，则所有子元素中的内容沿基线对齐。
- stretch：同一行中的所有子元素高度被调整为最大。如果未指定任何子元素高度，则所有子元素高度被调整为最接近容器高度（当考虑元素边框及内边距时，当边框宽度与内边距均为0则等于容器高度）。
上述各属性值的区别如下图所示(灰色代表空白部分)。

![](http://upload-images.jianshu.io/upload_images/201324-0c40e31ae8952f27.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

align-self属性与align-items属性的区别在于：align-items被指定为容器元素的样式属性，用于指定所有子元素的对齐方式，而align-self属性被指定为某些子元素的样式属性，用于单独指定这些子元素的对齐方式。例如将容器元素的align-items属性值指定为center（居中对齐）后，可以将第一个子元素的align-self属性值指定为flex-start（对齐在cross-start端）。可指定值如下所示：
- auto:继承父元素的align-items属性值
- flex-start
- flex-end
- center
- baseline
- stretch

### align-content属性
当进行多行布局时，可以使用align-content属性来指定各行对齐方式。该属性与align-items属性的区别在于：align-items属性用于指定子元素的对齐方式，而align-content属性用于指定行对齐方式。可以指定的属性值如下所示：

- flex-start：从cross-start开始布局所有行。
- flex-end：从cross-end开始布局所有行。
- center：居中布局所有行。
- space-between：将第一行布局在cross-start处，将最后一行布局在cross-end处，将空白部分平均分配在各行之间。
- space-around：将空白部分平均分配在以下几处：cross-start与第一行之间、各行与行之间、最后一行与cross-end之间。

上述各属性值的区别如下图所示(灰色代表空白部分)。

![](http://upload-images.jianshu.io/upload_images/201324-a4d14df6a0d5ffbe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

*[摘自](http://www.admin10000.com/)*
