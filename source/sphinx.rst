***********
Sphinx 安装
***********

.. code-block:: 

    pip install -U Sphinx

*****************
Sphinx 的简单使用
*****************

1. 快速构建文档
===============

新建一个文件夹，命名成自己想要的项目名称。打开命令行，
切换到该文件夹的路径下，运行命令：

.. code-block:: 

    sphinx-quickstart

2. 进行一些项目设置
===================

.. code-block:: 
   
    You have two options for placing the build directory for Sphinx output.
    Either, you use a directory "_build" within the root path, or you separate
    "source" and "build" directories within the root path.
    > Separate source and build directories (y/n) [n]: y
    The project name will occur in several places in the built documentation.
    > Project name:                             # 设置项目名
    > Author name(s): Zhang                     # 设置作者名称
    > Project release []:                       # 设置项目版本号
    > Project language [en]: zh_CN              # 最后设置显示语言

设置完了以后按 ``Enter`` 就可以了。

3. 写作
=======

在 source 文件夹下添加一个 demo.rst 的文件，
然后在 index.rst 上这么修改：

.. raw:: html

    <pre>
    .. toctree::
        :maxdepth: 3
        :caption: 详细内容:

        demo.rst    # 新增
    </pre>

然后就可以在 demo.rst 用 reStructuredText 标记语言进行写作了。

4. 生成 html
============

.. code-block:: 

    make html

接着就可以在 build 或者是 _build 文件路径 html 文件夹下看到生成的文件，
index.html 就是文件主页。主要代码在 source 文件夹下。


***************
Sphinx 部分语法
***************

分割线
======

使用单横线为分割线，和 markdown 一样。但是该线上下两行最好不要有字符串。

.. code-block::

    ---------


**********************************
Sphinx 使用 LaTeX 引擎渲染数学公式
**********************************

添加插件
========

首先，要在 conf.py 中添加数学引擎，如:

.. code-block:: python

    # conf.py
    extensions = [
        'sphinx.ext.mathjax',
    ]

然后，我们就可以在 html 里面编写基于 LaTeX 的数学公式了，格式如下：

行间公式
=========

行间公式格式

.. code-block::

    .. math::
        # write the math code here


行内公式
==========

行内公式格式

.. code-block::

    :math:`# write the math code here`


示例
====

行间公式显示效果：

.. math::
    f'(x) = \lim_{\triangle x \to 0} \frac{f(x + \triangle x) - f(x)}{\triangle x}

行内公式显示效果：

:math:`f'(x) = \lim_{\triangle x \to 0} \frac{f(x + \triangle x) - f(x)}{\triangle x}`


行间公式代码：

.. code-block:: LaTeX

    .. math::
        f'(x) = \lim_{\triangle x \to 0} \frac{f(x + \triangle x) - f(x)}{\triangle x}


行内公式代码：

.. code-block:: LaTeX

    :math:`f'(x) = \lim_{\triangle x \to 0} \frac{f(x + \triangle x) - f(x)}{\triangle x}`


*************************
Sphinx 常见问题及解决方式
*************************


部分常用的 reStructuredText 标记
================================

