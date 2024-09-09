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
