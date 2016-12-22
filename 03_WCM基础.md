###一、了解WCM

>WCM（Web Content Management，网站内容管理）是针对大型门户网站的搭建和运行管理而发展起来的一类应用软件平台， 是随着互联网应用普及而发展起来的一项综合技术。WCM系统涉及内容管理、多媒体（富媒体）管理、内容采集、内容加工、网站运行管理、 网站交互功能管理以及网站安全管理等多方面的内容。

>简单来说就是为构建网站，网站内容的构建和更新管理的软件平台。


**1.基本概念**

***视图***
>建立在元数据之上、由元数据生成的属性的集合，类似数据库中视图的概念。 

***元数据***
>描述一个对象的属性的集合，类似数据库中表的概念。

***栏目***
>站点的下一级管理单元，用来组织和管理文档。栏目的存在必须依附于站点，没有站点便不能建立栏目。 

***模板***
>带有TRS置标的HTML文件，用来控制发布页面的显示。系统中的站点、栏目、文档都可以分别配备不同类型模板。 

***库***
>相同类型站点的集合，分为文字库、图片库、视频库和资源库。

***站点***
>WCM 系统里最主要的对象，负责组织和管理栏目。一个站点相当于一个 Internet 网站，你可以按照网站的结构来设计站点及栏目。 

***文档***
>WCM 系统的基本单元，也是系统的核心数据内容。系统中的每一篇文档都必须建立在某 个栏目下，由具备特定权限的用户来操作和管理。 

***发布***
>将系统中的数据结合模板置标生成 HTML 页面的过程。设置了完整发布属性的站点、栏目 及文档都可以执行发布操作。 

***预览***
>在对象发布之前，通过预览功能可以提前查看站点、栏目和文档发布后的效果

###二、创建WCM站点
下面以TRS WCM为例，尝试创建一个站点

**1.安装配置TRS WCM本地环境，安装成功后启动TRS WCM**

