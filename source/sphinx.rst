******
Sphinx
******

Sphinx 的简单使用方式
======================

1. 安装
--------
.. code-block:: 

    pip install -U Sphinx

2. 快速构建文档
----------------
.. code-block:: 

    sphinx-quickstart

3. 进行一些项目设置
--------------------
.. code-block:: 
   
    You have two options for placing the build directory for Sphinx output.
    Either, you use a directory "_build" within the root path, or you separate
    "source" and "build" directories within the root path.
    > Separate source and build directories (y/n) [n]: y        
    The project name will occur in several places in the built documentation.
    > Project name:                             # 设置项目名
    > Author name(s): Zhang                     # 设置作者名称
    > Project release []: 0.0.1                 # 设置项目版本号
    > Project language [en]: zh_CN              # 最后设置显示语言                    

设置完了以后按 ``Enter`` 就可以了。

4. 写作
--------
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

5. 生成 html
--------------------

.. code-block:: 

    make html

接着就可以在 build 文件夹 html 文件夹下看到生成的文件，
index.html 就是文件主页。主要代码在 source 文件夹下。

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

reStructuredText sublime text 的三款辅助插件
============================================

OmniMarkupPreviewer (用于解析渲染reST等多种标记语法, 必选 ), 
安装好后, 按快捷键 Ctrl + Alt + O 预览.

reStructuredText Improved (用于语法着色, 可选 , 建议安装 )

Restructured Text (RST) Snippets (用于自动补全, 可选, 但推荐安装 ), 
在制表时很有用。 [1]_

.. [1] `reStructuredText简明教程 <https://iridescent.ink/HowToMakeDocs/Basic/reST.html?highlight=sublime>`_ 

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

Sphinx 部署
===========

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

以下这段英文配置方式来自： [2]_

GitHub

* Go to the ``Settings`` page for your project
* Click ``Webhooks`` > ``Add webhook``
* For **Payload URL**, use the URL of the integration on Read the Docs, found on the project’s ``Admin`` > ``Integrations`` page. You may need to prepend https:// to the URL.
* For **Content type**, both application/json and application/x-www-form-urlencoded work
* Leave the **Secrets** field blank
* Select **Let me select individual events**, and **mark Branch or tag creation**, **Branch or tag deletion** and **Pushes** events
* Ensure **Active** is enabled; it is by default
* Finish by clicking **Add webhook**. You may be prompted to enter your GitHub password to confirm your action.

Payload URL 就是第 6 步所得的地址。

.. [2] `add webhook <https://docs.readthedocs.io/en/stable/webhooks.html#github>`_


这些配置完成后，我们平时只要 push 到 github 仓库就会自动同步到 Read the Docs 更新，相当方便。
