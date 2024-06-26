# Latex Grammer

## 文档结构

### 1. 文档类型

`\documentclass{article}`

`\document[12pt, a4paper, oneside]{ctexart}`

英文： `book`, `article` , `beamer`

中文： `ctexbook`, `ctexart`, `ctexbeamer`



### 2. 使用宏包

`\usepackage{package_name1， package_name2}`

`\usepackage{amsmath, amsthm, amssymb, graphicx}`

数学公式与定理环境相关宏包： `amsmath`、`amsthm`、`amssymb`

插入图片的宏包：` graphicx`

超链接宏包： `hyperref` 

​		可以设置引用的颜色为黑色等

​		`\usepackage[bookmarks=true, colorlinks, citecolor=blue, linkcolor=black]{hyperref}`



### 3. 文档环境

`\begin{document}`

`······`

`\end{document}`



## 文本和排版

### 1. 标题，作者，日期

标题： `\title{}`

作者： `\author{}`

日期： `\date{}`



### 2. 特殊字体

| 加粗           | `\textbf{}`  |
| -------------- | ------------ |
| 斜体（意大利） | `\textit{}`  |
| 直立           | `\textup{}`  |
| 倾斜           | `\textsl{}`  |
| 小型大写       | ` \textsc{}` |



### 3. 特殊字符

需要用反斜杠进行转义

 `\#`, `\$`, `\%`, `\&`, `\_` 



### 4. 间距

使用 `\quad` 表示一个空格，`\qquad` 表示两个空格



### 6. 字体大小

改变字体大小，如 `\tiny`, `\small`, `\normalsize`, `\large`, `\Large`, `\LARGE`, `\huge`, `\Huge`。



### 7.章节

对于`ctexart`文件类型

章节可以用`\section{一级标题}`和`\subsection{二级标题}`命令来标记



### 8. 目录

`\tableofcontents`命令可以在指定位置生成目录

通常带有目录的文件需要编译两次，因为需要先在目录中生成.toc文件，再据此生成目录。

```latex
\documentclass[12pt, a4paper, oneside]{ctexart}
\usepackage{amsmath, amsthm, amssymb, graphicx}
\usepackage[bookmarks=true, colorlinks, citecolor=blue, linkcolor=black]{hyperref}

% 导言区

\title{我的第一个\LaTeX 文档}
\author{Dylaaan}
\date{\today}

\begin{document}

\maketitle

\tableofcontents

\section{一级标题}

\subsection{二级标题}

这里是正文. 

\subsection{二级标题}

这里是正文. 

\end{document}
```



### 9. 图片

插入图片需要使用`graphicx`宏包

```latex
\begin{figure}[htbp]
    \centering
    \includegraphics[width=8cm]{图片.jpg}
    \caption{图片标题}
\end{figure}
```

其中，`[htbp]`的作用是自动选择插入图片的最优位置，`\centering`设置让图片居中，`[width=8cm]`设置了图片的宽度为8cm，`\caption{}`用于设置图片的标题。



### 10. 表格

LaTeX中表格的插入较为麻烦，可以直接使用[Create LaTeX tables online – TablesGenerator.com](https://link.zhihu.com/?target=https%3A//www.tablesgenerator.com/%23)来生成。

```latex
\begin{table}[htbp]
    \centering
    \caption{表格标题}
    \begin{tabular}{ccc}
        1 & 2 & 3 \\
        4 & 5 & 6 \\
        7 & 8 & 9
    \end{tabular}
\end{table}
```



### 11. 列表

LaTeX中的列表环境包含无序列表`itemize`、有序列表`enumerate`和描述`description`

以`enumerate`为例

```latex
\begin{enumerate}
    \item 这是第一点; 
    \item 这是第二点;
    \item 这是第三点. 
\end{enumerate}
```

可以自定义`\item`的样式

```latex
\begin{enumerate}
    \item[(1)] 这是第一点; 
    \item[(2)] 这是第二点;
    \item[(3)] 这是第三点. 
\end{enumerate}
```



### 12. 定理环境

定理环境需要使用`amsthm`宏包，首先在导言区加入：

```latex
\newtheorem{theorem}{定理}[section]
```

其中`{theorem}`是环境的名称，`{定理}`设置了该环境显示的名称是“定理”，`[section]`的作用是让`theorem`环境在每个section中单独编号。

在正文中，用如下方式来加入一条定理：

```latex
\begin{theorem}[定理名称]
    这里是定理的内容. 
\end{theorem}
```

其中`[定理名称]`不是必须的。

另外，我们还可以建立新的环境，如果要让新的环境和`theorem`环境一起计数的话，可以用如下方式：

```latex
\newtheorem{theorem}{定理}[section]
\newtheorem{definition}[theorem]{定义}
\newtheorem{lemma}[theorem]{引理}
\newtheorem{corollary}[theorem]{推论}
\newtheorem{example}[theorem]{例}
\newtheorem{proposition}[theorem]{命题}
```

另外，定理的证明可以直接用`proof`环境。



### 13. 页面

最开始选择文件类型时，我们设置的页面大小是a4paper，除此之外，我们也可以修改页面大小为b5paper等等。

一般情况下，LaTeX默认的页边距很大，为了让每一页显示的内容更多一些，我们可以使用`geometry`宏包，并在导言区加入以下代码：

```latex
\usepackage{geometry}
\geometry{left=2.54cm, right=2.54cm, top=3.18cm, bottom=3.18cm}
```

另外，为了设置行间距，可以使用如下代码：

```latex
\linespread{1.5}
```



### 14. 页码

默认的页码编码方式是阿拉伯数字，也可以自己设置为小写罗马数字：

```tex
\pagenumbering{roman}
```

另外，`aiph`表示小写字母，`Aiph`表示大写字母，`Roman`表示大写罗马数字，`arabic`表示默认的阿拉伯数字。如果要设置页码的话，可以用如下代码来设置页码从0开始：

```tex
\setcounter{page}{0}
```



## 数学公式

### 1. 行内公式

行内公式通常使用`$..$`来输入，这通常被称为公式环境，例如：

```tex
若$a>0$, $b>0$, 则$a+b>0$.
```

公式环境通常使用特殊的字体，并且默认为斜体。需要注意的是，只要是公式，就需要放入公式环境中。如果需要在行内公式中展现出行间公式的效果，可以在前面加入`\displaystyle`，例如

```tex
设$\displaystyle\lim_{n\to\infty}x_n=x$.
```



### 2. 行间公式

行间公式需要用`\[..\]`或者`$$..$$`来输入，推荐使用`\[..\]`，输入方式如下：

```tex
若$a>0$, $b>0$, 则
\[
a+b>0.
\]
```

关于具体的输入方式，可以参考[在线LaTeX公式编辑器-编辑器 (latexlive.com)]([在线LaTeX公式编辑器-编辑器 (latexlive.com)](https://www.latexlive.com/))，在这里只列举一些需要注意的。



### 3. 上下标

上标可以用`^`输入，例如`a^n`；下标可以用`_`来输入，例如`a_1` 。

上下标只会读取第一个字符，如果上下标的内容较多的话，需要改成`^{}`或`_{}`。



### 4. 分式

分式可以用`\dfrac{}{}`来输入，例如`\dfrac{a}{b}`。

为了在行间、分子、分母或者指数上输入较小的分式，可以改用`\frac{}{}`，例如`a^\frac{1}{n}`。