.. code-block:: 

    引用：         [1]_            .. [1] 
    脚注：         [#f1]_          .. [#f1]
    强制换行：     | string  

.. warning:: 在使用引用和脚注时，中括号的后面必须带至少一个空格，不然无法正常生成 html 文件。


如何固定主题 alabaster 的侧边栏
===============================

在该项目的 conf.py 下加入以下语句

.. code-block:: python3

    html_theme_options = {
        'fixed_sidebar': True,
    }

附：`alabaster 主题文档地址 <https://alabaster.readthedocs.io/en/latest/customization.html#theme-options>`_ 


如何取消主页的 Page source 链接
===============================

在该项目的 conf.py 下加入以下语句

.. code-block:: python3

    html_show_sourcelink = False


如何个性化网页图标(设置 favicon)
==================================

将目标图片 favicon.ico 放入 _static 文件夹内，然后
在该项目的 conf.py 下加入以下语句

.. code-block:: python3

    html_favicon = '_static/favicon.ico'


如何更新默认的CSS
=================

此方法来自： `How to add custom css file to Sphinx? <https://stackoverflow.com/questions/23462494/how-to-add-custom-css-file-to-sphinx#answer-37980230>`_ 

在 _static 文件夹下新建一个 my_style.css 的文件。在该文件中写上自己想增加的自定义的 css style，比如：

.. code-block::

    a:visited {
        color: none;
    }

在 conf.py 文件中增加以下代码：

.. code-block:: python

    def setup(app):
        app.add_css_file('_static/my_style.css')


.. note:: 这种方法的 css 不会破坏原来已有的 css。如果设置了相同的属性，my_style.css 会覆盖掉原来的属性。另有一种通过设置 html_style 的方法直接取消掉默认的 css 完全用自己的 css 代替的方式，我觉得不理想。还是这种方式比较好！


reStructuredText sublime text 的三款辅助插件
============================================

OmniMarkupPreviewer (用于解析渲染reST等多种标记语法, 必选 ), 安装好后, 按快捷键 Ctrl + Alt + O 预览。该插件的浏览器预览是动态预览，每当你编辑目标文件的时候，浏览器都会动态显示你编辑的内容。

reStructuredText Improved (用于语法着色, 可选 , 建议安装 )

Restructured Text (RST) Snippets (用于自动补全, 可选, 但推荐安装 ), 
在制表时很有用。 [1]_

.. [1] `reStructuredText简明教程 <https://iridescent.ink/HowToMakeDocs/Basic/reST.html#id10>`_ 


补全插件 Restructured Text (RST) Snippets
=========================================

该插件的 github 地址 `github 地址 <https://github.com/mgaitan/sublime-rst-completion>`_ ，里面详细介绍了使用方式和快捷键，特别是对于表格的使用很方便，需要用到表格时最好看一下。

该插件的突出优点：表格，标题 mark 的自动补全(tab)，以及标题的升降级都有相应的快捷键，可以很好缩短编写时间。

该插件的安装虽然可以直接从 Package Control 安装，但是从 Package Control 安装的话就我观察无法修改快捷键。因为【标题的升降级】快捷键和默认的 sublime text 快捷键有冲突(也可能是我安装了某些插件的缘故) [#f1]_ 。但是问题是无法修改，这就很伤。
所以推荐另一种安装方式。就是直接在 github 下载源码，解压放到 sublime text 默认插件安装的文件夹下就可以了。一般该文件夹的路径大致如下：

.. code-block::

    C:\Users\Administrator\AppData\Roaming\Sublime Text 3\Packages\User

有可能需要重启 sublime text 才能完成安装。总之这样安装完后就能随意改变快捷键了。

.. note:: .. [#f1] 后来我发现，【标题的升降级】有两种快捷键，一种和默认冲突，另一种是按小键盘的 ``ctrl++`` 和 ``ctrl+-`` 则可以正常工作。所以如果在有小键盘的情况下，安装其实完全可以直接用 Package Control 的方式安装，因为比较省事。虽然不完美。


如何使用原始的 html 标签
========================

.. code-block:: python3

    .. raw:: html

        html tag


如何支持中文搜索
================

| Sphinx 默认是不支持中文搜索的。
| 要支持中文搜索需要用到 jieba 模块。
| 使用起来很简单。

1.安装

.. code-block:: python3

    pip install jieba

2.使用
在 conf.py 文件的最后一行加上

.. code-block:: python3

    html_search_language = 'zh'

然后重新生成就可以了。

源： `sphinx doc正式支持中文搜索啦 <https://www.chenyudong.com/archives/sphinx-doc-support-chinese-search.html>`_ 


Sphinx 生成 PDF
===============

个人心得
--------

有必要在这里先写上个人心得：环境搭建太麻烦，结果输出不够理想！

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


****************
Sphinx make 命令
****************

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

***************************
Sphinx 语法高亮支持的关键字
***************************

`Code blocks with syntax highlighting <https://docs.typo3.org/m/typo3/docs-how-to-document/main/en-us/WritingReST/Codeblocks.html#available-lexers>`_ 

***********
Sphinx 部署
***********

.. _Read the Docs: https://readthedocs.org/

简要说明一下如何将已经写好的 Sphinx 文档部署到互联网上，主要是通过 `Read the Docs`_  这个网站部署的。该网站免费托管一些开源文档，所以在 github 里面的 private 项目的文档在这里是无法托管的。

1.到该网站(`Read the Docs`_)下注册一个账号；

2.在 github 新建一个项目，以下用 <address> 来表示在此处获得的 https 地址；

3.在本地用 sphinx-quickstart 新建 sphinx 项目，然后和正常一样在里面写文档。

4.在该项目的根路径(运行 make html)下初始化 git，并添加 .gitignore

.. code-block:: bash

    git init
    touch .gitignore

在 .gitignore 里面忽略掉 build 文件夹，因为该文件夹是生成 html 的文件夹，上传到 github 这个文件夹是不需要上传的。我们后续配置好 webhook 以后每一个 push 到远端的 commit 都会自动同步更新到 Read the Docs，不需要我们手动更新。

.. code-block::

    # .gitignore
    build/

5.添加远程仓库路径并将已经写好的文档推送；

注：这里略过了 add 和 commit 的步骤

.. code-block:: bash

    git remote add origin <address>
    git push origin master

6.在 `Read the Docs`_ 自己的账号下导入项目

``Import a project`` >> ``手动导入``

| 然后可以看到需要填一个表单：
| 名称：随便填，但是貌似不能填中文；
| 地址：上面生成的 <address>

填好好点击 ``下一页`` 之类的一直点下去就行。成功的话最后可以看到一个地址，类似于下面这个：

.. code-block::

    https://readthedocs.org/api/v2/webhook/XXXXX/

7.添加 webhook

2023-11-15 15:51:43 Update

以下这段英文配置方式来自： add webhook [2]_


- Go to the **Settings** page for your **GitHub project**
- Click **Webhooks** > **Add webhook**
- For **Payload URL**, use the URL of the integration on your **Read the Docs project**, found on the project’s **Admin** > **Integrations** page. You may need to prepend *https://* to the URL.
- For **Content type**, both *application/json* and *application/x-www-form-urlencoded* work
- Fill the **Secret** field with the value from the integration on Read the Docs
- Select **Let me select individual events**, and mark **Branch or tag creation**, **Branch or tag deletion**, **Pull requests** and **Pushes** events
- Ensure **Active** is enabled; it is by default
- Finish by clicking **Add webhook**. You may be prompted to enter your GitHub password to confirm your action.

.. [2] `add webhook <https://docs.readthedocs.io/en/stable/guides/setup/git-repo-manual.html#manual-integration-setup>`_


这些配置完成后，我们平时只要 push 到 github 仓库就会自动同步到 Read the Docs 更新，相当方便。
