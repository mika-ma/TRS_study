>前端页面用静态HTML编写，嵌入JQuery和Ajax实现动态显示和提交评论。

>以“发表评论”为例，season后台大致数据流动过程理解为：前端通过Ajax将评论comment的数据提交到Controller控制层，在控制层通过注解查找saveComment方法，方法中将评论对象实例化一个评论vo，依次通过工厂类ServiceFactory、服务层CommentService、工厂类DaoFactory到数据层CommentDao，通过save方法实现数据持久化。


**1.IDEA中新建项目，并配置数据库**

![配置mysql.png](http://upload-images.jianshu.io/upload_images/208018-e37b26b5fdf55742.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


![配置mysql.png](http://upload-images.jianshu.io/upload_images/208018-7e37347b1f08d313.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**2.录入数据库信息连接数据库，用建表语句建表**

![录入数据库名等信息.png](http://upload-images.jianshu.io/upload_images/208018-52999396439970b8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![连接数据库建表.png](http://upload-images.jianshu.io/upload_images/208018-c1f56a559001383b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 项目结构

![工程结构.png](http://upload-images.jianshu.io/upload_images/208018-eb08cdff8a802ce1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**3.season后台：创建启动类**
```
package com.main;
import com.season.core.spring.SeasonApplication;
import com.season.core.spring.SeasonRunner;
/** 
* Created by mwkang on 2016/12/19. 
* 启动类 
*/
public class App extends SeasonApplication {    
public static void main(String[] args) {        
SeasonRunner.run(App.class);   
}}
```

**4.创建实体类**
```
package com.vo;

import com.season.core.db.Pojo;

import com.season.core.db.annotation.Column;
import com.season.core.db.annotation.TableInfo;
import com.season.core.db.annotation.Transient;

import java.util.Date;

/**
 * Created by mwkang on 2016/12/19.
 * 实体类
 */
@TableInfo(tableName = Comment.tableName,pkName = "comment_id")
public class Comment extends Pojo<Comment>{
    public static final String tableName = "comment";

    @Column(name = "comment_id")
    private int commentId;

    @Column(name = "product_name")
    private String productName;

    @Column(name = "comment_content")
    private String commentContent;

    @Column(name = "create_date")
    private String createDate;


    @Transient
    private String remark;

    public Comment(){}

    public String getRemark() {
        return remark;
    }

    public void setRemark(String remark) {
        this.remark = remark;
    }



    public int getCommentId() {
        return commentId;
    }

    public void setCommentId(int commentId) {
        this.commentId = commentId;
    }

    public String getProductName() {
        return productName;
    }

    public void setProductName(String productName) {
        this.productName = productName;
    }

    public String getCommentContent() {
        return commentContent;
    }

    public void setCommentContent(String commentContent) {
        this.commentContent = commentContent;
    }

    public String getCreateDate() {
        return createDate;
    }

    public void setCreateDate(String createDate) {
        this.createDate = createDate;
    }

    public Comment(int commentId, String productName, String commentContent, String createDate) {
        this.commentId = commentId;
        this.productName = productName;
        this.commentContent = commentContent;
        this.createDate = createDate;
    }

}

```

**5.创建数据层**
```
package com.dao;

import com.vo.Comment;
import com.season.core.db.Dao;
import org.springframework.stereotype.Repository;
import java.util.List;

/**
 * Created by DELL on 2016/12/19.
 * 数据层
 */
@Repository
public class CommentDao {
    //查询全部评论
    public List<Comment> findAll(){
        return Dao.findAll(Comment.class);
    }

    //增加评论数据
    public void save(Comment vo){
        Dao.save(vo);
    }

    //删除评论数据
    public void delete(int commentId){
        Dao.deleteById(Comment.class,commentId);
    }

    //修改评论数据
    public void update(Comment vo){
        Dao.update(vo);
    }

}
```

**6.服务层**
```
package com.service;

import com.factory.DaoFactory;

import com.vo.Comment;
import java.util.List;

/**
 * Created by mwkang on 2016/12/19.
 * 服务层
 */
public class CommentService {
    public List<Comment> findAll(){
        return DaoFactory.getCommentDAOInstance().findAll();
    }

    public void insert(Comment vo){
        DaoFactory.getCommentDAOInstance().save(vo);
    }

    public void delete(int commentId){
        DaoFactory.getCommentDAOInstance().delete(commentId);
    }

    public void update(Comment vo){
        DaoFactory.getCommentDAOInstance().update(vo);
    }


}

```


**7.创建控制层**
```
package com.controller;


import com.factory.ServiceFactory;
import com.vo.Comment;
import com.season.core.ActionKey;
import com.season.core.Controller;
import com.season.core.ControllerKey;

import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.List;

/**
 * Created by mwkang on 2016/12/19.
 * 控制层
 */
@ControllerKey("product")
public class CommentController extends Controller {

    //查询显示所有评论
    @ActionKey("findAllComments")
    public void findAllComments(){
        List<Comment> all = ServiceFactory.getCommentServiceInstance().findAll();
        renderJson("comments",all);
    }

    //新增
    @ActionKey("saveComment")
    public void saveComment(){
        String content = getPara("comment");
        Comment vo = new Comment();
        vo.setCommentContent(content);
        vo.setProductName("computer");
        vo.setCreateDate(new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(new Date().getTime()));
                //new java.sql.Date(System.currentTimeMillis()));
        ServiceFactory.getCommentServiceInstance().insert(vo);
        renderJson();
    }

    //删除
    @ActionKey("delete")
    public void delete(){
        int id=getParaToInt("id");
        ServiceFactory.getCommentServiceInstance().delete(id);
    }

    //修改
    @ActionKey("update")
    public void update(){
        String changecontent = getPara("comment");
        Comment vo = new Comment();
        vo.setCommentId(getParaToInt("id"));
        vo.setCommentContent(changecontent);
        vo.setProductName("computer");
        vo.setCreateDate(new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(new Date().getTime()));
        ServiceFactory.getCommentServiceInstance().update(vo);
        renderJson();
    }


}
```

**8.工厂类**
- DaoFactory

```
package com.factory;
import com.dao.CommentDao;
/** 
* Created by mwkang on 2016/12/19. 
* 工厂类 
*/
public class DaoFactory {    
public static CommentDao getCommentDAOInstance(){        
return new CommentDao();    
}}
```

- ServiceFactory

```
package com.factory;
import com.service.CommentService;
/** 
* Created by DELL on 2016/12/19. 
* 工厂类 
*/public class ServiceFactory {    
public static CommentService getCommentServiceInstance(){       
 return new CommentService();    
}}
```


 
**9.前端页面**
```
<!doctype html>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
<html>
<head>
    <title>商品详情</title>
    <script type="text/javascript" src="jquery-1.8.3.js"></script>
    <script type="text/javascript">

        function cc(id) {
            //删除评论
            $.ajax({
                type: "post",
                dataType: "json",
                url: "http://localhost:8080/season/product/delete?id=" + id,
                data: id,
                success: function (data) {
                    location.href = "http://localhost:8080/season/index.html"
                }

            });
        }

        function dd(id, comment) {
            //修改评论
            $("#comment").val(comment);
            $("#div1").append("<button id='b_c' >确认修改</button>");
            $("#a_c").css('display:none');
            
            $("#b_c").click(function () {
            var changeComment = $("#comment").val();

                $.ajax({
                    type: "get",
                    dataType: "json",
                    url:"http://localhost:8080/season/product/update?id="+id,
                    data: {
                        comment: changeComment
                    },
                    success: function (data) {
                        location.href = "http://localhost:8080/season/index.html"
                    }

                })
            })

        }




        $(document).ready(function() {

        $(function bb () {
                //查询显示所有评论
                $.ajax({
                    type: "get",
                    dataType: "json",
                    url: "http://localhost:8080/season/product/findAllComments",
                    data: null,
                    success: function (data) {
                        $("#commentDiv").empty();
                        var commentsText = "";
                        $.each(data.comments, function (commentIndex, comment) {
                            commentsText += "<li>" +
                                    "<div style='background-color: #d9fff7'>" + "游客" + comment.commentId + "说：</div>" +
                                    "<div style='background-color: #fff3f3'><b>" +  comment.commentContent + "</b></div>" +
                                    "<div style='background-color: #fff3f3'>" + "评论时间：" +comment.createDate+

//                                new Date(comment.createDate).getFullYear()+"."+
//                                new Date(comment.createDate).getUTCMonth()+"."+
//                                new Date(comment.createDate).getDate()+"&nbsp&nbsp&nbsp&nbsp"+
//                                new Date(comment.createDate).getHours()+" : "+
//                                new Date(comment.createDate).getMinutes() +

                                    "&nbsp&nbsp"+"<button id='"+comment.commentId+"' onclick='cc("+comment.commentId+")'>"+"删除"+"</button>"+
                                    "&nbsp&nbsp"+"<button id='"+comment.commentId+"' onclick='dd("+comment.commentId+","+comment.commentContent+")'>"+"修改"+"</button>"+
                                    "</div>"+"</li>";
                        });
                        $("#commentDiv").append(commentsText);
                    }
                });
            });

            //发表提交评论
            $("#a_c").click(function aa () {

                var enterComment = $("#comment").val();
                $.ajax({
                    type: "post",
                    dataType: "json",
                    url: "http://localhost:8080/season/product/saveComment",
                    data: {
                        comment: enterComment
                    },
                    success: function (data) {
                    location.href="http://localhost:8080/season/index.html"
                    }
                });

            });

        });
    </script>
</head>
<body>




<p align=center>
    <font style="font-size:12pt">
        <span> 冰箱 </span>
    </font>
    <br><br>

    <FONT style="font-size:9pt" color=darkgray>
        来源：<TRS_DOCUMENT FIELD="DOCSOURCE" AUTOLINK="TRUE">来源 </TRS_DOCUMENT>
        时间：<TRS_DATETIME>时间</TRS_DATETIME>
    </FONT>
    <br><br>


    <img align="center" style="width: 25%; height: 50%" src='./bx.png' border=0/>
    <br><br>

    <font style="font-size:15pt">
        <span> 642升变频风冷对开门冰箱；优雅香槟金，时尚百搭；变频压缩机，节能静音；手机操控，智能饮食养生，低温净味系统 </span>
    </font>
    <br><br>

</p>
<br><br>
 
<div id="div1"> 
请发表您的评论：<br>
<textarea type="text" id="comment" cols="80" rows="2"></textarea>
<input type="button" id="a_c" value="发表"/>
</div>

<div id="commentDiv"></div>

</body>
</html>
```

**10.http://localhost:8080/season/index.html 运行结果显示如下：**
- 首页

![首页.png](http://upload-images.jianshu.io/upload_images/208018-3730989a89f3a16b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 录入评论内容并点击发表按钮

![录入评论内容.png](http://upload-images.jianshu.io/upload_images/208018-ecf054c8ce1bc40a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 发表同时刷新页面显示结果

![显示结果.png](http://upload-images.jianshu.io/upload_images/208018-9c2f72f509874a48.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 删除操作
点击删除

![点击删除.png](http://upload-images.jianshu.io/upload_images/208018-d7984eff37bd5ea2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

删除成功
![删除成功.png](http://upload-images.jianshu.io/upload_images/208018-c9e2d78fa1706d8c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 修改操作
点击修改按钮，评论内容同步到录入框中，后边出现一个“确认修改”按钮
![点击修改.png](http://upload-images.jianshu.io/upload_images/208018-0947cedec34927a5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击确认修改，修改成功同时刷新当前页面

![12修改完成.png](http://upload-images.jianshu.io/upload_images/208018-63d85e4eb812ebaa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




