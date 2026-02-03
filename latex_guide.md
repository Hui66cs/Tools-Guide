注释：%

换段：代码里空一行，文字会自动缩进。若段落开头写\noindent则取消缩进。
段落内强制换行： 结尾加上\\，或第二行开头加\newline,但都不会有缩进
强制换页：\newpage

\documentclass{ctexart} % [导言区] 指定文档类型（ctexart 支持中文）

\usepackage{amsmath}   % 处理数学公式的宏包

\title{文章标题}
\author{你的名字}
\date{\today}

\begin{document}       % [正文区] 开始
\maketitle             % 打印标题页

这里写你的具体内容...

\end{document}         % [正文区] 结束

语法：
\textbf{加粗文本}          加粗
\textit{斜体文本}          斜体
\underline{下划线文本}      下划线  
\paragraph{段落标题}      段落标题
\section{章节标题}         章节标题
\subsection{小节标题}      小节标题 
\subsubsection{子小节标题}  子小节标题

\begin{itemize}         无序列表
    \item 第一项
    \item 第二项
\end{itemize}

\begin{enumerate}       有序列表
    \item 第一项
    \item 第二项
\end{enumerate}

数学公式：
行内公式：$E=mc^2$
行间公式： \[ E=mc^2 \]
编号公式：
\begin{equation}
E=mc^2
\end{equation}

数学公式规则：
1. 上标：使用^符号，如x^2表示x的平方
2. 下标：使用_符号，如a_i表示a的第i个元素
3. 分数：使用\frac{分子}{分母}，如\frac{a}{b}
4. 根号：使用\sqrt{表达式}，如\sqrt{x+1}
5. 求和：使用\sum_{下限}^{上限}，如\sum_{i=1}^{n} i  --大sigma求和符号
6. 积分：使用\int_{下限}^{上限}，如\int_{0}^{1} x^2 \, dx  --积分符号
7. 希腊字母：如\alpha, \beta, \gamma, \pi, \theta, \mu 等

插入图片：
\usepackage{graphicx}  % 在导言区引入 graphicx 宏

\begin{figure}[htbp]
    \centering
    \includegraphics[width=0.9\textwidth]{路径}
    \caption{图片说明（显示在图片正下方）}
    \label{fig:命名，用于引用}
\end{figure}

**左右子图的大图：**
\usepackage{subcaption} % 在导言区引入宏包

\begin{figure}[htbp]
    \centering
    \begin{subfigure}[b]{0.45\textwidth}
        \centering
        \includegraphics[width=\textwidth]{路径1}
        \caption{子图1说明}
    \end{subfigure}
    \hfill % 在两个子图之间加点间距
    \begin{subfigure}[b]{0.45\textwidth}
        \centering
        \includegraphics[width=\textwidth]{路径2}
        \caption{子图2说明}
    \end{subfigure}
    \caption{大图总说明}
\end{figure}

引用图片：见图\ref{fig:lable名}
引用公式：见公式\ref{eq:label名}
引用表格：见表\ref{tab:label名}

插入表格：
\begin{table}[htbp]
    \centering
    \caption{表格说明}           放在上面则表格说明显示在表格上方，放在下面则显示在表格下方，表格说明一般放在上方，图片说明一般放在下方
    \begin{tabular}{|c|c|c|}
        \hline
        列1 & 列2 & 列3 \\        
        \hline
        数据1 & 数据2 & 数据3 \\
        数据4 & 数据5 & 数据6 \\
        \hline
    \end{tabular}
    \label{tab:label名}
\end{table}

解释：
\\表示换行，一行结束
&表示列与列之间的分隔
\begin{tabular}{|c|c|lr} :每个字母代表一列，|代表两列之间竖线分隔，c代表居中，l代表左对齐，r代表右对齐。
\hline : 普通表格横线
想要更精美、专业的横线，可以\usepackage{booktabs}
\toprule : 表格最上方的横线，较粗
\midrule : 表格中间的横线，较细
\bottomrule : 表格最下方的横线，和顶线一样粗


插入代码：
\usepackage{listings}   插入宏包

\begin{lstlisting}[language=Python, caption=我的代码]
print("Hello LaTeX")  --代码区
\end{lstlisting}