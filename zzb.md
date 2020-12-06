# url

- 统一资源定位符
  - 资源所在的地址
  - 资源：HTML页面 CSS文档 图像

- protocol 协议
  - http

- domain name 域名
  - www.example.com

- 端口
  - :80

- 路径 额外参数 锚点
- 绝对 URL - 指向其他站点（比如 src="http://www.example.com/"）
- 相对 URL - 指向站点内的文件（比如 src="/i/image.gif"）

## 接口

- Java类型
- 类通过继承接口，从而继承接口的抽象方法。
  - 类描述对象的属性和方法。
  - 接口包含类要实现的方法

```java
interface 接口名称[extends]
//声明变量
//抽象方法
```

e.g.

```java
/* 文件名 : NameOfInterface.java */
import java.lang.*;
//引入包
public interface NameOfInterface
{
   //任何类型 final, static 字段
   //抽象方法
}
```

## 实现

- 类实现接口时，要实现接口中所有的方法

```java
...implements 接口名称[, 其他接口名称, 其他接口名称..., ...] ...
实例
/* 文件名 : MammalInt.java */
   public class MammalInt implements Animal{
   public void eat(){
      System.out.println("Mammal eats");
   }
   public void travel(){
      System.out.println("Mammal travels");
   }
   public int noOfLegs(){
      return 0;
   }
   public static void main(String args[]){
      MammalInt m = new MammalInt();
      m.eat();
      m.travel();
   }
}
```

## 继承

- extends关键字

```java
// 文件名: Sports.java
public interface Sports
{
   public void setHomeTeam(String name);
   public void setVisitingTeam(String name);
}
// 文件名: Football.java
public interface Football extends Sports
{
   public void homeTeamScored(int points);
   public void visitingTeamScored(int points);
   public void endOfQuarter(int quarter);
}
```

- 实现Football接口的类需要实现五个方法，其中两个来自于Sports接口

## Vue.js

- 目录结构

- build：项目构建(webpack)相关代码
config：配置目录，包括端口号等。我们初学可以使用默认的。
node_modules：npm 加载的项目依赖模块
src：要开发的目录，里面包含了几个目录及文件：
  - assets: 放置一些图片，如logo等。
  - components: 一个组件文件，可以不用。
  - App.vue: 项目入口文件。
  - main.js: 项目的核心文件。
  - static：静态资源目录，如图片、字体等。
  - test:初始测试目录，可删除
  - t.xxxx文件：一些配置文件，包括语法配置，git配置等。
  - index.html：首页入口文件，添加一些 meta 信息或统计代码等。
  - package.json：项目配置文件。
  - README.md：项目的说明文档。

- 示例

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Vue</title>
<script src="https://cdn.staticfile.org/vue/2.4.2/vue.min.js"></script>
</head>
<body>
<div id="vue_det">
<h1>site : {{site}}</h1>
<h1>url : {{url}}</h1>
<h1>{{details()}}</h1>
</div>
<script type="text/javascript">
var vm = new Vue({
el: '#vue_det',
data: {
site: "菜鸟教程",
url: "www.runoob.com",
alexa: "10000"
},
methods: {
details: function() {
return  this.site + " - 学的不仅是技术，更是梦想！";
}
}
})
</script>
</body>
</html>
```

- el参数：

  - DOM 元素中的 id。在上面实例中 id 为 vue_det
  - 接下来的改动全部在以上指定的 div 内，div 外部不受影响
    - div 是一个块级元素。即自动地开始一个新行。
    - 可以通过 div 的 class 或 id 应用额外的样式。
