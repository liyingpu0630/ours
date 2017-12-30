#获取项目的需求文档

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
* 注意：在分支切换之前最好先commit全部的改变，除非你真的知道自己在做什么
#后台开发相关接口


#前端书写静态页面
