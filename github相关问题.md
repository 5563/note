## 在github中遇到的问题

1. 关联远程仓库

   ` $ git remote add origin https://github.com/5563/note.git`

2. 删除远程仓

   ` git remote rm origin `

### 关联仓库时遇到错误

- git push 出现

![image-20210428161014278](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20210428161014278.png)

​	解决：执行`git config http.sslVerify "false" `

