# Learn_Ajax
学习Ajax

### 使用Ajax
- 导入Jquery资源
- 前端
```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
  <head>
    <title>$Title$</title>

    <script src="${pageContext.request.contextPath}/static/js/jquery-3.6.0.js"></script>
    <script>

      function fun(){
        $.post({
          url:"${pageContext.request.contextPath}/a",
          data:{"dataName":$("#username").val()},
          success:function (data) {
            alert(data);
          }
        })
      }
    </script>
  </head>
  <body>
    <!-- 失去焦点的时候，发起一个请求到后台 -->
    用户名:<input type="text" id="username" onblur="fun()">
  </body>
</html>

```
- 后端
```java
    @RequestMapping("/a")
    public void a1(String dataName, HttpServletResponse response) throws IOException {
        System.out.println("a1:param => " + dataName);
        if ("kindred".equals(dataName)){
            response.getWriter().print("true");
        }else {
            response.getWriter().print("false");
        }
    }
```
