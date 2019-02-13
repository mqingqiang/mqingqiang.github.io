---
title: Hexo + Github Pages 搭建个人博客
date: 2019-02-01 17:31:12
type: "tags"
tags: 
  - 教程
  - 博客
categories: 
  - 安装配置
comments: 
---

> &emsp;&emsp;一年又过去了，2019 年已经过了 2 个月了，想起自己从毕业至今已工作了差不多 2 年的时间，期间做了一个又一个项目，技术也学了不少，但是现在回想起来，很多记忆已经很模糊，看过的，学过的，做过的，都已不大记得清楚了，更别谈刻在脑海中。掌握一个技术性知识点的过程无非这三步：一是学习，可在博客、书籍、视频中学习；二是实践，学了没用上的知识是很快就会在脑海中消失的；三是分享，一些牛人都说过，不能说得让别人听懂的，证明自己还没理解透彻，想来是有一定道理的。基于以上三点，想来要在 2019 年掌握一些知识，是需要开始写一些博客做下分享了。写博客的目的，一来可以做一些学习中的必须，二来可以阶段性对某一个技术进行总结，三来我的分享要是有幸让别人受益，也算是做了一点贡献了。
>
> &emsp;&emsp;要写博客，首先要有一个博客，博客也无非 2 种，一种是注册现成的博客，如 CSDN、博客园、简书、SegmentFault、掘金、知乎等；一种是自己搭建博客，如 Hexo、WordPress 等。本文题目是 `Hexo + Github Pages 搭建个人博客` ，那么我的选择就肯定是 Hexo 了。至于这些博客的优劣，这里不会阐述。
>
> &emsp;&emsp;既然我的博客搭建起来了，想起搭建博客过程中的各种折腾各种坑，第一篇博客当然就是分享下个人博客的搭建过程啦！

### 一、准备工具

​        由于 Hexo 需要使用 nodejs 编译，git 上传，所以需要安装这 2 个工具。这里安装过程略过，只给出下载地址。

#### 1、安装 Node.js

- 下载地址：https://nodejs.org/zh-cn/
- 测试是否成功：命令行使用 `node -v` 和 `npm -v` ，查看显示版本号即成功。

#### 2、安装 Git

- 下载地址：https://git-scm.com/download
- 建议安装一个 Git 客户端，如：TortoiseGit

### 二、安装 Hexo

