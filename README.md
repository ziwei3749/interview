# interview

## HTML/CSS

- 1.什么是语义化的HTML,语义化的HTML有什么用?

可以分,对用户、开发者、搜索引擎优化来回答

- 2.行内元素和块级元素的区别,分别举例3个

```
img / input / a
div / h1 / p / header / main / footer / ul / tr / td 
```

- 3.浮动的表现,以及常见的闭合浮动的方式,简单说说他们能清除浮动的原理

- 4.盒模型由什么哪些组成? 

margin padding border

- 5.解释什么是外边距合并现象 (或者看代码回答,给brother2元素添加margin-top:60px后会发生什么)


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .brother1 {
            width: 100px;
            height: 100px;
            background: blue;
            margin-bottom: 40px;
        }

        .brother2 {
            width: 100px;
            height: 100px;
            background: red;
        }
    </style>
</head>
<body>
    <div class="brother1"></div>
    <div class="brother2"></div>
</body>
</html>

```

- 6.解释什么是外边距的塌陷现象 (或者看代码回答,给child元素添加margin-top:60px后会发生什么)

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .father {
            width: 200px;
            height: 200px;
            background: blue;
        }

        .child {
            width: 100px;
            height: 100px;
            background: red;
        }
    </style>
</head>
<body>
    <div class="father">
        <div class="child"></div>
    </div>
</body>
</html>

```

- 7.position常见的几种定位方式,以及区别

 position: static 
 position:absolute : 脱离文档流,相对于父元素定位
 position:relative : 不脱离文档流, 相对于自己本身的位置定位
 position:fixed  : 脱离文档流, 相对于body定位
 
- 8.如何让文本垂直居中,如何高度不确定呢? 
 
- 9.实现图中的布局,容器高度不确定的情况下,如何让中间content自适应
 
 <img src="./css.png">
 
 ## JS
 
 - 1.'=='和'==='的区别
 
 - 2.什么是JS的预解析,解释下面代码的运行结果
 
 ```
     var value = 'hello';
     function show() {
       alert(value);
       if (!value) {
         var value = 'function';
       }
       alert(value);
     }
     show() 
 
 ```
 
 函数声明提升优于变量声明提升:
 ```
    var a;
     function a() {} 
     alert(typeof a);
 
 ```
 
 - 3.this & arguments。this和arguments分别是什么? 说出下列代码的运行结果,并试着解释为什么
 
 ```
   function f(){
       console.log(this)
       console.log(arguments)
   }
   f.call() // window
   f.call({name:'frank'}) // {name: 'frank'}, []
   f.call({name:'frank'},1) // {name: 'frank'}, [1]
   f.call({name:'frank'},1,2) // {name: 'frank'}, [1,2]
 
 ```
 
 - 4.如何改变this的指向?
 
 通过call / apply / bind
 
 call 、 apply返回的是对原函数的调用结果。参数的话,第一个是this,后面是原函数的参数
 bind 返回是是一个函数。函数体和原来的函数一样, bind的参进去的参数就是这个函数里的this
 
 
 - 5.你知道哪些把伪数组变成数组的方法?
 
 ES5: Array.prototype.slice.call('arguments')
 ES6: Array.from('arguments')
        
- 6.单线程的js是如何通过eventloop机制,说出代码的执行顺序

```
    console.log(1)
    
    setTimeout(function(){
        console.log(2)
    },0)

    console.log(3)
    

```

```
 setTimeout(function(){
     console.log('定时器开始啦')
 });
 
 new Promise(function(resolve){
     console.log('马上执行for循环啦');
     for(var i = 0; i < 10000; i++){
         i == 99 && resolve();
     }
 }).then(function(){
     console.log('执行then函数啦')
 });
 
 console.log('代码执行结束');
    

```
 
- 7.下面程序的输出结果是怎样的,为什么?
 
 ```
    let liList = document.querySelectorAll('li')
        for(var i=0; i<liList.length; i++){
         liList[i].onclick = function(){
             console.log(i)
         }
    }
 
 ````
 
- 8.如何阻止事件冒泡和默认事件
 
    stopPropagation
    return false

- 9.前后端开发过程中,出现错误时,一般你如何检查这个错误是否属于前端。
 