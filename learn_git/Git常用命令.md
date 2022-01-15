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

有时候需要撤销对版本做出的改动，



