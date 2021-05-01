# 格院毕设LaTeX模板简略说明

## 文件结构

```
.
├── 📁.vscode           vscode配置文件
├── 📁Appendices        各个附录的tex文件文件夹
├── 📁Code              要插入的代码可以放这个文件夹
├── 📁Figures           图片文件夹
├── 📁Front             几个前置页的tex文件文件夹
├── 📁Sections          各个正文章节的tex文件文件夹
├── 📑main.tex          控制页
├── 📑Notations.bib     所有符号, 缩写放在这里
├── 📑sample.pdf        生成出来的pdf该是这样
├── 📑README.md         本说明文件
└── 📑References.bib    所有引用的bibtex放这里
```

关于版式, 使用的包, 颜色等文章设置, 姓名学号, 一导二导名字等信息都在**main.tex**这个控制页中, 在**main.tex**中以`\include{AA/Bb.tex}`语句添加了**Front**下的封面, 信息表格, 摘要, 致谢几个前置页, **Sections**下的几个正文章节以及**Appendices**下的几个附录. 通过在**main.tex**中注释掉相应include语句可以在写论文的时候暂时不生成不必要的部分.

通过像**Notations.bib**中已经给出的例子那样将符号/缩写与含义配对地写在**Notations.bib**中, 以`\gls{xx}`来调用, 可以在文中插入点击能跳转到List of Notations页的符号/缩写. 如果不想放这种东西, 可以**Notations.bib**留空不管.

如果文中想放代码, 可以参考附录2的写法, 将代码放在**Code**文件夹然后用`\inputminted[]{}{}`语句插入代码. `code`这个定义在**main.tex**中的环境是为了让跨页的代码也能有`caption`的. 更具体的用法就需要自己上网搜搜*minted*这个包啦.

在**\.vscode**文件夹中有我在用VSC的LaTeX Workshop插件写LaTeX时用到的配置, 如果你已经安装了完整的TexLive并添加到路径了, 应当直接能用.

## 指定字体

取消**main.tex**中38-41行注释来指定常规字体, 无衬线字体, 等宽字体. 注意*Times New Roman*, *Arial*, *Courier New*这几个字体在Linux系统默认是没有的, 是Windows的字体. 可以换成你电脑上装了的字体的全称填进去.

```latex
\usepackage{fontspec}
\setmainfont{Times New Roman}
\setsansfont{Arial}
\setmonofont{Courier New}
```

## 中文支持

`xelatex`天然支持中文字符的存在, 但是需要取消**main.tex**中36行`\usepackage{xeCJK}`的注释, 输出的pdf中才会在对应处显示出中文. 如果文中不含中文建议还是把这行注释掉.

## 编译

> xelatex ➞ bib2gls ➞ biber ➞ xelatex × 2

在vsc的配置文件中提供了两条编译工具链. 以上面这条为例, **xelatex**是比**pdflatex**功能更强大的pdf生成工具, 支持中文字符, **bib2gls**是根据`.bib`文件生成符号工具, **biber**是比**bibtex**功能更新的引用生成工具, 支持像**References.bib**中已有的`@online`这样的引用类型. 如果不想放符号, 可以不调用**bib2gls**, 用另一条编译工具链. (需要整个注释掉**main.tex**中`list of symbols`一段的设置)

💡 如果你是用VSC的LaTeX Workshop插件进行的编译, 你会发现多了一个**main.synctex.gz** (如果你是以其他方式编译的, 那很有可能多出很多文件), 这个是用于tex源文件与pdf正反向同步用的文件, 删掉了就无法在pdf中按着<kbd>Ctrl</kbd>点到字或者图上跳转到tex文件中对于字段了.

## 小技巧

通过取消**main.tex**第16行的注释, 即给`\documentclass[]{article}`加上draft选项, 会开启草稿模式, 以线框代替图片, 在布局不恰当处用粗黑线标出, 生成也会更快.

取消17行的注释的话会以线条显示出当前布局.



祝学弟学妹们毕业设计顺利, 圆满毕业 💪
