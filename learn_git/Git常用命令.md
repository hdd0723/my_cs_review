## Git常用命令

#### 1 版本变化

##### 版本回退

将本地仓库的内容回退到之前的某个版本，注意这里回退的**本地仓库**的内容，远程仓库的内容并不会受影响。

方法一：HEAD+'^'

```bash
git reset --hard HEAD^ 		# 回退到前一个版本，HEAD是当前版本
git reset --hard HEAD^^ 	# 回退到前2个版本
git reset --hard HEAD~10 	# 回退到前10个版本
```

方法二：通过commit id指定回退版本

```bash
git log --pretty=oneline	# 显示所有提交的commit id
git reset --hard 1094aa		# 回退至版本commit id为1094aa的版本(某个历史版本)
```

##### 版本前进

与版本回退的作用刚好相反，将本地仓库的内容往前

方法一：通过commit id指定回退版本

```bash
git log --pretty=oneline	# 显示所有提交的commit id
git reset --hard 1094aa		# 前进至版本commit id为1094aa的版本(最近提交的某个版本)
```

方法二：通过reflog查看某个版本的commit id

```bash
git reflog					# 用来记录每次的操作的记录
git reset --hard 07822e3	# 前进至commit id为0722e3的版本处
```

#### 2 撤销修改

有时候对工作区做了一定的修改之后，需要对修改进行撤销，根据当版本当前的状态，分为以下几种情况

**撤销工作区修改**

修改了工作区的内容之后，并未添加到暂存区或者提交，通过下面两句命令可以实现撤销工作区的修改

```bash
# 方法一
git restore file_name.txt
# 方法二
git checkout -- file_name.txt
```

注意方法二中的“--”不能忽略，否则就无法实现工作区的撤销。



**撤销暂存区的修改**

假设file.txt修改了，并添加到了暂存区

```bash
# 方法一：通过两步撤销暂存区的修改
git reset HEAD file.txt # 将file.txt在暂存区的修改撤销，修改目前停留在工作区
git restore file.txt	# 将工作区的file.txt的修改撤销
```



