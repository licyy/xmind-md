ajax 不是新的语言，是综合利用 

作用，与用户交互，在页面不刷新的情况下请求服务器，局部更新页面数据



异步：不需要跳转，局部刷新

异步对象：var xhr= new XMLHttpRequest()  内置对象 



实现异步：创建异步对象 

​											var xhr= new XMLHttpRequest()

​				    发送请求报文  

​											写请求行 xhr.open(请求方式，请求url)

​															get请求拼接参数 

​															post请求不写参数

​											写请求头xhr.setRequestHeader("key":"value")

​															get请求不写请求头

​															post请求：xhr.setRequestHeader("Content-Type","application/x-www-form-urlencoded")

​											写请求体xhr.send()

​															get请求请求体内容为空xhr.send(null)

​															post请求：xhr.send("username="+name)   字符串拼接

​				    接收响应报文

​											通过监听异步对象状态readystate改变判断是否完成响应   onreadystatechange

​															服务器成功响应xhr.status==200

​															数据解析完成xhr.readystate==4

​											通过xhr.responseText接收返回的数据

​															document.querySelector(".showmes").innerText=xhr.responseText





请求报文

请求行 ：请求方式 请求url 协议  

​		xhr.open(请求方式，请求url)

​		get请求如果有参数需要拼接

​		post请求如果有参数在请求体中传递

请求头：客户端发送给服务器的一些额外信息

​		xhr.setRequestHeader("key":"value")

​		get请求不用请求头

​		post请求需要设置Content-Type:application/x-www-form-urlencoded

请求体： 客户端发送给服务器的信息

​		xhr.rend（参数：key=value&key=value）

​		如果有参数，post应该在这个位置来传递

​		get请求参数已经拼接在请求行，所以不用写 xhr.send(null)



响应报文

报文行：相应状态码（status） 相应状态信息  200   ok    

报文头：服务器返回给客户端的一些额外信息

报文体：服务器返回给客户端的信息 

​		responseText:普通字符串

​		responseXML:符合xml格式字符串

JSON.parse()将json文件转换成数组或者对象



jsonp 实现跨域请求：请求别的域名里面的数据，默认就只能get请求；使用jsonp方法服务器端可以设置想分享的数据

实现，跨域都需要第三方的同意

实现原理：利用script标签天然的跨域特性来实现的

实现方式：原生方式

1：客户端向服务器发送请求

1. <script src="corss.php?callback=test">

2：服务器返回给客户端的是一个函数的调用，函数传递的实参就是数据

客户端script只能识别js格式语法，所以在服务端echo时要拼接起来，服务器是将数据反馈到客户端上，实际调用还是在客户端的

```
<?php 				
				//服务端接收callback函数
$callback=$_GET["callback"]
<--  $data 服务器端获取数据  -->
				//向客户端返回函数的调用
echo $callback."(".$data.")"  ?> 
```

3：客户端不能直接识别没有声明的调用，所以在另一个script里面创建对应的函数体



ajax：

data：{

​			向服务器传递的属性

}

dataType："jsonp" 就可以了



success：success（res）