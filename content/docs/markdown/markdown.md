---
title: "Markdown"
weight: 1
---


Markdown 学习文档
=====================

## Markdown标题
Markdown标题有两种格式
### 1. 使用=和-标记一级和二级标题
> 代表一级标题  
> \=================  
> 
> 代表二级标题  
> \--------------

### 2. 使用#号标记
> \#  一级标题  
> \##  二级标题  
> \### 三级标题  
> ...  
> 以此类推

#### 注意事项：  
符号与文件间空格，#号和标题文字间要有一个空格。是Markdown语法有求
> \# 正确写法  
> \#错误写法  
> 
标记前面不能有Tab或者空格（虽然自己实验可以有1-3个空格，应该编辑器做的容错处理） 

一般文档只有要只有一个一级标题。

#### 标题的嵌套结构：
标题的层次结构应该遵循逻辑顺序，不应该跳级使用。良好的标题结构就像一本书的目录：

##### 推荐的层次结构
> \#
> \##
> \###
> \###
> \##

#### 标题锚点
可以为标题创建锚点，用于文本内跳转，比如下面这个可以跳转到一级标题
[返回最上](#markdown-学习文档)

## Markdown文本格式  
这一节和后面的学习中只展示效果，如果看标记方式，打开编辑器的源码模式
#### 1. 换行
使用在一行最后面加**两个以上空格，加上回车**，如果没有加空格直接回车，在显示中还是同一行.  
在段落后面使用一个空行来表示重新开始一个段落。
#### 2.  字体  
**粗体：** 使用两个**号或者两个下划线__ __包围__ 文字 
*斜体：* 使用一个*号或者下划线_ _包围_ 文字
***粗斜体组合*** 使用三个***号或者___ ___包围文字___

**使用建议：**
建议使用*号而不是下划线_，因为*号在各种Markdown编辑器中兼容性更好。  

#### 3.  分割线
这是一条分割线，可以使用不同方式插入下划线，查看源码
***
* * *
- - -
-------
#### 4.  删除线
是文字两边各加两个~~波浪线，找不到的话看一下键盘左上角Esc下面那个键。
~~这是一个删除线~~
#### 5.  下划线
<u>这是下划线</u>
这是HTML标签实现的，在Markdown中也支持很多HTML和CSS标签。

#### 6. 脚注
[^这是一个脚注 ] 后面是被脚注的内容  
这个测试下来很多都不支持。

#### 7. 行内代码标记
> 使用 `git commit` 命令提交代码

当代码本身包含反引号时，使用两个反引号包围
> 要显示反引号，使用 `` `code` `` 这样的格式

#### 8. 文本高亮
文本高亮不是标准Markdown语法，但是许多扩展支持
常见语法：
> 这是==文本高亮==  

HTML替代方案
> 这是<mark>文本高亮</mark>

#### 9. 段落和换行
> 这是第一个段落。他可以包含很多句子，内容可以很长，会自动换行显示。
>
> 这是第二个段落，上面有一个空行分割时，下面的内容会形成一个新的段落。

**常见错误**

- 段落之间没有空行分割，不会显示为新段落
- 使用段落缩进，在Markdown文本中不应该使用段落缩进，包括空格缩进或者Tab缩进。

**换行技巧**

- 在行尾添加两个或更多空格，然后回车
- HTML换行标签 \<br\>
- 反斜杠 \\ (部分解析器支持)  
  
一般使用两个空格或者\<br\>标签

**空行的作用**
在很多情况下需要使用空行，因为空行可以结束前面文本标记的延续，比如列表，如果只是换行后继续输入文本，其实还是在前面列表格式的范围内，需要使用空行来表示不属于前面列表格式范围。总结有下面两个作用：

- 分割段落
- 分割不同元素

**一些实用建议**

- 在标题和内容之间留空行
- 在列表前后留空行
- 在代码块前后留空行
- 保持一致的空行使用习惯

## Markdown列表  

#### 无序列表

可以使用 `` `*` ``  `` `\` `` `` `\` `` 作为无序列表标记，标记后面加空格，然后再填写内容。

建议使用 `` `-` `` ,因为它在视觉上更清晰，在同一文档中保持一致的标记方式。

#### 有序列表

使用数字加上 `.` 就可以，就像显示的那样，数字可以不连续，Markdown会自动修正数字顺序：
> 1. 第一项
> 3. 第二项
> 4. 第三项

#### 列表嵌套

使用缩进对列表进行嵌套使用，子列表在前加两个或者四个空格即可：
> 1. 第一项
>    - 子列表第一项
>    - 子列表第二项
> 2. 第二项
>    - 子列表第一项
>    - 子列表第二项       

使用四个空格显示层次感更强，同一文档中使用一致缩进长度。

#### 任务列表

任务列表是Github风格Markdown的扩展功能，现在被广泛支持：

**基本语法**

> - [ ] 未完成任务
> - [x] 已完成任务
> - [ ] 另一个未完成任务

可以使用缩进来展示任务和子任务：

> ##### 开发阶段
> - [ ] 任务
>      - [x] 子任务1
>      - [ ] 子任务2

**使用技巧**
方括号内的空格和x表示复选框是否选中，可以与嵌套列表结合使用，在项目管理，学习计划，生活清单中特别有用。

## 引用块

引用块用于突出显示重要信息，引用他人观点或创建视觉层次。

> 使用>符号，后面再紧跟一个空格，创建一个引用块。

简化写法可以只在第一行使用>符号，结束地方使用空行结束引用。

> 一个多行引用
  。。。
  。。。

多级嵌套，使用多个>符号

> 第一层
>> 第二层
>>> 第三层

引用块的自定义显示效果

<blockquote style="border-left: 5px solid #ff0000; color: #333; background-color: #f9f9f9;">这是带有颜色的引用块。</blockquote>

## Markdown代码

Markdown提供了多种方式来展示代码，从简单的行内代码，到复杂的代码块，满足不同场景下的代码展示需求。

> 写到这里觉得如果一个文档里有多个主次标题还有其他加粗效果，是在很难分清主次标题或者说文章结构，是否可以考虑只增大字体而不加粗，这样可以比较明确的分清不同章节。
> 可以使用HTML标签来增大字体，如使用\<span\>标签：
> <span style="font-size:20px;">这是增大字体的文本</span>

1. 行内代码

> `printf()` 函数

2. 转义字符

如果要显示特殊字符，需要使用转义字符。
用两个 \`\` 包含来显示一个 \`, 用三个 \`\`\` 包含来显示两个\`\` ，但是大多数特殊字符都可以用 `\` 进行转义。
使用 &nbsp; 表示空格。

3. 代码块

使用 ` ``` ` 包裹一段代码,并指定一种语言（也可以不指定）：

    ```javascript
    $(document).ready(function () {
        alert('RUNOOB');
    });
    ```

常用支持语言列表

- javascript / js - JavaScript
- python / py - Python
- html - HTML
- css - CSS
- sql - SQL
- json - JSON
- xml - XML
- yaml / yml - YAML
- bash / shell - Shell脚本
- java - Java
- cpp / c++ - C++
- csharp / c# - C#
- php - PHP
- ruby / rb - Ruby
- go - Go语言
- rust - Rust
- typescript / ts - TypeScript

4. 显示行号

语法示例（部分支持）：

```javascript {.line-numbers}
function fibonacci(n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

console.log(fibonacci(10));
```

5. 代码差异对比

Diff语法

```diff
function calculateTotal(items) {
-   let total = 0;
+   let total = 0.0;
    
    for (let item of items) {
-       total += item.price;
+       total += parseFloat(item.price);
    }
    
+   // 保留两位小数
+   total = Math.round(total * 100) / 100;
    return total;
}
```

Git风格的差异显示

```diff
@@ -1,5 +1,8 @@
 function greetUser(name) {
-    console.log("Hello " + name);
+    if (!name) {
+        throw new Error("Name is required");
+    }
+    console.log(`Hello, ${name}!`);
 }
```

## Markdown链接

链接是使Markdown文档具有交互性的关键元素。
掌握链接语法能让你创建内容丰富、易于导航的文档。
链接使用方法如下

> [链接名称] (链接地址)
> [链接文字] (链接地址 "可选的标题")

> [这是一个链接](https://www.baidu.com "baidu")

链接标题的作用，也就是双引号里的内容：

- 当鼠标悬停在链接上时显示提示信息
- 对搜索引擎优化和无障碍访问有帮助
- 标题文字放在双引号、单引号中都可以

> 电话联系：[拨打电话](tel:+86-138-0013-8000)

<span style="font-size:20px;">参考链接</span>

参考式链接将链接定义与使用分离，让文档更整洁，特别适合长文档或需要多次引用相同链接的情况，类似于书中的注解，右上角加个小1，可以到文后的注解部分根据标号查找。

基本语法：

> markdown [链接文字] [参考标签]
> [参考标签]: URL "可选标题"

可以通过变量来设置一个链接，变量赋值在文档末尾进行，例如定义一个变量，变量名是 `1`

> 这个链接用 1 作为网址变量 [Baidu][1]

然后在文章结尾部分：

> [1]: https://www.baidu.com

这时就给 `1` 赋值了。


<span style="font-size:20px;">简化写法</span>

当参考标签与链接文字相同时，可以省略第二个方括号，也就是不定义变量名，第一个方括号内的内容就是变量名

> 比如这个 [baidu][]  

> [baidu]: https:www.baidu.com

自动链接识别：

> markdown直接输入网址时： https://www.example.com

<span style="font-size:20px;">锚点链接的使用</span>

跳转标题：

 > [返回顶部](#markdown-学习文档)

 锚点规则：

 - 标题会自动生成锚点（我现在写这个文档的标题就没有自动生成锚点）
 - 锚点名称通常是标题的小写形式
 - 空格替换为连字符
 - 移除特殊字符

手动创建锚点：

> <a id="custom-anchor"></a>
> 自定义锚点位置
> [跳转到自定义位置](#custom-anchor)

返回顶部的特殊字符：

> [回到顶部][#]

## Markdown图片

Markdown图片语法格式如下：

> ![替代文字](图片路径)
> ![替代文字](图片路径 "图片标题")

其实和网络链接或者标题的格式差不多，图片路径可以使用本地图片文件路径，路径可以使用相对路径或者绝对路径，或者路径使用网络地址。

路径使用建议：

- 建议使用相对路径，便于项目移植。
- 创建专门的图片文件夹（如images/, assets/）
- 使用有意义的文件名，便于管理

也可以像网址那样对图片路径使用变量，再在结尾对图片路径统一赋值。

Markdown无法改变图片大小，如果需要可以使用HTML来改变大小
> <img src="https://www.baidu.com/img/flexible/logo/pc/result.png" width="20%">


可以使用CDN服务来保存图片

图片 alt 文本的重要性
Alt文本（替代文字）在图片无法显示时提供替代信息，同时对无障碍访问和SEO很重要。

同时，可以使图片链接到地址，需要与前面语法结合使用，例如

> [![这是百度](https://www.baidu.com/img/flexible/logo/pc/result.png)](https://www.baidu.com)

关于一些图片的尺寸控制，对齐方式，尺寸控制包含响应式自适应，这些功能可以查看HTML具体语法。

<div style="display: flex; justify-content: space-around; flex-wrap: wrap;">
  <img src="image1.jpg" alt="图片1" style="width: 30%; margin: 10px;">
  <img src="image2.jpg" alt="图片2" style="width: 30%; margin: 10px;">
  <img src="image3.jpg" alt="图片3" style="width: 30%; margin: 10px;">
</div>

## Markdown表格

| 靠左 | 靠右 | 居中| 换行 | Emoji |
| :--- | ---: | :---: | --- | --- |
| 左 | 右 | 居中 | 这个太长了，<br>换个行显示 | 👍 |
| **加粗** | [链接](https://www.baidu.com) | 单元格 | 单元格 | 💯 |


两端的线可以不要，但是为了美观建议写上，注意对齐方式。写法不需要严格对齐，显示时会自动对齐，但是对齐会更美观。

## Markdown高级技巧

支持的HTML元素

不在Markdown涵盖范围之内的标签，都可以直接在文档里面用HTML撰写。
目前支持的HTML元素有： `\<kbd\> \<b\> \<i\> \<em\> \<sup\> \<sub\> \<br\>` 等。

> 使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑

公式

Markdown Preview Enhanced 使用 KaTeX 或者 MathJax 来渲染数学表达式。
KaTeX 拥有比 MathJax 更快的性能，但是它却少了很多 MathJax 拥有的特性。你可以查看 KaTeX supported functions/symbols 来了解 KaTeX 支持那些符号和函数。

> \$...\$ 或者 \\(...\\) 中的数学表达式将会在行内显示。
> \$\$... \$\$ 或者 \\[...\\] 或者 ```math 中的数学表达式将会在块内显示。

例如

> $
\begin{Bmatrix}
   a & b  \\
   c & d
\end{Bmatrix}
$
$$
\begin{CD}
   A @>a>> B \\
@VbVV @AAcA \\
   C @= D
\end{CD}
$$

其中在数学表达范围内使用 \\ 时代表可以使用的函数， \\\\ 代表换行。

在 Markdown 中，数学公式通过 LaTeX 语法来表示。LaTeX 是一个强大的排版系统，特别适用于包含复杂数学公式的文档。

基本语法结构

- 命令：以反斜杠 \ 开头，如 \alpha、\sum
- 参数：用花括号 {} 包围，如 \frac{a}{b}
- 下标：使用 _，如 x_1
- 上标：使用 ^，如 x^2
- 分组：用花括号将多个字符组合，如 x_{i+1}

多行公式
使用 align 环境创建多行对齐公式：

> $$
> \begin{align}
> f(x) &= ax^2 + bx + c \\
> f'(x) &= 2ax + b \\
> f''(x) &= 2a
> \end{align}
> $$

不同括号类型的矩阵：

pmatrix：圆括号 $\begin{pmatrix} a & b \\ c & d \end{pmatrix}$
bmatrix：方括号 $\begin{bmatrix} a & b \\ c & d \end{bmatrix}$
vmatrix：行列式 $\begin{vmatrix} a & b \\ c & d \end{vmatrix}$

## Markdown图表绘制

图标在技术文档中非常重要，它可以帮助我们：
- 可视化复杂的数据关系
- 展示系统架构和工作流程
- 更清晰地表达思想和概念

常见的Markdown工具

1. Mermaid   
   Mermaid是最流行Markdown图标工具之一，它允许你使用简单的文本语法生成各种图表。
   支持的图表类型：
   - 流程图 (Flowchart)
   - 序列图 (Sequence Diagram)
   - 类图 (Class Diagram)
   - 状态图 (State Diagram)
   - 甘特图 (Gantt Chart)
   - 饼图 (Pie Chart)
   
    流程图：

     ```mermaid
      graph TD
        A[开始] --> B{条件判断}
        B -.->|Yes| C(执行操作A)
        B ==>|No| D((执行操作B))
        C --> E>结束]
        D --> E
        click E "https://www.baidu.com" "这是提示文本"
    ```

    流程图方向
    - TD 或 TB：从上到下
    - BT：从下到上
    - RL：从右到左
    - LR：从左到右
  
    节点形状
    - A[方形]：矩形
    - B{菱形}：菱形（决策）
    - C(圆角矩形)：圆角矩形
    - D((圆形))：圆形
    - E>旗帜形]：旗帜形
  
    连接线类型
    - --> 实线箭头
    - -.-> 虚线箭头
    - ==> 粗实线箭头
    - -- 实线
    - -. 虚线

    时序图：
     ```mermaid
    sequenceDiagram
    participant A as 用户
    participant B as 系统
    participant C as 数据库
    
    A->>B: 登录请求
    B->>C: 验证用户信息
    C-->>B: 返回验证结果
    B-->>A: 登录成功/失败
    ```

    时序图语法要点：

    - participant 定义参与者
    - ->> 实线箭头
    - -->> 虚线箭头
    - note 添加注释

    甘特图：

    ```mermaid
    gantt
    title 项目开发计划
    dateFormat  YYYY-MM-DD
    section 设计阶段
    需求分析      :done,    des1, 2024-01-01,2024-01-15
    UI设计       :active,  des2, 2024-01-10, 30d
    section 开发阶段
    前端开发      :         dev1, after des2, 45d
    后端开发      :         dev2, 2024-02-01, 60d
    section 测试阶段
    单元测试      :         test1, after dev1, 15d
    集成测试      :         test2, after dev2, 10d
    ```

    甘特图语法要点：

    - title 设置标题
    - dateFormat 定义日期格式
    - section 定义阶段
    - 任务状态：done（已完成）、active（进行中）、crit（关键）

    饼图：

    ```mermaid
    pie
    title 浏览器市场份额
    "Chrome" : 65
    "Safari" : 15
    "Firefox" : 10
    "其他" : 10
    ```

    类图： 

    ```mermaid
    classDiagram
    class 用户 {
        +用户名: string
        +密码: string
        +登录()
    }
    
    class 订单 {
        +订单号: int
        +创建日期: date
        +计算总价()
    }
    
    用户 "1" --> "n" 订单
    ```

    大多数工具支持将图表导出为：

    - PNG 图片
    - SVG 矢量图
    - PDF 文档

    各类工具支持情况需要查看官方文档。

2. 思维导图
 
   - 使用Mermaid的mindmap功能
   - 使用Markmap（需要安装特定插件）
  
   mindmap示例：

   ```mermaid
    mindmap
        root((项目计划))
            需求分析
              设计阶段
            开发阶段
            测试阶段
              部署上线
              后期维护
    ```
