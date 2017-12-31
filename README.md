
# git配置用户名和密码

### 配置用户名和邮箱（初次必须配置，否则push代码会提示 please tell me who you are.）
** 初次使用git，需要配置用户名和密码，用以链接对应远程仓库的用户。

 ```
 git config --global user.name "yourusername"
 
 git config --global user.email "youruseremail"
 ```
### 配置ssh密钥，免去每次提交的用户名密码输入（此步骤根据自己需要选择）
** git使用https协议，每次pull, push都会提示要输入密码，使用git协议，然后使用ssh密钥，这样免去每次都输密码的麻烦
 
###### 更改https协议为git协议，并使用ssh密钥大概需要三个步骤：
1、生成密钥对
- 查看是否已经有了ssh密钥：cd ~/.ssh
- 如果没有密钥则不会有此文件夹，有则备份删除
2、设置远程仓库（本文以github为例）上的公钥
- ssh-keygen -t rsa -C “youremail”
- 按3个回车，密码为空。
- 最后得到了两个文件：id_rsa和id_rsa.pub
3、把git的 remote url 修改为git协议（以上两个步骤初次设置过以后，以后使用都无需再次设置，当前步骤视项目的remote url而定，如果以后其它项目的协议为https则需要此步骤）
- 查看生成的密钥
```
cat ~/.ssh/id_rsa.pub

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC0X6L1zLL4VHuvGb8aJH3ippTozmReSUzgntvk434aJ/v7kOdJ/MTyBlWXFCR+HAo3FXRitBqxiX1nKhXpHAZsMciLq8vR3c8E7CjZN733f5AL8uEYJA+YZevY5UCvEg+umT7PHghKYaJwaCxV7sjYP7Z6V79OMCEAGDNXC26IBMdMgOluQjp6o6j2KAdtRBdCDS/QIU5THQDxJ9lBXjk1fiq9tITo/aXBvjZeD+gH/Apkh/0GbO8VQLiYYmNfqqAHHeXdltORn8N7C9lOa/UW3KM7QdXo6J0GFlBVQeTE/IGqhMS5PMln3 admin@admin-PC
```
- 登陆你的github帐户。 Settings -> SSH and GPG keys ->  New SSH key
- 验证该key是否正常工作
```
ssh -T git@github.com
```
结果显示如下，表明设置成功了
```
Hi xxx! You've successfully authenticated, but GitHub does not # provide shell access.
```
- 使用命令 git remote set-url 来调整url
``` 
git remote set-url origin git@github.com:someaccount/someproject.git
```


# git分支开发


## 在dev上开发
git checkout dev  # 切换到dev分支进行开发
### 开发代码之后，我们有两个选择
-  第一个：如果功能开发完成了，可以合并主分支
git checkout master  # 切换到主分支
git merge dev  # 把dev分支的更改和master合并
git push  # 提交主分支代码远程
git checkout dev  # 切换到dev远程分支
git push  # 提交dev分支到远程
-  第二个：如果功能没有完成，可以直接推送
git push  # 提交到dev远程分支
* 注意：在分支切换之前最好先commit全部的改变，除非你真的知道自己在做什么11

