# PlayBook：PlayBook /Runbook 创建过程
本文档仅供参考。 它代表了截至本文档发布之日 Amazon Web Services (AWS) 提供的当前产品和实践，这些产品和做法如有更改，恕不另行通知。 客户有责任对本文档中的信息以及对 AWS 产品或服务的任何使用情况进行自己的独立评估，每种产品或服务都是 “按原样” 提供的，无论是明示还是暗示的担保。 本文档不创建 AWS、其附属公司、供应商或许可方的任何担保、陈述、合同承诺、条件或保证。 AWS 对客户的责任和责任受 AWS 协议的控制，本文档既不是 AWS 与其客户之间的任何协议的一部分，也不修改。

© 2021 Amazon 网络服务公司或其附属公司。 保留所有权利。 本作品根据知识共享署名 4.0 国际许可协议进行许可。

提供此 AWS 内容须遵守 http://aws.amazon.com/agreement 提供的 AWS 客户协议的条款或客户与 Amazon Web Services, Inc. 或 Amazon 网络服务 EMEA SARL 或两者之间的其他书面协议。

## 联系点

作者：`作者姓名`\
批准者：`批准者姓名`\
最后批准日期：2021 年 3 月 25 日

## NIST 800-61r2 阶段

准备

## 执行摘要
本行动手册概述了创建新的游戏手册/运行手册、将文档从草稿过渡到已批准以及使用 GitLab 重新验证要求的过程。

如需创建更高级的行动手册，请参考 [AWS 事件响应行动手册研讨会]（https://gitlab.aws.dev/fredski/aws-incident-response-playbooks-workshop/-/blob/main/playbooks/crypto_mining/EC2_crypto_mining.md）

## 指导

