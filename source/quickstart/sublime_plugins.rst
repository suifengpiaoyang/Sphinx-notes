.. index:: Sublime Text 插件

****************
Sublime Text插件
****************

如果你使用的是 Sublime Text 编辑器的话，可以考虑安装并尝试使用这些插件。

这些 Sublime Text 的插件主要用于方便编写 reStructuredText 语法。 Sphinx 使用的是 reStructuredText 语法，感觉没有 markdown 语法简单容易编写，当然，编写习惯以后也没有多大差别。但是使用一些插件可以让编写过程变得更加简单，或许也不错。

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
