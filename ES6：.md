## ES6：

#### 1：变量

##### var 

> 1：可以重复声明
>
> 2：无法限制修改
>
> 3：没有块级作用域

##### let

> 1：不能重复声明
>
> ```js
> let a=12;
> let a=5;
> 
> console.log(a)
> //会报错，重复声明
> ```

> 2：变量---可以修改
>
> 3：有块级作用域（只在自己的函数作用域里面使用）
>
> ```html
> <input type="button" value="按钮1">
> <input type="button" value="按钮2">
> <input type="button" value="按钮3">
> 
> <script>    
>     var btn=document.getElementsByTagName("input")
> 	for(var i=0;i<btn.length;i++){
>     	btn[i].onclick=function(){
>         	console.log(i)//这里i永远是3
>     	}
> 	}
>     //闭包
>     for(var i=0;i<btn.length;i++){
>         (function(i){
>             btn[i].onclick=function(){
>         	console.log(i)//这里利用闭包延展了作用域i是0,1,2
>     	}
>         })(i)
>     }
>     //ES6 let
>     for(let i=0;i<btn.length;i++){
>         btn[i].onclick=function(){
>         	console.log(i)//这里i是0,1,2
>     	}
>     }
>     
> </script>
> ```
>
> 

##### const

> 1：不能重复声明
>
> 2：常量---不可以修改
>
> 3：有块级作用域（只在自己的函数作用域里面使用）



#### 2：函数

##### 箭头函数：只是函数的简写，省掉function 换成=>

()=>{

}

```js
let arr=[12,4,3,45,22,54,34]
arr.sort(function(a,b){
    return a-b
})
arr.sort((a,b)=>{
    return a-b
})
```



> 1：如果只有一个参数，()可以省
>
> ```js
> let add=function(a){
>     return a+2
> }
> let add=a=>{
>     return a+2
> }
> ```
>
> 2：如果只有一个return 可以省掉return和{}
>
> ```js
> let add=function(a){
>     return a+2
> }
> let add=a=>a+2
> 
> let arr=[12,4,3,45,22,54,34]
> arr.sort(function(a,b){
>     return a-b
> })
> arr.sort((a,b)=>a-b)
> 
> ```
>
> 

3：数组

4：字符串

5：面向对象

6：Promise

7：generator

8：模块化

