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
#### 7，IDEA常撸快捷键
      alter + enter : 导入包
      alter + insert : 插入getter/setter 或者构造函数
   
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
####8，chrome插件：JSONview

####9，基于IDEA的热部署</br>
　　在DEBUG项目的时候，如果不能进行热部署，那将是很痛苦的一件事，IDEA2016是支持服务器热部署选项的：RUN/DEBUG Configuration -> Server -> On frame deactivation，选择Update classes and resource。也就是说在IDEA失去焦点的时候，会重新加载被改变的class文件。</br>
　　如果是非DUBUG的普通开发模式，建议就不要打开该选项了，不然每次切换窗口，IDEA就会检查有没有class文件被修改。（打开也没问题~）
####10，远程代码调试（http://blog.csdn.net/cyl937/article/details/44134955）
####11，网站开发工具curl（http://www.ruanyifeng.com/blog/2011/09/curl.html）
        curl www.aliyun.com  获取网页源码
        curl www.aliyun.com -o filename 获取网页源码，同时保存到指定文件（等同于wget）
        curl www.aliyun.com -i  获取网页源码，同时加上响应头
        curl www.aliyun.com -v  显示一次http通信的整个过程，包括端口连接、http request头信息、响应头和响应正文等信息。
        curl --form upload=@localfilename --form press=OK [URL]  文件上传
	        假定文件上传的HTML为<form method="POST" enctype='multipart/form-data' action="upload.cgi"><input type=file name=upload><input type=submit name=press value="OK"></form>
####12，Tomcat对Session的管理
　　（1）浏览器第一次请求访问应用中任意一个支持会话的网页时，Servlet容器会试图寻找HTTP请求中表示Session ID的Cookie，由于还不存在这样的Cookie，因此Servlet认为一个新的会话开始了，于是创建一个HttpSession对象，为它分配唯一的Session ID，然后把Session ID作为Cookie添加到HTTP响应结果中。当浏览器接受到HTTP响应结果后，会把其中表示Session ID的Cookie保存在客户端。</br>
　　（2）当浏览器再次访问该应用时，本次HTTP请求中就会包含有表示Session ID的Cookie。Servlet容器从HTTP请求中获取到该Cookie，认为本次请求已经处于会话中了，就不会再创建新的HttpSession对象，而是从Cookie中获取Session ID，然后根据Session ID找到内存中对应的HttpSession对象。</br>
　　（3）浏览器重复步骤二，直到当前会话被销毁，HttpSession对象就会结束生命周期。</br>
　　在默认情况下，JSP网页都是支持会话的，如果一个Web组件支持会话（比如JSP），就意味着：</br>
　　a.当客户端访问该Web组件时，Servlet容器会自动查找HTTP请求中表示Session ID的Cookie，以及向HTTP响应结果中添加表示Session ID的Cookie。Servlet容器还会创建新的HttpSession对象或则寻找已经存在的与Session ID对应的HttpSession对象。</br>
　　b.Web组件可以访问代表当前会话的HttpSession对象。
~~~Java
如下JSP代码：
<%
Cookie[] cookies = request.getCookies();
if(cookies == null) {
	out.print("no cookie");
	return;
}
for(int i=0; i < cookies.length; i++) {
%>
	<p>
	<b>Cookie name:</b>
	<%= cookies[i].getName() %>
	<b>Cookie value:</b>
	<%= cookies[i].getValue() %>
	</p>
	<p>
	<b>max age in seconds:</b>
	<%= cookies[i].getMaxAge() %>
	</p>
<%
}
%>
~~~
####13，Linux工具命令之Dig：Dig主要是用来做域名解析（http://www.ruanyifeng.com/blog/2016/06/dns.html）
####14，HttpClient4.x自带维持会话功能，只要使用同一个HttpClient且未关闭连接，则可以使用相同会话来访问其他要求登录验证的服务。HttpClient对session的保持有两种方式：
　　a.使用一个全局的HttpClient对象，因为HttpClient自带维持会话功能。</br>
　　b.获取登录请求返回的Cookie信息，后面的所有请求都带着Cookie信息。
####15，为了保证变量名的规范使用，对不会重新赋值的变量尽量加上final。　　
####16，利用EXCEL拼接SQL语句（CONCATENATE函数），例如：
　　=CONCATENATE("update question_category set solution_url='", L3, "' and tool_url='", N3,"' where category_name='",A3, "' and product_code='", B3, "';")
####17，关于MySQL中的replace into
　　a.当存在pk冲突的时候是先delete再insert。</br>
　　b.当存在uk冲突的时候是直接update</br>
　　结论：如果业务逻辑强依赖自增ID，绝对不要用replace，普通环境也不建议这样用，因为会导致主键的重新组织。
####18，MySQL的字符类型中，char和varchar指定的大小是字符，其它字符类型指定的都是字节；MySQL的text等类型加索引时，需要指定索引的长度，也就是以text所属字段的前X个字符进行索引。
