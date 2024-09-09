
**************
用得较少的笔记
**************


Sphinx 语法高亮支持的关键字
===========================

`Code blocks with syntax highlighting <https://docs.typo3.org/m/typo3/docs-how-to-document/1.0/en-us/WritingReST/Reference/Code/Codeblocks.html>`_ 


Sphinx make 命令
================

我们可以通过 make 来看 sphinx 到底支持了多少选项。

.. code-block:: 

    $make
    Sphinx v4.3.2
    Please use `make target' where target is one of
      html        to make standalone HTML files
      dirhtml     to make HTML files named index.html in directories
      singlehtml  to make a single large HTML file
      pickle      to make pickle files
      json        to make JSON files
      htmlhelp    to make HTML files and an HTML help project
      qthelp      to make HTML files and a qthelp project
      devhelp     to make HTML files and a Devhelp project
      epub        to make an epub
      latex       to make LaTeX files, you can set PAPER=a4 or PAPER=letter
      text        to make text files
      man         to make manual pages
      texinfo     to make Texinfo files
      gettext     to make PO message catalogs
      changes     to make an overview of all changed/added/deprecated items
      xml         to make Docutils-native XML files
      pseudoxml   to make pseudoxml-XML files for display purposes
      linkcheck   to check all external links for integrity
      doctest     to run all doctests embedded in the documentation (if enabled)
      coverage    to run coverage check of the documentation (if enabled)
      clean       to remove everything in the build directory

| 个人注解：
| make html: **最常用选项，生成标准的 html 文件**
| make singlehtml: 和 make html 相比，生成了单独一个大的 html 文件。并且少了最前面的一页导航栏。个人觉得导航栏还是很重要的。
| make clean: 今天(2022-01-06)才知道有这个选项，删除掉生成文件夹里的内容。平时在添加一个新的文档进去的时候，就需要删除掉 make html 生成的文件重新生成。才能拥有正常的侧边栏。但感觉这个命令挺危险的，如果有制作 htmlhelp 文件的话，一般都是需要处理过 htmlhelp 文件，这样一来，就可能连同这个也被删除掉了。**感觉这个命令少用为妙，要删除手动删除比较妥当！**


Sphinx 生成 PDF
===============

个人心得
--------

有必要在这里先写上个人心得：环境搭建太麻烦，结果输出不够理想！真的没什么用！

latex 环境安装
--------------

在 Windows 下需要安装 latex 环境

#. 安装 Miktex 软件，软件文件名为 basic-miktex-21.12-x64.exe

#. Miktex 需要 perl 环境，所以还要安装 perl 环境。

    * perl 环境安装 strawberryperl
    * 软件名：strawberry-perl-5.32.1.1-64bit.msi
    * 验证安装成功：在命令行界面输入 perl --version

命令行生成
----------

切换到项目主目录下，运行

.. code-block:: bash

    make latex

将命令行目录切换到 build/latex/ 下，再运行

.. code-block:: bash

    make

首次运行需要安装很多插件，将显示弹出窗口的勾去掉，就会自动安装到完。下次运行相对就快了。

.. note:: 生成的文件在当前目录下，总体来说挺不错，生成的目录我个人相当喜欢。不过字体太小了，目前不知道怎么调，不够理想！ **个人还是不太喜欢通过这种方式生成的 pdf，总体来说不太理想！并且环境搭建过程实在是太麻烦了！**
