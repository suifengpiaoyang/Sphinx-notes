***************
Sphinx 实用场景
***************

如何固定主题 alabaster 的侧边栏
===============================

在该项目的 conf.py 下加入以下语句

.. code-block:: python3

    html_theme_options = {
        'fixed_sidebar': True,
    }

固定侧边栏以后，默认的显示模式仍然存在问题。所以我们还需要增加自定义的 CSS:

:ref:`custom_css`

.. code-block:: CSS

    a:visited {
        color: none;
    }

    div.sphinxsidebar {
        max-height: 93%;
        overflow-y: auto;
    }


附：`alabaster 主题文档地址 <https://alabaster.readthedocs.io/en/latest/customization.html#theme-options>`_ 


如何给 alabaster 增加索引
=========================

:download:`点击下载<_static/_templates.7z>`  

模板文件，解压后复制进项目的 source 文件夹中，重新编译就好。我们就可以在侧边栏的最上方看到一个索引的链接。

如何取消主页的 Page source 链接
===============================

在该项目的 conf.py 下加入以下语句

.. code-block:: python3

    html_show_sourcelink = False


.. index:: T-图标

如何个性化网页图标(设置 favicon)
==================================


将目标图片 favicon.ico 放入 _static 文件夹内，然后
在该项目的 conf.py 下加入以下语句

.. code-block:: python3

    html_favicon = '_static/favicon.ico'


.. index:: Z-自定义CSS

.. _custom_css:

如何使用自定义的CSS
===================

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

sphinx 版本更新后，需要写成

.. code-block:: python

    def setup(app):
        app.add_css_file('my_style.css')

.. note:: 这种方法的 css 不会破坏原来已有的 css。如果设置了相同的属性，my_style.css 会覆盖掉原来的属性。另有一种通过设置 html_style 的方法直接取消掉默认的 css 完全用自己的 css 代替的方式，我觉得不理想。还是这种方式比较好！


如何使用原始的 html 标签
========================

.. code-block:: python3

    .. raw:: html

        html tag


.. index:: Z-中文搜索

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

.. index:: X-下载链接

如何添加下载链接
================

把自己想要做成的下载文件打包成单独一个文件，比如 download.zip，然后将其放到项目路径下的 source/_static 路径下。于是我们可以通过这种方式来创建下载链接：

.. code-block:: rst

   :download:`点击下载示例文件<_static/download.zip>`
