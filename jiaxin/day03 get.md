# GET

![](/home/xin/images/5.png)



![](/home/xin/images/4.png)

0126*

## 什么是GitHub？

GitHub是用于版本控制和协作的代码托管平台。它使您和其他人可以在任何地方共同处理项目。

本教程教您GitHub基本知识，例如*存储库*，*分支*，*提交*和*请求请求*。您将创建自己的Hello World存储库，并学习GitHub的Pull Request工作流程，这是一种创建和查看代码的流行方法。

#### 无需编码

要完成本教程，您需要一个[GitHub.com帐户](http://github.com/)和Internet访问权限。您无需知道如何编码，使用命令行或安装Git（版本控制软件GitHub是基于GitHub构建的）。

> **提示：**在单独的浏览器窗口（或选项卡）中打开本指南，以便在完成教程中的步骤时可以看到它。



## 步骤1.创建存储库

一个**库**通常用于举办单个项目。储存库可以包含文件夹和文件，图像，视频，电子表格和数据集-项目需要的任何内容。我们建议包括*README*或包含有关项目信息的文件。使用GitHub可以轻松地在创建新存储库的同时添加一个。*它还提供了其他常用选项，例如许可证文件。*

您的`hello-world`存储库可以是您存储思想，资源，甚至与他人共享和讨论事物的地方。

### 创建一个新的存储库

1. 在右上角，您的头像或标识旁边，单击 然后选择“ **新建存储库”**。
2. 命名您的存储库`hello-world`。
3. 写一个简短的描述。
4. 选择**使用README初始化此存储库**。

![新形式](https://guides.github.com/activities/hello-world/create-new-repo.png)

单击**创建存储库**。



## 步骤2.创建一个分支

**分支**是一次在不同版本的存储库上工作的方式。

默认情况下，您的存储库有一个名为的分支`master`，该分支被视为权威分支。我们使用分支进行实验并进行修改，然后再将其提交到`master`。

当您在分支机构外创建分支机构时`master`，您正在复制`master`当时的副本或快照。如果`master`在您处理分支时其他人对该分支进行了更改，则可以提取这些更新。

该图显示：

- 该`master`分支
- 一个新的分支称为`feature`（因为我们正在该分支上进行“功能工作”）
- `feature`合并之前的旅程`master`

![分店](https://guides.github.com/activities/hello-world/branching.png)

您是否曾经保存过文件的不同版本？就像是：

- `sudo apt-get upgradestory.txt`
- `story-joe-edit.txt`
- `story-joe-edit-reviewed.txt`

分支在GitHub存储库中实现了相似的目标。

在GitHub，我们的开发人员，作家和设计师使用分支机构将错误修复和功能工作与`master`（生产）分支机构分开。更改准备就绪后，他们会将分支合并到中`master`。

### 创建一个新分支

1. 转到新的存储库`hello-world`。
2. 单击文件列表顶部显示**分支：master**的下拉列表。
3. `readme-edits`在新的分支文本框中输入分支名称。
4. 选择蓝色的“ **创建”分支**框，或在键盘上按“ Enter”。

![分支gif](https://guides.github.com/activities/hello-world/readme-edits.gif)

现在您有两个分支，`master`和`readme-edits`。它们看起来完全一样，但时间不长！接下来，我们将更改添加到新分支。



## 步骤3.进行并提交更改

太棒了！现在，您在`readme-edits`分支的代码视图中，该视图是的副本`master`。让我们进行一些编辑。

在GitHub上，保存的更改称为*commits*。每个提交都有一个关联的*提交消息*，该*消息*是说明为什么进行特定更改的说明。提交消息记录了更改的历史记录，因此其他贡献者可以了解您所做的事情以及原因。

#### 进行并提交更改

1. 单击`README.md`文件。
2. 点击 要编辑的文件视图右上角的铅笔图标。
3. 在编辑器中，写一些关于您自己的信息。
4. 编写描述您所做更改的提交消息。
5. 单击**提交更改**按钮。

![承诺](https://guides.github.com/activities/hello-world/commit.png)

这些更改将仅对您`readme-edits`分支上的README文件进行，因此现在此分支包含的内容不同于`master`。



## 步骤4.打开拉取请求

不错的编辑！现在您已经在分支的分支中进行了更改`master`，您可以打开*拉取请求*。

拉取请求是GitHub上协作的核心。当您打开*请求请求时*，您正在提出更改，并要求某人检查并提取您的贡献并将其合并到其分支中。拉取请求显示两个分支中内容的*差异*或差异。更改，加法和减法以绿色和红色显示。

提交后，即使在代码完成之前，也可以打开请求请求并开始讨论。

通过在请求请求消息中使用GitHub的[@mention系统](https://help.github.com/articles/about-writing-and-formatting-on-github/#text-formatting-toolbar)，您可以要求特定人员或团队提供反馈，无论他们是在大厅还是在10个时区之外。

您甚至可以在自己的存储库中打开拉取请求，然后自己合并它们。这是在进行大型项目之前学习GitHub流程的好方法。

#### 打开请求更改自述文件的请求

*点击图像查看大图*

| 步                                                           | 屏幕截图                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 点击 **“拉取请求”**选项卡，然后从“拉取请求”页面中，单击绿色的“ **新建拉取请求”**按钮。 | [![预标签](https://guides.github.com/activities/hello-world/pr-tab.gif)](https://guides.github.com/activities/hello-world/pr-tab.gif) |
| 在“ **示例比较”**框中，选择`readme-edits`要与`master`（原始）进行比较的分支。 | [![科](https://guides.github.com/activities/hello-world/pick-branch.png)](https://guides.github.com/activities/hello-world/pick-branch.png) |
| 在“比较”页面上的差异中查看您的更改，确保它们是您要提交的。   | [![差异](https://guides.github.com/activities/hello-world/diff.png)](https://guides.github.com/activities/hello-world/diff.png) |
| 如果您对要提交的更改感到满意，请单击绿色的大的**创建请求请求**按钮。 | [![创建拉](https://guides.github.com/activities/hello-world/create-pr.png)](https://guides.github.com/activities/hello-world/create-pr.png) |
| 给您的请求请求一个标题，并写下您所做更改的简短描述。origin/a` | [![形式](https://guides.github.com/activities/hello-world/pr-form.png)](https://guides.github.com/activities/hello-world/pr-form.png) |

完成您的消息后，单击**创建请求请求**！

------

> **提示**：您可以使用[的表情符号](https://help.github.com/articles/basic-writing-and-formatting-syntax/#using-emoji)和[拖放图片和GIF](https://help.github.com/articles/file-attachments-on-issues-and-pull-requests/)到的意见和引入请求。



## 步骤5.合并您的拉取请求

在最后的步骤中，是时候将您的更改集中在一起了–将`readme-edits`分支合并到`master`分支中。

1. 点击绿色的**合并拉取请求**按钮，将更改合并到中`master`。
2. 点击**确认合并**。
3. 继续并删除分支，因为已经合并了其更改，请在紫色框中使用“ **删除分支”**按钮。

![合并](https://guides.github.com/activities/hello-world/merge-button.png) ![删除](https://guides.github.com/activities/hello-world/delete-button.png)

### 庆祝！

通过完成本教程，您已经学会了创建项目并在GitHub上发出拉取请求！

这是您在本教程中完成的工作：

- 创建一个开源存储库
- 开始并管理一个新分支
- 更改了文件并将这些更改提交到GitHub
- 打开并合并拉取请求

查看您的GitHub个人资料，您会看到新的[贡献平方](https://help.github.com/articles/viewing-contributions)！

要了解有关请求请求功能的更多信息，建议阅读[GitHub flow Guide](http://guides.github.com/overviews/flow/)。您还可以访问[GitHub Explore，](http://github.com/explore)并参与一个开源项目。

## 公钥及密钥概念

### 对称加密

　1.对称密钥加密，又称私钥加密，即信息的发送方和接收方用一个密钥去加密和解密数据。它的最大优势是加/解密速度快，适合于对大数据量进行加密，但密钥管理困难。

　2. 采用单钥密码系统的加密方法，同一个密钥可以同时用作信息的加密和解密，这种加密方法称为对称加密，也称为单密钥加密。需要对加密和解密使用相同密钥的加密算法。由于其速度，对称性加密通常在消息发送方需要加密大量数据时使用。对称性加密也称为密钥加密。所谓对称，就是采用这种加密方法的双方使用方式用同样的密钥进行加密和解密。密钥实际上是一种算法，通信发送方使用这种算法加密数据，接收方再以同样的算法解密数据。因此对称式加密本身不是安全的。

　3. 对于普通的对称密码学，加密运算与解密运算使用同样的密钥。通常,使用的对称加密算法比较简便高效，密钥简短，破译极其困难，由于系统的保密性主要取决于密钥的安全性，所以，在公开的计算机网络上安全地传送和保管密钥是一个严峻的问题。正是由于对称密码学中双方都使用相同的密钥，因此无法实现数据签名和不可否认性等功能