![安装配置TRSWCM并启动.png](http://upload-images.jianshu.io/upload_images/208018-4d2e14794036c4f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**2.登陆进入平台**


![登陆wcm.png](http://upload-images.jianshu.io/upload_images/208018-b0e2c56ed0d7e85a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**3.新建站点**
站点实际上就是我们访问网络的一个页面，我们可以在这个页面进行各种不同的操作。站点信息设置如图所示，站点HTTP就是就是访问我们建立网站的地址。


![创建新站点.png](http://upload-images.jianshu.io/upload_images/208018-3d227665a4dd894a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**4.创建栏目**
栏目是一个网站上的分支，它依附于站点而存在，如购物网站里的各种商品的分类。


![新建栏目.png](http://upload-images.jianshu.io/upload_images/208018-6e87378a412d4870.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**5.创建文档**
文档相当于新闻网站中的一条新闻消息，包括标题和内容等。在栏目product下创建文档，保存并发布。


![创建文档.png](http://upload-images.jianshu.io/upload_images/208018-b2508b512acbd21b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**6.创建模板**
使用各类TRS置标添加“栏目列表”选项创建栏目列表模板，并添加头部

![创建栏目列表模板.png](http://upload-images.jianshu.io/upload_images/208018-5ab871999e3526c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

使用TRS置标添加“文档列表”选项创建栏目列表模板


![创建文档列表模板.png](http://upload-images.jianshu.io/upload_images/208018-258c4106904149a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



使用TRS置标添加“文档信息”选项创建栏目列表模板


![创建文档信息模板.png](http://upload-images.jianshu.io/upload_images/208018-46dcd833491f7ee2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)





**7.设置关联站点模板**
将模板加入站点的首页模板中


![设置站点首页模板.png](http://upload-images.jianshu.io/upload_images/208018-b47b885e61511d8b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



设置栏目概览模板和细览模板

![设置栏目模板.png](http://upload-images.jianshu.io/upload_images/208018-01a742080b9f0916.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**8.新增几项栏目和文档并预览站点**

栏目预览：


![栏目.png](http://upload-images.jianshu.io/upload_images/208018-fba692dc1964f8e2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


文档预览：


![文档.png](http://upload-images.jianshu.io/upload_images/208018-c6726d4eb7f48f62.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


模板预览：


![模板.png](http://upload-images.jianshu.io/upload_images/208018-8f65afd87c291103.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


增量发布站点后，预览首页如下：
![预览站点首页.png](http://upload-images.jianshu.io/upload_images/208018-d7623aef27769cbd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

product栏目下两个文档：
![product栏目下两个文档.png](http://upload-images.jianshu.io/upload_images/208018-d5f9b8ebe603e0ac.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

第二篇文档信息（此处只显示文档标题内容，不显示文档正文内容，发现错误后学习《TRSWCM7.0发布置标手册》发现 要根据不同置标内容显示文档不同信息，详见第三部分具体项目和手册）：
![第二篇文档信息.png](http://upload-images.jianshu.io/upload_images/208018-a2a3c285826d5877.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

###三、创建一个简单商品详情页
**1.新建站点product作为商城首页，站点下创建2个栏目分别为“冰箱”和“电视”作为简单商城商品分类，首页设置首页概览模板**


![栏目预览.png](http://upload-images.jianshu.io/upload_images/208018-55d9536909bbe4a1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


**2.冰箱分类下有两个商品“冰箱一”和“冰箱二”，“冰箱一”编辑简单商品详情如下**


![文档预览.png](http://upload-images.jianshu.io/upload_images/208018-2b343937671ecb54.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



![文档细览.png](http://upload-images.jianshu.io/upload_images/208018-70df73937f06fa9d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



**3.创建三个模板“首页概览”“栏目概览”“栏目细览”分别作为命名对应的页面模板，模板代码如下**


![模板预览.png](http://upload-images.jianshu.io/upload_images/208018-d35e3e93b92bc986.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


- 首页概览代码内容：

```
<HTML xmlns="http://www.w3.org/1999/xhtml">
<HEAD>
	<META http-equiv="Content-Type" content="text/html; charset=utf-8" />
	<TITLE>产品列表</TITLE>
</HEAD>
<BODY>
<p align=center> 
<FONT style="font-size:20pt;line-height:150%">   
<span>欢迎光临商城</span></br>
</FONT>
<FONT style="font-size:13pt;line-height:150%">   
<span>请选购您喜欢商品：</span>
</FONT>
<br><br>
<table border="1" cellspacing="0" cellpadding="0"> 
<TRS_CHANNELS id="OWNER"  childtype="-1" startpos="0" >
	<tr> 
		<td>
			<TRS_RECORD>
				<TRS_CHANNEL FIELD="CHNLDESC"> 栏目 </TRS_CHANNEL>
			</TRS_RECORD>
		</td>
	</tr>
</TRS_CHANNELS>
</table>
</p>

</BODY>
</HTML>
```

- 栏目概览代码如下：

```
<HTML xmlns="http://www.w3.org/1999/xhtml">
<HEAD>
	<META http-equiv="Content-Type" content="text/html; charset=utf-8" />
	<TITLE>产品列表</TITLE>
</HEAD>
<BODY>
<p align=center> 
<table cellspacing="0" cellpadding="0" border="0">
<TRS_DOCUMENTS id="OWNER"  channeltype="0"  num="50" startpos="0" automore="FALSE" moretarget="_blank" moretext="更多..."      enablelimit="FALSE">
	<tr>
		<td width="100%" align="left">
			<TRS_DOCUMENT FIELD="DOCTITLE"></TRS_DOCUMENT>
		</td>
	</tr>
</TRS_DOCUMENTS>
</table>
</p>


</BODY>
</HTML>
```

- 栏目细览代码如下：

```
<HTML xmlns="http://www.w3.org/1999/xhtml">
<HEAD>
	<META http-equiv="Content-Type" content="text/html; charset=utf-8" />
	<TITLE>商品详情</TITLE>
</HEAD>
<BODY>
<FONT style="font-size:10.8pt;line-height:150%">   
<TRS_CURPAGE Value=" -> "> 当前位置 </TRS_CURPAGE>     

<p align=center>   
<font style="font-size:12pt">
<b> <TRS_DOCUMENT FIELD="DOCTITLE" > 标题 </TRS_DOCUMENT> </b>
</font>    
<br><br> 

<FONT style="font-size:9pt" color=darkgray>
来源：<TRS_DOCUMENT FIELD="DOCSOURCE" AUTOLINK="TRUE">来源 </TRS_DOCUMENT>   
时间：<TRS_DATETIME>时间</TRS_DATETIME>     
</font>     
</p>  
  
<TRS_DOCUMENT FIELD="DOCHTMLCON" > 正文 </TRS_DOCUMENT> 


</BODY>
</HTML>
```

**4.增量发布站点，预览如下**
- 商城首页：

![首页预览.png](http://upload-images.jianshu.io/upload_images/208018-9ea936dd971462dd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 商品列表


![商品预览.png](http://upload-images.jianshu.io/upload_images/208018-a704531130f64aa0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- “冰箱一”商品详情


![商品详情.png](http://upload-images.jianshu.io/upload_images/208018-87805f8aea6c912f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
