# 如何贡献代码和文档
### 开始之前
github或社区提交问题
欢迎为项目贡献任何代码或文档，但是建议先在github或社区上提交一个问题，和大家共同讨论。

### 签署贡献者许可协议(CLA)
什么是CLA？

签署协议链接：seccome inc. Contributor License Agreement

单击按钮**Sign in with GitHub to agree**签署协议。

如果有任何问题，请发送邮件至ask@seccome.com。


### 修改单篇文档
Ehoney文档以Markdown语言编写。单击文档标题右侧的铅笔图标即可提交修改建议。该方法仅适用于修改单篇文档。

### 批量修改或新增文件
该方法适用于贡献代码、批量修改多篇文档或者新增文档。

###### Step 1：通过GitHub fork仓库
ehoney项目有很多仓库，以gh-pages仓库为例：

访问https://github.com/seccome/Ehoney/tree/gh-pages。

在右上角单击按钮Fork，然后单击用户名，即可fork出以gh-pages仓库。

###### Step 2：将分支克隆到本地
定义本地工作目录。


1.定义工作目录。
```shell
working_dir=$HOME/Workspace
```
2.将user设置为GitHub的用户名。
```shell
user={GitHub用户名}
```
3.克隆代码。
```shell
mkdir -p $working_dir
cd $working_dir
git clone https://github.com/$user/ehoney-graph.git
# 或：git clone git@github.com:$user/ehoney-graph.git

cd $working_dir/ehoney
git remote add upstream https://github.com/seccome/ehoney-graph.git
# 或：git remote add upstream git@github.com:seccome-inc/ehoney-graph.git

# 由于没有写访问权限，请勿推送至上游主分支。
git remote set-url --push upstream no_push

# 确认远程分支有效。
# 正确的格式为：
# origin    git@github.com:$(user)/ehoney-graph.git (fetch)
# origin    git@github.com:$(user)/ehoney-graph.git (push)
# upstream  https://github.com/vesoft-inc/ehoney-graph (fetch)
# upstream  no_push (push)
git remote -v
```

4.(可选)定义pre-commit hook。

请将ehoney Graph的pre-commit hook连接到.git目录。
hook将检查commit，包括格式、构建、文档生成等。

```shell
cd $working_dir/ehoney-graph/.git/hooks
ln -s $working_dir/ehoney-graph/.linters/cpp/hooks/pre-commit.sh 
```
pre-commit hook有时候可能无法正常执行，用户必须手动执行。
```shell
cd $working_dir/ehoney-graph/.git/hooks
chmod +x pre-commit
```

###### Step 3：分支
1.更新本地主分支。
```shell
cd $working_dir/ehoney
git fetch upstream
git checkout master
git rebase upstream/master
```
2.从主分支创建并切换分支：

```shell
git checkout -b myfeature
```

>由于一个PR通常包含多个commit，在合并至master时容易被挤压（squash），因此强烈建议创建一个独立的分支进行更改。合并后，这个分支可以被丢弃，因此可以使用上述rebase命令将本地master与upstream同步。此外，如果直接将commit提交至 master，用户可以需要在master分支使用hard reset，例如：
git fetch upstream
git checkout master
git reset --hard upstream/master
git push --force origin master

###### Step 4：开发
1.代码风格
ehoney Graph采用cpplint来确保代码符合Google的代码风格指南。检查器将在提交代码之前执行。

2.单元测试要求
请为新功能或Bug修复添加单元测试。
构建代码时开启单元测试
详情请参见使用源码安装ehoney Graph。

>请确保已设置-DENABLE_TESTING = ON启用构建单元测试。

3.运行所有单元测试
在ehoney根目录执行如下命令：

```shell
cd ehoney/build
ctest -j$(nproc)
```

###### Step 5：保持分支同步
```shell
# 当处于myfeature分支时。
git fetch upstream
git rebase upstream/master
```
在其他贡献者将PR合并到基础分支之后，用户需要更新head分支。

###### Step 6：Commit
提交代码更改：

```shell
git commit -a
```
用户可以使用命令--amend重新编辑之前的代码。

###### Step 7：Push
需要审核或离线备份代码时，可以将本地仓库创建的分支push到GitHub的远程仓库。
```shell
git push origin myfeature
```

###### Step 8：创建pull request
1.访问fork出的仓库https://github.com/$user/ehoney-graph (替换此处的用户名$user)。

2.单击myfeature分支旁的按钮Compare & pull request。

###### Step 9：代码审查
pull request创建后，至少需要两人审查。审查人员将进行彻底的代码审查，以确保变更满足存储库的贡献准则和其他质量标准。

### 添加测试用例
添加测试用例的方法参见How to add test cases。

### 捐赠项目
###### Step 1：确认项目捐赠Step 1：确认项目捐赠
通过邮件、微信、等方式联络ehoney官方人员，确认捐赠项目一事。项目将被捐赠至ehoney组织下。

邮件地址：ask@seccome.com
微信：seccome

###### Step 2：获取项目接收人信息
由ehoney官方人员给出ehoney的项目接收者ID。

###### Step 3：捐赠项目
由您将项目转移至本次捐赠的项目接受人，并由项目接收者将该项目转移至ehoney组织下。捐赠后，您将以Maintain角色继续主导社区项目的发展。

GitHub上转移仓库的操作，请参见Transferring a repository owned by your user account。