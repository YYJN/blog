日本程序员norahiko，写了一个排序算法的[动画演示](http://jsdo.it/norahiko/oxIy/fullscreen)，非常有趣。

[排序算法](http://en.wikipedia.org/wiki/Sorting_algorithm)（Sorting algorithm）是计算机科学最古老、最基本的课题之一。要想成为合格的程序员，就必须理解和掌握各种排序算法。
目前，最常见的排序算法大概有七八种，其中["快速排序"](http://en.wikipedia.org/wiki/Quicksort)（Quicksort）使用得最广泛，速度也较快。它是图灵奖得主C. A. R. Hoare（1934--）于1960时提出来的。

![[地址](http://jsdo.it/norahiko/oxIy/fullscreen)](http://upload-images.jianshu.io/upload_images/201324-90ffd235d11693ec.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

[排序算法](http://en.wikipedia.org/wiki/Sorting_algorithm)（Sorting algorithm）是计算机科学最古老、最基本的课题之一。要想成为合格的程序员，就必须理解和掌握各种排序算法。

目前，最常见的排序算法大概有七八种，其中["快速排序"](http://en.wikipedia.org/wiki/Quicksort)（Quicksort）使用得最广泛，速度也较快。它是图灵奖得主C. A. R. Hoare（1934--）于1960时提出来的。

![](http://upload-images.jianshu.io/upload_images/201324-75bf12dee8dd18ec.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

"快速排序"的思想很简单，整个排序过程只需要三步：

> （1）在数据集之中，选择一个元素作为"基准"（pivot）。
（2）所有小于"基准"的元素，都移到"基准"的左边；所有大于"基准"的元素，都移到"基准"的右边。
（3）对"基准"左边和右边的两个子集，不断重复第一步和第二步，直到所有子集只剩下一个元素为止。

举例来说，现在有一个数据集{85, 24, 63, 45, 17, 31, 96, 50}，怎么对其排序呢？
第一步，选择中间的元素45作为"基准"。（基准值可以任意选择，但是选择中间的值比较容易理解。）
![](http://upload-images.jianshu.io/upload_images/201324-629a85a9a5530ae3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

第二步，按照顺序，将每个元素与"基准"进行比较，形成两个子集，一个"小于45"，另一个"大于等于45"。
![](http://upload-images.jianshu.io/upload_images/201324-8a25858f1176a875.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

第三步，对两个子集不断重复第一步和第二步，直到所有子集只剩下一个元素为止。
![](http://upload-images.jianshu.io/upload_images/201324-23dc83b11607e7a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/201324-89a6ca11a078a28c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/201324-a198982b852a5b46.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
![](http://upload-images.jianshu.io/upload_images/201324-f110ec937a56452a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

下面参照网上的资料（[这里](http://acatalept.com/blog/2008/10/28/stable-quicksort-in-javascript/)和[这里](http://www.stoimen.com/blog/2010/06/11/friday-algorithms-quicksort-difference-between-php-and-javascript/)），用Javascript语言实现上面的算法。
首先，定义一个quickSort函数，它的参数是一个数组。
```
var quickSort = function(arr) {
};
```
然后，检查数组的元素个数，如果小于等于1，就返回。
```
var quickSort = function(arr) {
　　**if (arr.length <= 1) { return arr; }**
};
```

接着，选择"基准"（pivot），并将其与原数组分离，再定义两个空数组，用来存放一左一右的两个子集。
```
var quickSort = function(arr) {
　　if (arr.length <= 1) { return arr; }
　　**var pivotIndex = Math.floor(arr.length / 2) ;**
　　**var pivot = arr.splice(pivotIndex, 1)[0];**
　　**var left = [];**
　　**var right = [];**
};
```
然后，开始遍历数组，小于"基准"的元素放入左边的子集，大于基准的元素放入右边的子集。
```
var quickSort = function(arr) {
　　if (arr.length <= 1) { return arr; }
　　var pivotIndex = Math.floor(arr.length / 2) ;
　　var pivot = arr.splice(pivotIndex, 1)[0];
　　var left = [];
　　var right = [];
　　**for (var i = 0; i < arr.length; i++){**
　　　　**if (arr[i] < pivot) {**
　　　　　　**left.push(arr[i]);**
　　　　**} else {**
　　　　　　**right.push(arr[i]);**
　　　　**}**
　　**}**
};
```
最后，使用递归不断重复这个过程，就可以得到排序后的数组。
```
var quickSort = function(arr) {
　　if (arr.length <= 1) { return arr; }
　　var pivotIndex = Math.floor(arr.length / 2);
　　var pivot = arr.splice(pivotIndex, 1)[0];
　　var left = [];
　　var right = [];
　　for (var i = 0; i < arr.length; i++){
　　　　if (arr[i] < pivot) {
　　　　　　left.push(arr[i]);
　　　　} else {
　　　　　　right.push(arr[i]);
　　　　}
　　}
　　**return quickSort(left).concat([pivot], quickSort(right));**
};
```
使用的时候，直接调用quickSort()就行了。

![](http://upload-images.jianshu.io/upload_images/201324-ee7a842a1a1954e8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

(END[摘自](http://www.ruanyifeng.com/blog/2011/04/quicksort_in_javascript.html))
