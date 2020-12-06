# DOM

- 定义了访问 HTML 和 XML 文档的标准
- 获取、修改、添加或删除 HTML 元素

## DOM节点

- HTML文档视为节点树

[html树](https://www.w3school.com.cn/i/ct_htmltree.gif)

### DOM方法

- 编程接口

  - 通过 JavaScript （或其他语言）对 HTML DOM 进行访问
  - 所有 HTML 元素被定义为对象
  - 编程接口：对象方法和对象属性

- getElementById()
  - 返回带有指定 ID 的元素。
getElementsByTagName()
  - 返回包含带有指定标签名称的所有元素的节点列表（集合/节点数组）。
getElementsByClassName()
  - 返回包含带有指定类名的所有元素的节点列表。
appendChild()
  - 把新的子节点添加到指定节点。
removeChild()
  - 删除子节点。
replaceChild()
  - 替换子节点。
insertBefore()
  - 在指定的子节点前面插入新的子节点。
createAttribute()
  - 创建属性节点。
createElement()
  - 创建元素节点。
createTextNode()
  - 创建文本节点。
getAttribute()
  - 返回指定的属性值。
setAttribute()
  - 把指定属性设置或修改为指定的值。

### DOM属性

- innerHTML - 节点（元素）的文本值
parentNode - 节点（元素）的父节点
childNodes - 节点（元素）的子节点
attributes - 节点（元素）的属性节点

- nodeName 属性规定节点的名称。

  - nodeName 是只读的
  - 元素节点的 nodeName 与标签名相同
  - 属性节点的 nodeName 与属性名相同
  - 文本节点的 nodeName 始终是 #text
  - 文档节点的 nodeName 始终是 #document

- nodetype返回节点的类型，只读
  
  - 元素：1
属性：2
文本：3
注释：8
文档：9

- 访问HTML元素（节点）

  - getElementById():指定ID
  - getElementsByTagName：指定标签名
  - getElementsByClassName()：指定类名

- DOM修改

  - innerHTML属性

- 创建新的HTML元素

  - 创建新节点，将其追加到已有元素上
1.appendChild（）

```html
<!DOCTYPE html>
<html>
<body>

<div id="div1">
<p id="p1">This is a paragraph.</p>
<p id="p2">This is another paragraph.</p>
</div>

<script>
var para=document.createElement("p");//创建文本节点
var node=document.createTextNode("This is new.");//创建文本节点
para.appendChild(node);//向p元素追加文本节点

var element=document.getElementById("div1");//查找已有元素
element.appendChild(para);//追加新元素
</script>

</body>
</html>

```

2.insertBefore（）

- 将新元素插入一个父元素和一个子元素之间

```html
<!DOCTYPE html>
<html>
<body>

<div id="div1">
<p id="p1">This is a paragraph.</p>
<p id="p2">This is another paragraph.</p>
</div>

<script>
var para=document.createElement("p");
var node=document.createTextNode("This is new.");
para.appendChild(node);

var element=document.getElementById("div1");
var child=document.getElementById("p1");
element.insertBefore(para,child);
</script>

</body>
</html>

```

- 删除
  - 需要知晓父元素

```html
parent.removeChild(child);
```

- 替换
  - replaceChild（）

```html
<!DOCTYPE html>
<html>
<body>

<div id="div1">
<p id="p1">This is a paragraph.</p>
<p id="p2">This is another paragraph.</p>
</div>

<script>
var parent=document.getElementById("div1");
var child=document.getElementById("p1");
var para=document.createElement("p");
var node=document.createTextNode("This is new.");
para.appendChild(node);
parent.replaceChild(para,child);//节点替换
</script>

</body>
</html>

```

- HTML事件
当 HTML 元素”有事情发生“时，浏览器就会生成事件：

  - 在元素上点击
加载页面
改变输入字段

```html
<!DOCTYPE html>
<html>
<body>

<input type="button"
onclick="document.body.style.backgroundColor='lavender';"
value="改变背景色">

</body>
</html>

```

或者使用函数

```html
<!DOCTYPE html>
<html>
<body>

<script>
function ChangeBackground()
{
document.body.style.backgroundColor="lavender";
}
</script>

<input type="button" onclick="ChangeBackground()" value="改变背景色" />

</body>
</html>

```

- 分配事件

```html
<button onclick="displayDate()">嘿</button>//向button元素分配一个onclick事件
```

```javascript
<script>
document.getElementById("myBtn").onclick=function(){displayDate()};
</script>
```

- onload、onunload
用户进入或离开页面时触发
处理cookies，浏览器类型/版本等。

- onchange
用于输入字段的验证

- onmouseover、onmouseout
鼠标指针移动到或离开元素时触发函数

- onmousedown、onmouseup、onclick
鼠标按钮被点击时，触发 onmousedown 事件，然后，当鼠标按钮被松开时，会触发 onmouseup 事件，最后，当鼠标点击完成时，触发 onclick 事件

## DOM节点列表

- getElementsByTagName() 方法返回节点列表。

```html
var x=document.getElementsByTagName("p");
```

节点列表是一个节点数组
可以通过下标访问对应节点，如第二个p元素可用y=x1

- length定义节点数量，可用于循环列表

### 导航节点

- parentNode、firstChild、lastChild
访问某一个子元素相对应的父节点，首个子元素以及最后一个子元素。

### 根节点

- document.documentElement - 全部文档
document.body - 文档的主体

### 其他属性

- childNodes
- nodeValue

```html
<script>
var txt=document.getElementById("intro").childNodes[0].nodeValue;
document.write(txt);
</script>
```
