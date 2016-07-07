## Tips
#### 1，类名.this 与 类名.class 的区别。
#### 2，日志系统与日志框架
        http://openwebx.org/docs/Webx3_Guide_Book.html#webx.filter.requestcontexts.pipeline
#### 3，git删除远程分支
        https://git-scm.com/book/zh/v1/Git-%E5%88%86%E6%94%AF-%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF
#### 4，git跟踪远程分支checkout，这个命令也可以说是创建本地分支或者切换分支。
        （1）当前为master分支：git checkout -b master_test  origin/master_dev   在本地创建与远程master_dev相同的分支（not master）
        （2）当前为master分支：git checkout -b master_test  在本地创建与远程master（当前分支）相同的分支，（常见操作）
        （3）当前为master分支：git checkout master_dev  切换当前分支从master到master_dev
#### 5，Linux 会话管理神器：screen  （tmux更先进一点）
         screen -ls             显示所有会话
         screen -S xingyu       后台创建新的会话，会话名为xingyu（会话只用创建一次即可，如果要进入已有会话，直接执行第3步）
         script /dev/null       切换管道
         screen -x xingyu       进入会话xingyu
