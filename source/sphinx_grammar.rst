***********
Sphinx 语法
***********


分割线
======

使用单横线为分割线，和 markdown 一样。但是该线上下两行最好不要有字符串。

.. code-block::

    ---------

.. index:: T-显示图片

显示图片
=========

显示图片的默认代码格式：

.. code-block::

    .. figure:: image_path

       caption

可以通过参数改变显示的图片的大小和标题。

示例：

将目标图片放到 _static 文件夹下，通过

.. code-block::

    .. figure:: _static/SigmoidFunction.png
        :alt: Sigmoid Function
        :width: 540
        :height: 300

        Sigmoid Function

这种方式来显示图片。

weight 和 height 可以只设置一个，以保留原来的图片比例。

.. index:: S-索引

增加索引
==========

Sphinx 索引这个功能十分好用，以前我却从没用过。在 Sphinx 里面增加索引也十分简单。

首先，我们要保证 index.rst 里面的这部分代码还在：

.. code-block::

    索引
    =====

    * :ref:`genindex`
    * :ref:`search`

主要是 `genindex` 这个要存在。接着我们在编写的笔记里面要加索引的地方，写上

.. code-block::

    .. index:: Keyword

在这里，需要注意几方面的内容：

1. `.. index::` 这个标头写上后，`genindex` 会自动生成相关的链接；
2. `.. index::` 可以写在笔记的任何地方，生成的链接会跳转到目的地，不一定要写在标题之前；
3. `Keyword` 部分支持中文和空格，但是在生成之后，因为中文不像英文只有26个分类，当关键词一多，会变得十分混乱。所以，在写中文关键词的时候，可以加上一些前缀，比如可以加上 `Z-` 前缀，变成 `Z-Keyword` 这种形式。到时候所有词会归类到 Z 这系列里面。

编写完我们想要的 `.. index::` 之后，只需要编译一次就可以在文档首页看到相关的可访问的标签链接了。

我们可以将一些常用的定义成标签，这使得文档的使用效率变得很高！

.. index:: J-交叉引用

交叉引用
========

锚点的放置
----------

下面的 `_random-seed` 是我自定义写的，你要写成自己想要的名字。

.. code-block::

    .. _random-seed:

锚点的放置可以看到它遵循一定的格式。上面除了 `random-seed` 之外，都是格式。第一个单下划线也算。

这个锚点一般放置在标题前面。

锚点的引用
----------

.. code-block::

    :ref:`random-seed`

我们可以在其他文档的任何地方直接使用上面的方式，将锚点引用到目标位置。

.. index:: S-数学公式

渲染数学公式
============

配置
-------

首先，在配置文件中添加插件。

在 conf.py 中添加数学引擎:

.. code-block:: python

    # conf.py
    extensions = [
        'sphinx.ext.mathjax',
    ]

然后，我们就可以在 html 里面编写基于 LaTeX 的数学公式了，格式如下：

行内公式
--------

行内公式格式

.. code-block::

    :math:`# write the math code here`

行间公式
--------

行间公式格式

.. code-block::

    .. math::
        # write the math code here

示例
------

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

部分有用的语法
================

.. code-block:: 

    引用：         [1]_            .. [1] 
    脚注：         [#f1]_          .. [#f1]
    强制换行：     | string  

.. warning:: 在使用引用和脚注时，中括号的后面必须带至少一个空格，不然无法正常生成 html 文件。
