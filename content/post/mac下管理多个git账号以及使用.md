# mac下管理多个git账号以及使用
## 使用ssh免密管理git
生成git账号对应的公私钥
以github为例
```shell
# 进入ssh目录
cd /Users/{accountname}/.ssh/
# 生成 SSH key
ssh-keygen -t rsa -C "abc@qq.com"
# 出现以下提示
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/{username}/.ssh/id_rsa):
# 此时输入目录:/Users/{username}/.ssh/id_rsa_github_abc
Enter file in which to save the key (/Uses/{username}/.ssh/id_rsa): /Users/{username}/.ssh/id_rsa_github_abc
# 继续回车,直到出现：
The key s randomart image is:
+---[RSA 2048]----+
|        o o..=+o |
|       . @. + o X|
|        B..B o   |
|       . oB B . E|
|        So X = + |
|        ..* X o .|
|       ..+ O o   |
|        o.* .    |
|        .o .     |
+----[SHA256]-----+
# 将生成的公钥拷贝到剪贴板上，到github管理ssh的页面贴入即可
pbcopy < ~/.ssh/id_rsa_github_abc.pub
# 将生成的私钥添加到ssh中
ssh-add ~/.ssh/id_rsa_github_abc
# 查看是否添加成功
ssh-add -l
# 测试是否成功
ssh -T git@github.com

```

针对多账号管理，需要配置config

```shell
# 进入ssh目录
cd /Users/{accountname}/.ssh/
# 打开或创建config文件
vim config
# 添加如下配置内容
Host github_abc
HostName github.com
PreferredAuthentications publickey
user git
#user abc@qq.com
IdentityFile ~/.ssh/id_rsa_github_abc
# 如果还有别的账号，参考该配置添加即可
Host github_ddd
HostName github.com
PreferredAuthentications publickey
user git
#user ddd@qq.com
IdentityFile ~/.ssh/id_rsa_github_ddd


```

拉取仓库
```shell
# 原先github中的ssh地址为
git clone git@github.com:abc/test.git
# 需要修改为别名
git clone github_abc:abc/test.git
# 其它git提交正常操作即可
```

如果是之前已经克隆的仓库，需要手动修改git地址
```shell
vim .git/config
# 修改url
[remote "origin"]
        url = git@github_abc:abc/test.git

```
## 单独git账号下的管理，设置全局方式
git config --global user.name "xxx"  # 配置全局用户名，如Github上注册的用户名
git config --global user.email "yyy@mail.com"  #配置全局邮箱，如Github上配置的邮箱
## 重置
git config --global --unset user.name
git config --global --unset user.email
## 查询
git config --global user.name
git config --global user.email