- 执行命令：`npm install hexo-cli -g`
  ![](https://raw.githubusercontent.com/mqingqiang/pic/master/img/1548905279220.png?token=AdKuDjIttbvtIkIFJL6UQdd4CTNehGQ5ks5cVBKSwA%3D%3D)
- 创建存放博客的目录（如我的为 F:\Hexo\myblog）
- 初始化 Hexo 网站（比较漫长的等待）：`hexo init`
- 生成静态页面：`hexo g`
- 启动服务器：`hexo s`
- 访问博客：`http://localhost:4000/`

### 二、部署到 Github

&emsp;&emsp;完成上面的步骤之后，就可以在本地写写博客来玩了。但是我们既然写了博客，肯定是想要放到网上让别人看到的，要不然直接写到笔记软件里多好，不用折腾这么多。这里我选择使用 Github Pages 来部署我的博客。

### 四、测试代码高亮

- java代码

  ```java
  package com.tydic.o2o.common.constant;
  
  /** 
   * @ClassName: OrderStateEnum 
   * @Description: 订单状态枚举
   * @author tdd
   * @date 2016年8月19日 上午9:39:30 
   *  
  */
  public enum OrderStateEnum {
  	待实名("0", "待实名"),
  	待受理("1","待受理"),
  	已受理("2","已受理"),
  	已竣工("3","已竣工"),
  	待转录("4","待转录"),
  	已撤单("5","已撤单"),
  	受理失败("6","受理失败"),
  	办理中("7","办理中"),
  	支付成功("8","支付成功"),
  	待退费("9","待退费"),
  	退费成功("10","退费成功"),
  	已关闭("11","已关闭"),
  	实名不通过("12","实名不通过"),
  	已办理("13","已办理"),
  	下单成功("14","下单成功"),
  	待人工实名审核("15","待人工实名审核"),
  	待跟进("16","待跟进"),
  	待上传预约照片("17","待上传预约照片"),
  	照片审核不通过("18","照片审核不通过"),
  	预约照片待审核("19","预约照片待审核"),
  	无需核单("20","无需核单"),
  	照片审核通过("21","照片审核通过");
  	
  	private String code;
  	private String name;
  
  	private OrderStateEnum(String code,String name) {
  		this.code = code;
  		this.name=name;
  	}
  	private OrderStateEnum(String code){
  		this.code=code;
  	}
  
  	public static String getOrderStateEnum(String code){
  		for(OrderStateEnum e:OrderStateEnum.values()){
  			if(e.code.equals(code)){
  				return e.getName();
  			}
  		}
  		return null;
  	}
  
  	public String getCode() {
  		return code;
  	}
  
  	public void setCode(String code) {
  		this.code = code;
  	}
  
  	public String getName() {
  		return name;
  	}
  
  	public void setName(String name) {
  		this.name = name;
  	}
  	
  }
  ```

- properties文件

  ```properties
  #Created by elvis 
  #Tue Nov 09 11:33:32 CST 2010
  log4j.addivity.org.apache=true
  log4j.appender.A1=org.apache.log4j.DailyRollingFileAppender
  log4j.appender.A1.DatePattern='.'yyyy-MM-dd
  log4j.appender.A1.Encoding=UTF-8
  log4j.appender.A1.File=/opt/log/website.log
  log4j.appender.A1.Threshold=debug
  log4j.appender.A1.layout=org.apache.log4j.PatternLayout
  log4j.appender.A1.layout.ConversionPattern=%d{ABSOLUTE} %5p %c{1}\:%L \: %m%n
  log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender
  log4j.appender.CONSOLE.Encoding=UTF-8
  log4j.appender.CONSOLE.Target=System.out
  log4j.appender.CONSOLE.Threshold=debug
  log4j.appender.CONSOLE.layout=org.apache.log4j.PatternLayout
  log4j.appender.CONSOLE.layout.ConversionPattern=[o2o-intf] %d - %c -%-4r [%t] %-5p %c %x - %m%n
  log4j.logger.com.opensymphony.xwork2=error
  log4j.logger.org.springframework = error
  log4j.logger.com.ibatis=info
  log4j.logger.com.ibatis.common.jdbc.ScriptRunner=info
  log4j.logger.com.ibatis.common.jdbc.SimpleDataSource=info
  log4j.logger.com.ibatis.sqlmap.engine.impl.SqlMapClientDelegate=info
  log4j.logger.java.sql.Connection=info
  log4j.logger.java.sql.PreparedStatement=info
  log4j.logger.java.sql.Statement=info
  log4j.rootLogger=debug,CONSOLE
  
  # Configure logging for testing: optionally with log file
  log4j.rootLogger=WARN, stdout
  # log4j.rootLogger=WARN, stdout, logfile
  log4j.appender.stdout=org.apache.log4j.ConsoleAppender
  log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
  log4j.appender.stdout.layout.ConversionPattern=%d %p [%c] - %m%n
  log4j.appender.logfile=org.apache.log4j.FileAppender
  log4j.appender.logfile.File=target/spring.log
  log4j.appender.logfile.layout=org.apache.log4j.PatternLayout
  log4j.appender.logfile.layout.ConversionPattern=%d %p [%c] - %m%n
  ```

- xml文件

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <beans xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  	xmlns="http://www.springframework.org/schema/beans" xmlns:mvc="http://www.springframework.org/schema/mvc"
  	xmlns:context="http://www.springframework.org/schema/context"
  	xmlns:aop="http://www.springframework.org/schema/aop" xmlns:util="http://www.springframework.org/schema/util"
  	xmlns:p="http://www.springframework.org/schema/p"
  	xsi:schemaLocation="
  	http://www.springframework.org/schema/beans
  	http://www.springframework.org/schema/beans/spring-beans-3.2.xsd
  	http://www.springframework.org/schema/mvc
  	http://www.springframework.org/schema/mvc/spring-mvc-3.2.xsd
  	http://www.springframework.org/schema/context
  	http://www.springframework.org/schema/context/spring-context-3.2.xsd
  	http://www.springframework.org/schema/util
  	http://www.springframework.org/schema/util/spring-util-3.2.xsd">
  
  	<!-- 控制某一个单独的视图请求到某一个页面 -->
  	<mvc:view-controller path="/" view-name="redirect:/index.jsp" />
  	<!-- 扫描指定包下面,带有指定注解的类 -->
  	<context:component-scan base-package="com.tydic.o2o.intf.action" use-default-filters="false">
  		<context:include-filter type="annotation"
  			expression="org.springframework.stereotype.Controller" />
  		<context:include-filter type="annotation"
  			expression="org.springframework.web.bind.annotation.ControllerAdvice" />
  	</context:component-scan>
  
  	<!-- 静态资源映射 -->
  	<mvc:resources mapping="/viewWeui/**" location="/viewWeui/" cache-period="0" />
  	<mvc:resources mapping="/view/**" location="/view/" cache-period="0" />
  
  	
  	<!-- 默认的注解映射的支持，org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping -->
  	<mvc:annotation-driven
  		content-negotiation-manager="contentNegotiationManager">
  		<mvc:message-converters register-defaults="true">
  			<!-- 将StringHttpMessageConverter的默认编码设为UTF-8 -->
  			<bean class="org.springframework.http.converter.StringHttpMessageConverter">
  				<constructor-arg value="UTF-8" />
  			</bean>
  			<!-- 将Jackson2HttpMessageConverter的默认格式化输出为false -->
  			<bean
  				class="org.springframework.http.converter.json.MappingJackson2HttpMessageConverter">
  				<property name="supportedMediaTypes">
  					<list>
  						<value>application/json;charset=UTF-8</value>
  					</list>
  				</property>
  				<property name="prettyPrint" value="false" />
  			</bean>
  		</mvc:message-converters>
  	</mvc:annotation-driven>
  
  	<!-- REST中根据URL后缀自动判定Content-Type及相应的View -->
  	<bean id="contentNegotiationManager"
  		class="org.springframework.web.accept.ContentNegotiationManagerFactoryBean">
  		<property name="mediaTypes">
  			<map>
  				<entry key="xml" value="application/xml" />
  				<entry key="json" value="application/json" />
  			</map>
  		</property>
  		<property name="ignoreAcceptHeader" value="true" />
  		<property name="favorPathExtension" value="true" />
  	</bean>
  	<!-- 定义视图文件解析 -->
  	<bean
  		class="org.springframework.web.servlet.view.InternalResourceViewResolver">
  		<property name="prefix" value="/viewWeui/" />
  		<property name="suffix" value=".jsp" />
  	</bean>
  
  
  	<mvc:interceptors>
  		<mvc:interceptor>
  			<mvc:mapping path="/**" />
  			<mvc:exclude-mapping path="/outMain/service" />
  			<mvc:exclude-mapping path="/valid/sign.do" />
  			<mvc:exclude-mapping path="/valid/token.do" />
  			<mvc:exclude-mapping path="/main/service" />
  			<mvc:exclude-mapping path="/main/jingdongService" />
  			<mvc:exclude-mapping path="/jingdongWhiteOrder/**" />
  			<mvc:exclude-mapping path="/login/**" />
  			<mvc:exclude-mapping path="/**/libs/**" />
  			<mvc:exclude-mapping path="/**/login.html" />
  			<mvc:exclude-mapping path="/**/pc/login_web.html" />
  			<mvc:exclude-mapping path="/**/pc/**" />
  			<mvc:exclude-mapping path="/**/pc/customerInfo.html" />
  			<mvc:exclude-mapping path="/**/pc/uploadText.html" />
  			<mvc:exclude-mapping path="/**/pc/orderInfo.html" />
  			<mvc:exclude-mapping path="/**/loginManual.html" />
  			<mvc:exclude-mapping path="/**/card/handle_iccid.html" />
  			<mvc:exclude-mapping path="/**/card/iccid_order.html" />
  			<mvc:exclude-mapping path="/**/card/upload_idcard.html" />
  			<mvc:exclude-mapping path="/**/card/to_order.html" />
  			<mvc:exclude-mapping path="/**/forget_password.html" />
  			
  			<!-- 移动业务加载 -->
  			<mvc:exclude-mapping path="/**/mobileProdsList.html"/>
  			<mvc:exclude-mapping path="/**/mobile_prod_handle.html" />
  			<mvc:exclude-mapping path="/**/mobile_prod_vali.html" />
  			<mvc:exclude-mapping path="/**/mobile_prod_handle_external.html" />
  			<mvc:exclude-mapping path="/**/mobile_pay_QR_code.html" />
  			<mvc:exclude-mapping path="/**/mobile_pay_result.html" />
  			<mvc:exclude-mapping path="/**/mobile_prod_detail.html" />
  			<mvc:exclude-mapping path="/**/mobile_handle_result.html" />
  			<mvc:exclude-mapping path="/**/mobile_order_success.html" />
  			<mvc:exclude-mapping path="/**/mobileProd/**" />
  			<mvc:exclude-mapping path="/**/activityOrder/**" />
  			<mvc:exclude-mapping path="/**/activity/index.html" />
  			<mvc:exclude-mapping path="/**/activity/activity_index.html" />
  			<mvc:exclude-mapping path="/**/activity/activity_redpackage.html" />
  			<mvc:exclude-mapping path="/**/activity/activityProdsList.html" />
  			<mvc:exclude-mapping path="/**/activity/activity_prod_detail.html" />
  			<mvc:exclude-mapping path="/**/activity/jd_activity_index.html" />
  			<mvc:exclude-mapping path="/**/activity/middle_activity.html" />
  			<mvc:exclude-mapping path="/**/activity/transform_platform.html" />
  			<!-- 二维码销售品下单 -->
  			<mvc:exclude-mapping path="/**/product/product_detail.html" />
  			<mvc:exclude-mapping path="/**/product/product_detail_fuse.html" />
  			<mvc:exclude-mapping path="/**/product/product_detail_fuse_add.html" />
  			<mvc:exclude-mapping path="/**/product/product_QR_code.html" />
  			<mvc:exclude-mapping path="/**/product/product_list_fuse_add.html" />
  			<mvc:exclude-mapping path="/**/product/product_list_fuse.html" />
  			<mvc:exclude-mapping path="/**/product/product_list_llb.html" />
  			<mvc:exclude-mapping path="/**/product/product_list_mobile.html" />
  			<mvc:exclude-mapping path="/**/product/product_list_tv.html" />
  			<mvc:exclude-mapping path="/**/product/product_list_unlimitflow.html" />
  			<mvc:exclude-mapping path="/**/product/product_list.html" />
  			<mvc:exclude-mapping path="/**/order/product_order.html" />
  			<mvc:exclude-mapping path="/**/order/product_order_fuse.html" />
  			<mvc:exclude-mapping path="/**/order/product_order_new.html" />
  			<mvc:exclude-mapping path="/**/order/order_success.html" />
  			<!-- <mvc:exclude-mapping path="/**/order/order_list.html" /> -->
  			<mvc:exclude-mapping path="/**/order/real_name_qr_code.html" />
  			<mvc:exclude-mapping path="/**/order/real_name_qr_code_mobile.html" />
  			<mvc:exclude-mapping path="/**/order/product_order*" />
  			<mvc:exclude-mapping path="/**/order/orderQuery.html" />
  			<mvc:exclude-mapping path="/**/order/queryResult.html" />
  			<mvc:exclude-mapping path="/**/order/uploadImgTip.html" />
  			
  			<!-- 预约商机  -->
  			<mvc:exclude-mapping path="/**/niche/niche.html" />
  			<mvc:exclude-mapping path="/**/niche/niche_loading.html" />
  			<mvc:exclude-mapping path="/**/nicheOrder/busiOrderSubmit" />
  			<mvc:exclude-mapping path="/**/nicheOrderTransform/nicheOrderObj" />
  			
  			<mvc:exclude-mapping path="/**/register.html" />
  			<mvc:exclude-mapping path="/**/register_new.html" />
  			<mvc:exclude-mapping path="/**/agreement.html" />
  			
  			<mvc:exclude-mapping path="/**/common/**" />
  			<mvc:exclude-mapping path="/**/css/**" />
  			<mvc:exclude-mapping path="/**/js/**" />
  			<mvc:exclude-mapping path="/**/bower_components/**" />
  			<mvc:exclude-mapping path="/**/img/**" />
  			
  			<!-- 限购查询 -->
  			<mvc:exclude-mapping path="/**/product/queryProdLimitedNum" />
  			<mvc:exclude-mapping path="/**/product/checkProdLimitedNum" />
  			
  			<!-- 2016-09-21 -->
  			<!-- 分享 -->
  			<mvc:exclude-mapping path="/**/share/**" />
  			
  			<!-- 2016-10-19 -->
  			<!-- 开放接口 -->
  			<mvc:exclude-mapping path="/**/open/**" />
  			<!-- 实人认证 -->
  			<mvc:exclude-mapping path="/**/realName/**" />
  			
  			<!-- 机场大巴单B办理 -->
  			<mvc:exclude-mapping path="/**/skyBus/**" />
  			
  			<!-- 本地系统整合进跨界系统 -->
  			<mvc:exclude-mapping path="/**/localCrossover/**" />
  			
  			<mvc:exclude-mapping path="/**/product/queryProdTypeAndList" />
  			<mvc:exclude-mapping path="/**/product/queryRecommendList" />
  			
  			<mvc:exclude-mapping path="/**/weixin/phoneOrder" />
  			<mvc:exclude-mapping path="/**/share/product/createSubmitToken" />
  			
  			<!-- 用户查询订单列表 -->
  			<mvc:exclude-mapping path="/**/order/searchOrder.html" />
  			<mvc:exclude-mapping path="/**/order/searchResult.html" />
  			<mvc:exclude-mapping path="/**/order/searchOrderList" />
  			
  			<!-- 合伙人分享商店 -->
  			<mvc:exclude-mapping path="/**/shopshare/assets/**" />
  			<mvc:exclude-mapping path="/**/webUser/getQrCode" />
  			<mvc:exclude-mapping path="/**/shopshare/share_shop.html" />
  			<mvc:exclude-mapping path="/**/shopshare/shareShop.html" />
  			<mvc:exclude-mapping path="/**/shopshare/shop.html" />
  			
  			<!-- 517活动 -->
  			<mvc:exclude-mapping path="/**/V1/share189go.html" />
  			
  			<!-- 合伙人分享商店开发列表页等后续操作 -->
  				<!-- 融合业务 -->
  			<mvc:exclude-mapping path="/**/product/product_list_fuse.html" />
  			<mvc:exclude-mapping path="/**/product/queryProductList" />
  			<mvc:exclude-mapping path="/**/order/queryOrderDetail" />
  			<mvc:exclude-mapping path="/**/order/queryBankInfos" />
  			<mvc:exclude-mapping path="/**/order/queryOrderList" />
  			<mvc:exclude-mapping path="/**/activityOrder/queryActivityDetailByUserId" />
  			<mvc:exclude-mapping path="/**/webUser/queryWebUserCityById" />
  			
  			<mvc:exclude-mapping path="/**/product/product_list_tv.html" />
  			<mvc:exclude-mapping path="/**/mobileprods/mobile_QR_code.html" />
  			<mvc:exclude-mapping path="/**/product/product_list_mobile.html" />
  			<mvc:exclude-mapping path="/**/product/product_list.html" />
  			<mvc:exclude-mapping path="/**/product/product_list_llb.html" />
  			<mvc:exclude-mapping path="/**/product/product_detail_llb.html" />
  			<mvc:exclude-mapping path="/**/product/llb_QR_code.html" />
  			<mvc:exclude-mapping path="/**/product/product_detail.html" />
  			<mvc:exclude-mapping path="/**/order/order_detail.html" />
  			<mvc:exclude-mapping path="/**/order/protocol.html" />
  			<mvc:exclude-mapping path="/**/order/protocol2.html" />
  			<mvc:exclude-mapping path="/**/order/protocol3.html" />
  			<!-- 异常页面配置 -->
  			<mvc:exclude-mapping path="/**/error/**" />
  			<!-- 省级合伙人自主注册 -->
  			<mvc:exclude-mapping path="/**/webuser/registerProvincial.html" />
  			
  			<bean id="loginInterceptor" class="com.tydic.o2o.intf.action.common.LoginInterceptor" />
  		</mvc:interceptor>
  	</mvc:interceptors>
  
  </beans>
  ```

  