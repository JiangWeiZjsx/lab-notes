# Research-Notes （科研笔记）

科研相关学习笔记

# 绘图软件

绘图软件分为两类，一类是结果分析图，如点线图、箱线图等；另一类是流程示意图，如框架图、流程图等。

- origion

缺点：收费，部分学校提供学生版本。需要找资源安装破解版。

- Affinity

矢量图画图软件

# 论文写作

Latex $+$ Pandoc

- 中英文混排
```latex
\documentclass[12pt,a4paper,quiet]{ctexart}
\setlength{\marginparwidth}{2cm} % 确保待办事项和类似包的页边距足够宽

\usepackage[
    a4paper,
    top=2.54cm,
    bottom=2.54cm,
    left=3.17cm,
    right=2.54cm,
    headheight=0.8cm,
    headsep=0.4cm,
]{geometry}
```
- 目录
```latex
% 目录（自动生成）
\clearpage
\renewcommand{\contentsname}{目录} % 修改目录标题为“目录”
\setcounter{tocdepth}{3} % 目录深度：1=节，2=小节
\phantomsection % 使 hyperref 定位正确
\tableofcontents
```
- 代码显示
```latex
\usepackage{listings} % 支持代码块插入

\lstset{
    language=Python,          % 默认语言
    basicstyle=\footnotesize\ttfamily, % 代码字体和大小
    numbers=left,             % 在左侧显示行号
    numberstyle=\tiny\color{codenumbergray}, % 行号样式
    frame=single,             % 给代码块添加边框
    framesep=4pt,             % 边框和代码的距离
    tabsize=4,                % Tab 键占用的空格数
    showstringspaces=false,
    commentstyle=\color{codegray}\ttfamily, % 注释颜色（不使用斜体以避免中文斜体缺失）
    keywordstyle=\color{blue}\bfseries, % 关键词颜色和加粗
    stringstyle=\color{orange},
    breaklines=true,
    captionpos=b,             % 标题位置在底部
    rulecolor=\color{black},
}

\begin{lstlisting}[caption={代码示意}, language=Python, label=lst:grangerFunc]
    # 代码内容
\end{lstlisting}
```
> 注意：代码样式会对全文的行号样式进行修改，导致代码框的行号出现数字错乱的现象


## Pandoc
将 latex 文件转为所需文件，以下以 tex -> word 为例。

```shell
pandoc file_name.tex --citeproc --bibliography=ref.bib --csl=Ref/reference.csl --metadata=link-citations:true --reference-doc=Ref/reference.docx -o out.docx
```

> `cls`, `docx` 文件见 `pandoc/Ref` 文件夹。`bib` 文件为文献，可用 `zotero` 等其他文件管理工具直接导出。

## latex 做PPT Beamer


# 文献管理

Zotero 插件

* Better BibTex for Zotero - 导出bitex
* Translate for Zotero - 翻译
* Ethereal Style - 期刊信息
* GB2312 参考文献 - 见 `./zotero/`


# 图片管理

Eagle

缺点：收费

# 代码编写

## VSCode

免费的代码编写工具，适配大多数编程语言。

## Docker

* 编译 dockerfile 文件
```bash
docker build -t a1-pytorch .
```

* 备份 docker 安装后文件
```bash
docker save -o phd-latex-backup.tar phd-latex:latest
```

* 运行 docker 容器（带GPU）
```bash
docker run --gpus all -it -v ${PWD}:/app --name my_research a1-pytorch:latest bash
```

- 上传本地仓库到 docker hub:

```bash
docker tag a1-pytorch:latest johnwing/a1pytorch:tagname
docker push johnwing/a1pytorch:tagname
```