> 维护我们的运行手册以深入了解并快速向客户交付结果非常重要。 Per Matthew Helmke “作为更广泛的实践的一部分，Runbook 帮助我们，所有这些做法都旨在建立可靠性。 使运行手册保持最新是站点可靠性工程的重要组成部分。”
(< https://www.gremlin.com/blog/ensuring-runbooks-are-up-to-date/ >)

我们的团队使用 Github 来管理文档。 看 [参考文献] (.. /playbook_creation_Process.md/ #references) 来查看我们的流程流程的一些缩写步骤。

## 新PlayBook /Runbook

### GUI 程序

* 为流程跟踪创建问题
* 创建一个新的源分支进行工作
* 导航到分支的根
* 选择 “Web IDE” 按钮
* 要创建项目，请突出显示左边距文件夹并选择下拉箭头以获取选项
* 选择 “新建文件”
* 注意：从现有剧本中复制内容以进行格式化可能会有所帮助
* 我们的文档使用 [GitHub 调味降价]（https://github.github.com/gfm/）

* 确保遵守我们的图书馆的标准命名约定
* 游戏手册：`# PlayBook：PlayBook /Runbook `
* 工具指南：`# 工具：ToolName`
* 这是文档中唯一使用标题 1 (H1) 的时间

* 创建指向相关问题的链接
* 示例：`关联问题：(. /问题/1) `

* 完成文档后：
* 添加指向问题中文档的链接作为评论
* 在问题中添加标签 “REVEW”
* 在 “客户通信方法” 中发布包含问题链接的消息，并请求审核/评论。

* 为了使 PlayBook 获得批准，必须至少两 (2) 名团队成员在相关问题中查看并添加了他们的姓名和评论

* 更新和实施对文档的任何建议或更正

* 一旦您的文档经过审核并进行了所有更正，请提交您的文档以便审批流程最终完成。

* 进入问题并将受让人更改为批准人
* 进入这个问题
* 将已提交批准的标签添加到您的问题中
* 在 “受让人” 旁边的右边栏中选择 “编辑”
* 将受让人更改为 “批准者”
* 向 “批准者” 发送说明，让他知道文档已准备好进行最终审查
* 批准后，在自述文件/剧本中添加指向该文档/剧本的链接
* 示例：`[PlayBook 创建过程] (. /docs/PlayBook_creation_Process.md) `
* 提交合并请求

* 注意：请记住，合并请求之前的所有步骤都必须在你的工作分支内完成

* 此任务的 SLA 为提交文档后的 7 个日历日。
* 如果在 SLA 期限内没有收到任何回复以供批准，请通过向 “用户 A”、“用户 B”、“用户 C” 发送铃声说明来上报。

### CLI 程序

待定

## PlayBook /Runbook 更新

### 程序

* 为流程跟踪创建问题
* 创建一个新的源分支进行工作
* 导航到分支的根
* 选择 “Web IDE” 按钮
* 打开一个新问题以跟踪更改的进度
* 删除所有现有标签
* 添加标签草稿
* 创建指向相关问题的链接
* 你可以将你的问题附加到列表中
* 示例：（问题 1）、（问题 1）、（问题 3）

* 完成文档后：
* 添加指向问题中文档的链接作为评论
* 在问题中添加标签 “REVEW”
* 在 “客户通信机制” 中发布包含问题链接的消息，并请求审核/评论。

* 为了使 PlayBook 获得批准，必须至少两 (2) 名团队成员在相关问题中查看并添加了他们的姓名和评论

* 更新和实施对文档的任何建议或更正

* 一旦您的文档经过审核并进行了所有更正，请提交您的文档以便审批流程最终完成。

* 进入问题并将受让人更改为批准人
* 进入这个问题
* 将已提交批准的标签添加到您的问题中
* 在 “受让人” 旁边的右边栏中选择 “编辑”
* 将受让人更改为 “批准者”
* 在 Chime 中发送注释给 “批准者”，让他们知道文档已准备好进行最终审查
* 批准后，在自述文件/剧本中添加指向该文档/剧本的链接
* 示例：`[PlayBook 创建过程] (. /docs/PlayBook_creation_Process.md) `
* 提交合并请求

* 注意：请记住，合并请求之前的所有步骤都必须在你的工作分支内完成

* 此任务的 SLA 为提交文档后的 7 个日历日。
* 如果在 SLA 期限内没有收到任何回复以供批准，请通过向 “用户 A”、“用户 B”、“用户 C” 发送备注进行上报

### CLI 程序

待定

## 审批流程

### 任务所有者：

团队所有者

### 服务级别协议

-作者提交后 7 个日历日

### 程序

* 在 GitHub 中查看文档和相关问题

* 从文档标题中删除 “评论”

* 删除声明这是文档中的草稿行动手册

* 在联系点下
-将您的名称添加/更新到审批人中
-在批准文档时添加/更新 “最后批准日期” 为 YYYY/MM/DD

* 将问题重新分配给申请者
* 在该问题中添加注释说明该手册已获批准，然后继续处理合并请求

## 参考

### 使用 GitHub：创建问题

我们使用问题跟踪正在进行和已完成的工作。 此外，这有助于团队在审核和批准流程中过渡。 这也允许审阅者的评论解决存储库对象中的任何内容，作为我们的文档栏提取过程的一部分。

* 图形用户界面：GUI 允许您从 Web 浏览器与 GitHub 交互以与此存储库进行交互
1. 使用您喜欢的 Web 浏览器导航到 GitHub 存储库
1. 从顶部菜单中选择问题来打开问题
1. 选择 “新问题”
1. 添加标题和说明你正在处理的内容
1. 分配给自己（这将允许在以后的步骤中进行跟踪）
1. 对于里程碑，选择 “此处的客户里程碑”
1. 对于标签，请选择适合您的问题的任何选项
* 对于新文档，请确保选择 “草稿”
1. 选择 “提交问题”
1. 在新的问题页面上，在右边栏中的锁定问题 > 编辑 > 锁定

* 命令行界面：CLI 允许您以命令行形式与 GitHub 进行交互

### 使用 GitHub：创建一个分支以在其中工作

我们在个别分支机构工作，因此正在进行的工作不会干扰其他分支机构的实时工作。

* 图形用户界面：GUI 允许你通过 Web 浏览器与 [GitHub 交互以与此存储库进行交互] (https://docs.github.com/en/github/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository)

* 命令行界面：CLI 允许您以命令行形式与 GitHub 进行交互

### 使用 GitHub：创建合并请求

合并请求允许在与父存储库合并之前进行辅助栏提升者审查。

* [图形用户界面] (https://docs.github.com/en/github/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges)

* 命令行界面：CLI 允许您以命令行形式与 GitHub 进行交互

## 积压项目