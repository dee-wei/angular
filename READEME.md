# Angular简介和入门

## 什么是库（包），什么是框架？
 - jQuery ：库
  + 封装了一些常用的方法，我们主动的调用这些方法
    -- 提高了代码的利用，以及代码后期的维护

 - Angular: 前端框架   还有例如： react vue
  + 框架提供了一些结构或者模式，
  + 我们是根据框架提供的结构或者模式去书写代码
  + 由框架帮助我们去执行相应的操作。
 
## 什么是 Angular

- 一款非常优秀的前端高级 JS 框架,我们可以利用angular 轻松构建 SPA 应用程序（单页面应用程序）
- 单页面应用程序 模拟cs结构 （客户端/服务器） 作出的bs的结构 （浏览器/服务器） 的网站，但是带有客户端的功能性、页面局部刷新特点
- 其核心就是通过指令扩展了 HTML，通过表达式绑定数据到 HTML。
- *Angular不推崇DOM操作，也就是说在NG中几乎找不到任何的DOM操作*

- ps：
- CS和BS的区别及联系：
- cs 称之为 client/sever(客户端和服务器)模式，这种模式我的个人理解就是在客户端上面安装专用软件。
- 优点：可以发挥客户端PC的处理能力，客户端处理之后再交给服务端，客户端的响应速度快，提高响应速度。
- 缺点：需要安装很多的软件，需要对软件进行维护，维护成本高，而且只适用于局域网。
- bs 称之为 brower/server(浏览器/服务器)模式，这种模式是浏览器通过web server同数据库进行数据交互。一些主要的逻辑在服务端
- 优点：不用安装专门的软件，可以随时随地的使用
- 缺点：对服务器的要求变高了，所以单位一般都有数据库存储服务器（服务器炸了 就GG）


### 安装 Angular

- 暴力安装: 直接从本地硬盘中复制一个angular.js文件到项目中

- 通过工具安装
  + npm 方式 `npm install angular`  npm i angular  当前目录下的node_modules
 
  + bower 方式 'bower install angular'
- bower 
 安装 'npm install -g bower'

## Angular 基础概念

### 指令

- 内置指令   angular自带的
ng- 已ng-开头的标签里面的属性的扩展形式称之为指令
ng-app 告诉angular从这里开管理代码了
ng-controller 定义控制器范围
ng-model 绑定input输入框的值
ng-click 添加点击事件
ng-init 初始化一个对象的值

- 自定义指令  自己制定的指令


### Angular 的核心特性


### Angular 表达式
{{}}表示一个表达式，像模板引擎
 <p>hello:{{user.name}}</p>
 <p>{{"hello:"+user.name}}</p>
 <p>{{1+1}}</p>
 <p>{{[1,2,3,4]}}</p>
- 注意不能写json或对象
<!--<p>{{{"a":"123"}}}</p>-->

### 模块化  angular.module()

### 模块(module)
- angular.module('myApp',[])
  > 第一个参数是模块的名字
  > 第二个参数是一个数组，数组的元素是该模块所依赖其他模块的名字
*注意,即使不依赖任何模块，也需要给第二个参数传递一个空数组*
*否则angular.module('myApp')就是去获取名为myApp的模块对象*

### 控制器(controller) 在controller里面处理数据和具体业务逻辑
- angular.module('myApp',[]).controller('demoController',function($scope){})
> 第一个参数，是控制器的名字
> 第二个参数，是一个回调函数，在回调函数里写我们想要的js代码。

### 首先 MVC是一种设计思想,它是约定了程序的结构应该是怎么，每一个组成原件都会有一个明确的职责。
- 优点：提高代码的结构和可维护性;

### 我的理解要了解MVC 就要先理解$scope 和 $rootscope

- MVC 单项数据绑定
  - M:Model 模型  :数据存储，一些业务逻辑
  - V:View  视图 ：就是用来展示数据
  - C:Controller 控制器: 调度业务逻辑
  - 目的：使用表达式显示数据模型的值。

- MVVM 双向数据绑定
  - M:Model 模型  :数据存储，一些业务逻辑
  - V:View  视图 ：就是用来展示数据
  - vm:ViewModel $scope
  - 减弱了MVC中controller的作用，在M 和 V 之间添加了一层viewModel层，控制器只有在提交或者刷新页面的情况会用到
  - 目的：数据模型的值发生改变，就会导致页面值的改变，页面值的改变，就会导致数据模型值的改变，这各种相互影响的关系就是双向数据绑定。

## 看图理解：
  - (./pic/angular-mvvm.png);

### ViewModel
- $scope 实际上就是MVVM中所谓的VM（视图模型）
- 正是因为$scope在Angular中大量使用甚至盖过了C（控制器）的概念，所以很多人把Angular称之为MVVM框架

### 依赖注入
我需要什么，我就在参数上面去定义，要是调用我的方法就给我传
//angular
var controller =function(callback){
   setTimeout(function(){
    //写了一堆逻辑
      callback($scope);
   },2000)
}
//我们按照angular逻辑去写的代码
controller(function($scope){
   $scope
})
依赖注入的参数是不能修改的

### $watch
- 用于监视数据模型的变化（并且只能监视数据模型的变化）
- $scope.$watch('数据模型名的字符串形式',function(变化后的值,变化前的值){})
- $scope.$watch里的回调函数会默认执行一次。
- 速度快
- 减轻了服务器自身在带宽压力。

### 相关链接

- AngularJS 1.x 官方网站
  + https://angularjs.org/
- AngularJS 2.x 官方网站
  + https://angular.io/
- Google Material Design for Angular
  + https://material.angularjs.org
- Angular UI（Angular最大的第三方社区）
  + http://angular-ui.github.io/
- AngularJS中文社区
  + http://www.angularjs.cn/
- AngularJS中文社区提供的文档（不用翻墙）
  + http://docs.angularjs.cn/api
  + http://www.apjs.net/


### 案例1  写一个输入框一个按钮
<body>
<input type="text" name="" id="num" value="">
<input type="button" name="" id="add" value="值+1">
<script>
      var add=document.getElementById("add");
      add.onclick=function(){
         var num=document.getElementById("num");
         //注意点需要-0，从字符串变成数字
         num.value=(num.value-0)+1;
      }
</script>
</body>

### 案例2
<body ng-app> 
    <input type="text" ng-model="val" name="" value="">
    <input type="button" ng-click="val=(val-0)+1" name="" value="+1">
    <script src="node_modules/angular/angular.js"></script>
</script>
</body>



