# GitHub
#### 克隆远程仓库，使用ssh协议
![GitHub账号](vx_images/324590409258983.png =900x)


1. 配置ssh

![配置ssh秘钥](vx_images/586101009246850.png =900x)


![复制公钥](vx_images/251252016250476.png)
公钥上传：

![公钥上传GitHub](vx_images/588021309267016.png =900x)



配置成功：
![](vx_images/11611509259685.png =900x)

**注意：如果是第一次配置ssh，并没有修改默认文件名，此时配置成功
如果不是第一次配置，而是新建的一个保存秘钥的文件，则需要多加一步;**
需要创建一个config文件，执行tail -5 config得到五行内容，将这五行内容添加到文件里面
克隆远程仓库到本地：
![克隆远程仓库](vx_images/426601509256240.png =700x)

此时对这个仓库进行修改数据，并不会影响远程仓库，因为没有提交远程仓库中
#### 本地仓库和远程仓库是俩个独立仓库，不会相互影响，想要同步俩个仓库，需要用到俩个命令：
* git push &emsp;//把本地仓库的修改推送到远程仓库
* git pull &emsp;//把远程仓库的修改拉取到本地仓库
![本地仓库的信息修改推送到远程仓库](vx_images/227551609251994.png =700x)


此时可以在远程仓库看到新的数据：
![](vx_images/588051609269874.png =900x)


#### 关联本地仓库和远程仓库
* git remote add origin git@github.com:wlzdfsj/remote-repo.git
表示关联本地my-repo这个仓库和远程remote-repo仓库
* git remote -v 
查看当前仓库对应的远程仓库别名和地址，origin为别名
![关联本地仓库和远程仓库](vx_images/9983820255119.png)
* git push origin master &emsp;//master为本地分支
把本地仓库的master分支推送给远程仓库的master分支,关联本地和远程的分支
![关联分支](vx_images/75600121244417.png)

![成功推送分支](vx_images/157071909264980.png =900x)



* git pull origin master:master
将远程仓库的master分支拉取到本地master分支，进行合并（远程仓库已修改数据）
![拉取分支信息](vx_images/183331621240807.png)
合并以后，在本地仓库就可以看见新增的文件，拉取成功！！
![合并后的内容](vx_images/525901821252897.png)