# text1
11.9
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
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
var results = arr.map(pow); // [1, 4, 9, 16, 25, 36, 49, 64, 81]
console.log(results);

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
   - javascript还不会创建二维数组
- C++:建立二维数组办法
```
 vector<vector<int> > array;
```
 二维数组行数：
```
 int m=array.size();
```
 二维数组列数：
 ```
 int n=array[0].size();
 ```
- Java(行/列表示方法类似，建立二维数组：）
```
int [][] array
```
- 二分法（只写出来一维数组的hhh 再钻研一下）
```
#include<stdio.h>
#define M 10;

void main()
{
	static int a[10] = { -12,0,6,16,23,56,80,100,110,115 };
	int n, low, mid, high, found,index;
	low = 0;
	high = M - 1;
	found = 0;
	mid = (high + low) / 2;
	printf("input a number to be searched:");

	index = scanf_s("%d", &n);//输入要查询数字的值,并且获得scanf的返回值用于判断输入的格式

	while (index!= 1)
	{
		printf("the format is wrong!");
			break;
	}
	while (index== 1)
	{
		while (low <= high)
		{
			mid = (low + high) / 2;
			if (n == a[mid])
			{
				found = 1;
				break;
			}/*找到 结束循环*/
			else if (n > a[mid])
				low = mid + 1;
			else
				high = mid - 1;
		}
		if (found == 1)
		{
			printf("The index of %d is %d", n, mid);
			break;
		}
		else
		{
			printf("There is not %d", n);
			break;
		}
	}
	}
```
## 2.字符串替换
- C++：字符串运算
```
c +="%20";
```
- js:replace函数
```
replace(/ /g,"%20");
```
   - /g作用域为全局
   
 >11.11
   # 闭包
- 把函数作为结果值返回。
- e.g.求和
```
function sumall(arr){
    var sum=function(){
        return arr.reduce(function(x,y){
            return x+y;
        });
    }
    return sum;
}
```
   - 调用sumal（）时，返回求和函数，再次调用得到求和的结果。

- 返回函数不要引用任何循环变量，如果要使用，再创建一个函数，用该函数的参数绑定循环变量当前的值：
```
function count() {
    var arr = [];
    for (var i=1; i<=3; i++) {
        arr.push((function (n) {
            return function () {
                return n * n;
            }
        })(i));
    }
    return arr;
}
```
- 创造一个匿名函数并立即执行：
```
(function (x) {
    return x * x;
})(3); // 9
```

# 箭头函数
- 类似匿名函数
```
var fn = x => x * x;
```
- 多语句恰当使用{...}和return
```
x => {
    if (x > 0) {
        return x * x;
    }
    else {
        return - x * x;
    }
}
```
# Treenode

## 1.定义
```

struct TreeNode {
	int val;
	struct TreeNode *left;
	struct TreeNode *right;
};
```
- 包括
- 1.本节点所存储的值
- 2.左孩子节点的指针
- 3.右孩子节点的指针
   - 子节点必须使用指针
   - 节点必须**使用地址**的方式存在在结构体当中
      - 一级指针就是一个节点的地址，二级指针存放的节点地址的地址。通过一级指针可以找到一个节点（包括值和左右），二级指针可以找到节点。函数中需要递归的方式构建整个树，其中每次构建一个节点的时候其实获得到的是一级指针。这个指针的值是系统分配我们无法决定，然后需要把根的左右节点的值指向构建的新的子树，为了调用方法返回后依然能够保留指针的位置，所以需要二级节点.
- 如果需要重新定义结构体的名字，使用typedef方法
```
typedef struct TreeNode {
	int val;
	struct TreeNode *left;
	struct TreeNode *right;
} BiNode, *BiTree;
```

## 递归的特点
>两个显著的特征
- 终止条件
   - 递归必须有一个终止的条件，即不能无限循环地调用本身
- 自身调用
   - 原问题可以分解为子问题，子问题和原问题的求解方法是一致的，即都是调用自身的同一个函数

e.g.
```
public int sum(int n) { 
    if (n <= 1) { 
        return 1; 
    }  
    return sum(n - 1) + n;  
} 
```
## 遍历
- 二叉树的前序遍历：根左右
- 二叉树的中序遍历：左根右
- 二叉树的的后序遍历：左右根

## malloc函数
- #include<stdlib.h>

- 在内存中找一片指定大小的空间，然后将这个空间的首地址给一个指针变量，这里的指针变量可以是一个单独的指针，也可以是一个数组的首地址。
```
  int *p;

  p = (int *)malloc(sizeof(int));
```
   - 实参：sizeof(int)

>### new
-  返回指定类型的指针
-  **自动计算所需要的大小**。
```
int *p;

p = new int;   //返回类型为int *类型，分配的大小为sizeof(int)

p = new int[100]; //返回类型为int *类型，分配的大小为sizeof(int) * 100
    
```
>### malloc
- 人工计算字节数 
- 返回的时候强转成void*

>## BiTree T与BiTree &T

- Bitree T 
   - 定义Bitree一个实例对象T;
- Bitree *T 
   - 定义Bitree的实例对象指针,指向一个实例对象
- Bitree &T 
   - 定义Bitree的实例对象的引用,就是一个已经定义的对象的别名,需要初始化;
```
Bitree T;
Bitree &T = T;
Bitree *T = &T; //&是取地址.
```
>## 箭头运算符
- 传入参数是结构体
- 需要该结构体作为返回值
- 对结构体赋值
>## C实现

```
#include<stdio.h>
#include<stdlib.h>
typedef struct BiTNode
{
    char data;
    struct BiTNode* lchild, * rchild;   //创建二叉树
}BiTNode, * BiTree;
void PreOrderTraverse(BiTree T)//二叉树的先序遍历
{
    if (T == NULL)
        return;
    printf("%c ", T->data);
    PreOrderTraverse(T->lchild);
    PreOrderTraverse(T->rchild);
}
void InOrderTraverse(BiTree T)//二叉树的中序遍历
{
    if (T == NULL)
        return;
    InOrderTraverse(T->lchild);
    printf("%c ", T->data);
    InOrderTraverse(T->rchild);
}
void PostOrderTraverse(BiTree T)//后序遍历
{
    if (T == NULL)
        return;
    PostOrderTraverse(T->lchild);
    PostOrderTraverse(T->rchild);
    printf("%c ", T->data);
}
void CreateBiTree(BiTree* T)
{
    char ch;
    scanf_s("%c", &ch);
    if (ch == '#')
        *T = NULL;
    else
    {
        *T = (BiTree)malloc(sizeof(BiTNode));
        if (!*T)
            exit(-1);
        (*T)->data = ch;
        CreateBiTree(&(*T)->lchild);
        CreateBiTree(&(*T)->rchild);
    }
}
int main()
{
    BiTree T;
    printf("请给二叉树按照先序方式依次输入结点的值(空结点为#):\n");
    //例子：AB#D##C##
    CreateBiTree(&T);
    printf("先序方式遍历结果：\n");
    PreOrderTraverse(T);
    printf("中序方式遍历结果：\n");
    InOrderTraverse(T);
    printf("后序方式遍历结果：\n");
    PostOrderTraverse(T);
    return 0;
}
```
>## JS实现
- new运算符：
   - 创建一个定义的对象类型的实例
   - 创建一个具有构造函数的内置对象的实例

- shift函数
   - 把数组的第一个元素从其中删除，返回第一个元素的值
   - 不创建新数组
```
function TreeNode(val){
    this.val=val;
    this.left=null;
    this.right=null;
}
```

//根据二叉树的层次遍历的序列结果，创建二叉树
```
function createTree_levelOrder(levelOrderArr) {
    let queue=[];
    let root=null;

    if(levelOrderArr[0]!==undefined){
```
        //1、找到根节点，将根节点加入到队列（层次遍历结果序列的第一个一定是根节点）
```
        let nodeVal=levelOrderArr.shift();
        root=new TreeNode(nodeVal);
        queue.push(root);
```
        //2、循环的将队列队首的元素出队，把和出队元素相关的元素加入到队列（循环中的元素为空，循环就运行完了）

        //队列不为空
        
```
        while(queue.length){
            //1、将队列队首的元素出队（要么是整棵树的根节点、要么是子树的根节点）
            let head= queue.shift();
            //2、把和出队元素相关的元素加入到队列（先创建节点，根节点的左右孩子）
            //a、创建左节点，将它加入到队列
            nodeVal=levelOrderArr.shift();
            if(nodeVal!='#'){
                head.left=new TreeNode(nodeVal);
                queue.push(head.left);
            }

            //b、创建右节点，将它加入到队列
            nodeVal=levelOrderArr.shift();
            if(nodeVal!='#'){
                head.right=new TreeNode(nodeVal);
                queue.push(head.right);
            }
        }
    }

    return root;
}
```
## 根据先序遍历和中序遍历重建二叉树
- 递归
   -  i:
      - 根节点在中序遍历结果的下标
      - 当前左子树的节点个数
```
function reConstructBinaryTree(pre, vin)
{
if(!pre.length||!vin.length){
    return null;
}
    var rootVal=pre[0];
    var root=new TreeNode(rootVal);
    
    let i=0;
    for(;i<vin.length;++i){
        if(vin[i]===rootVal){
            break;
        }
    }
    root.left=reConstructBinaryTree(pre.slice(1,i+1),vin.slice(0,i));
    root.right=reConstructBinaryTree(pre.slice(i+1),vin.slice(i+1));
    return root;
}
```


### 参考资料
- https://blog.csdn.net/qq_40551367/article/details/90705080?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-2.channel_param

- https://blog.csdn.net/zhanggonglalala/article/details/79738213?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-4.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-4.channel_param
