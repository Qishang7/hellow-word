HelloAction.java:

    /**
     * @Auther: likang
     * @Date: 2018/11/21 16:06
     * @Description: hello请求的处理类
     */
    public class HelloAction {

        /**
        * @Description 请求接收的处理方法
        * @Author  likang
        * @Date   2018/11/21 16:07
        * @Param  []
        * @Return      java.lang.String
        * @Exception
        */
        public String execute(){
            return "success";
        }

    }


struts.xml:

    <!--name:模块名称
            extends:值是struts-default.xml中的package默认的name值
            namespace：命名空间，默认是“/”
        -->
        <package name="demo" extends="struts-default" namespace="/demo">
                   <!--
                       name:请求名称
                       class：接收请求处理类
                       method：请求类中的处理方法
                   -->
            <action name="hello" class="com.xdl.action.HelloAction" method="execute">
                <!--
                    name:方法返回的结果
                    type:返回值类型，默认的其实就是dispatcher
                -->
                <result name="success" type="dispatcher">/WEB-INF/jsp/hello.jsp</result>

            </action>
        </package>

web.xml:

     <!--加载struts2配置文件信息-->
      <filter>
        <filter-name>struts</filter-name>
        <filter-class>org.apache.struts2.dispatcher.filter.StrutsPrepareAndExecuteFilter</filter-class>
      </filter>
      <filter-mapping>
        <filter-name>struts</filter-name>
        <!--所有请求都可以访问到
          struts2默认的请求后缀名为：action和“”
        -->
        <url-pattern>/*</url-pattern>
      </filter-mapping>
