# text1
># 高阶函数
- JavaScript的函数其实都指向某个变量。既然变量可以指向函数，函数的参数能接收变量，那么一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数。
e.g.
```
function add(x, y, f) {
    return f(x) + f(y);
}
```

>## map/reduce
## map
- 由于map()方法定义在JavaScript的Array中，我们**调用Array的map()方法，传入我们自己的函数，就得到了一个新的Array作为结果：**
```

function pow(x) {
    return x * x;
}

```
e.g.小明希望利用map()把字符串变成整数，他写的代码很简洁：
```
'use strict';

var arr = ['1', '2', '3'];
var r;

```
注意用parseInt(arr)和传入一个指针后的parseInt(c)不一样
map:把f(x)作用在Array的**每一个元素**并把结果生成一个**新的Array**

## reduce
- Array的reduce()把一个函数作用在这个Array的[x1, x2, x3...]上，这个函数必须接收**两个参数**，reduce()把**结果继续和序列的下一个元素做累积计算**
   - 比方说对一个Array求和，就可以用reduce实现：
```
var arr = [1, 3, 5, 7, 9];
arr.reduce(function (x, y) {
    return x + y;
}); // 25
```

# 函数积累
>## substring()
- substring() 方法用于提取字符串中介于两个指定下标之间的字符。
   - 在本例中，我们将使用 substring() 从字符串中提取一些字符：
```
<script type="text/javascript">

var str="Hello world!"
document.write(str.substring(3))

</script>
输出：

lo world!
```
```
<script type="text/javascript">

var str="Hello world!"
document.write(str.substring(3,7))

</script>
输出：

lo w
```

>## parseFloat() 函数和parseInt()函数
资料参考：
https://www.cnblogs.com/qinxuemei/p/3969099.html#:~:text=parseInt%28%29%20%E5%87%BD%E6%95%B0%20%E5%AE%9A%E4%B9%89%E5%92%8C%E7%94%A8%E6%B3%95%20parseInt%28%29%20%E5%87%BD%E6%95%B0%E5%8F%AF%E8%A7%A3%E6%9E%90%E4%B8%80%E4%B8%AA%E5%AD%97%E7%AC%A6%E4%B8%B2%EF%BC%8C%E5%B9%B6%E8%BF%94%E5%9B%9E%E4%B8%80%E4%B8%AA%E6%95%B4%E6%95%B0%E3%80%82%20%E8%AF%AD%E6%B3%95%20parseInt%28string%2C%20radix%29,2%20~%2036%20%E4%B9%8B%E9%97%B4%E3%80%82%20%E5%A6%82%E6%9E%9C%E7%9C%81%E7%95%A5%E8%AF%A5%E5%8F%82%E6%95%B0%E6%88%96%E5%85%B6%E5%80%BC%E4%B8%BA%200%EF%BC%8C%E5%88%99%E6%95%B0%E5%AD%97%E5%B0%86%E4%BB%A5%2010%20%E4%B8%BA%E5%9F%BA%E7%A1%80%E6%9D%A5

## filter

- filter也是一个常用的操作，它用于把Array的某些元素过滤掉，然后返回剩下的元素。

- 和map()类似，Array的filter()也接收一个函数。和map()不同的是，filter()把传入的函数依次作用于每个元素，然后**根据返回值是true还是false**决定保留还是丢弃该元素。

# 算法题
## 1.查找数字
- 传统暴力遍历方法（java ,C++)
- 二分法（只写出来一维数组的hhh 再钻研一下）
## 2.字符串替换
- C++：字符串运算
- js:replace函数
