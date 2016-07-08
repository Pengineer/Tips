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
#### 6，开发中应该合理的使用enumeration。
~~~java
public enum DataIsShow {
    SHOW(1),NOT_SHOW(0);

    private Integer value;
    private DataIsShow(Integer tmpValue) {
        value = tmpValue;
    }

    public Integer getValue() {
        return value;
    }
}
~~~
#### 7，IDEA长撸快捷键
      ctrl + enter : 导入包
      ctrl + insert : 插入getter/setter 或者构造函数
   
      ctrl + alter + o : 自动优化导入的包
      ctrl + alter + t : 自动生成try-catch
      ctrl + alter + l : 自动格式化代码
      ctrl + alter + left/right : 返回上一次浏览的地方
      ctrl + alter + up/down : 代码块上/下移一个代码块
      shift + alter + up/down : 当前行上/下移一行
      ctrl + shift + f : 全局查找
   
      ctrl + i : 实现接口方法
      ctrl + o : 覆写父类方法
      ctrl + u : (从方法体外)跳转到父类
   
      ctrl + d : 复制一行
      ctrl + x : 剪切一行（可当删除使用ctrl + y）
   
      alter + left/right : 切换视图
     
      调试：
      F7 : 进入
      F8 : 单步
      F9 : 调到下一个断点
