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
