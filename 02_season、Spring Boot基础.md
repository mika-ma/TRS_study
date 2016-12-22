###一、搭建season开发环境
**1.在IntelliJ IDEA中创建一个Meven工程mwkang**
GroupId为trs.com.cn，artifactId为mwkang，version为1.0-SNAPSHOT

![新建一个Maven工程.png](http://upload-images.jianshu.io/upload_images/208018-d4f0a53f8828a031.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**2. 创建完成，项目预览及配置pom.xml如下**

![配置pom.xml.png](http://upload-images.jianshu.io/upload_images/208018-789929cf3efd9a85.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**3.创建启动类**
在src/main/java下创建一个包com.trs.config，然后新建一个继承自com.season.core.controller的类

![创建启动类.png](http://upload-images.jianshu.io/upload_images/208018-4a09310810983168.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**4. 创建Controller**
新建HelloController，继承com.season.core.Controller，添加@ControllerKey注解。新建类所属的包名必须是com开始，因 Season默认配置的Spring扫描包为com。

![创建Controller.png](http://upload-images.jianshu.io/upload_images/208018-1acd0f067010a51c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**5.重新启动main方法**
本地访问[http://localhost:8080/hello/season](http://localhost:8080/hello/season)，即可看见效果

![启动main方法.png](http://upload-images.jianshu.io/upload_images/208018-5ddb8c2b1be70370.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![启动main方法成功.png](http://upload-images.jianshu.io/upload_images/208018-46c4c9b98b2b14ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![访问本地服务显示效果.png](http://upload-images.jianshu.io/upload_images/208018-3ad5d63601bd0a94.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
