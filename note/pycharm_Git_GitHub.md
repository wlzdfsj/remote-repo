# pycharm_Git_GitHub
#### 1. 使用pycharm工具，关联Git和GitHub
![关联Git和GitHub](vx_images/531844311268661.png =900x)
#### 2. 将本地项目推送到github
VCS->Share Project On Github->填写新的仓库名、远程仓库名(默认origin)-->share
此时在GitHub上面刷新可以看到新上传的仓库
![本地项目推送到github](vx_images/475925311263797.png =900x)

#### 3. 内容修改后提交GitHub
* 在本地项目在新增一个文件，会呈红色显示（修改文件后呈蓝色），然后点击右键-->Git-->add-->添加到暂存区，此时呈绿色
* 再点击右键-->Git-->commit file-->选择文件并提交-->添加到本地仓库，呈黑色
![](vx_images/388510412257343.png =900x)
* 再从本地仓库推送到GitHub,在GitHub刷新可以看到修改后的项目
![](vx_images/360060713250477.png =900x)

![成功推送文件](vx_images/358120913241007.png =900x)
**注意：如果删除文件，一定不要忘记提交到仓库和远程，否则只是本地删除，远程还存在**
#### 从GitHub拉取项目到本地
1. 在GitHub上复制想要下载的项目链接
获取项目的链接操作：
![](vx_images/76705713245343.png =900x)

点击链接成功跳转到项目[Test01](https://github.com/wlzdfsj/Test_pycharm/tree/5dc5a06dbc8406e590d3c4e6de648664edf797a4/Test01)



2. pycharm中点击Git-->Clone-->填写远程仓库的项目URL
![克隆项目](vx_images/561932413243511.png =900x)
3. 再用pycharm打开项目即可
也可以使用Gitbash克隆操作


