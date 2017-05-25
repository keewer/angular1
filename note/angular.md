- run() 在config()之后执行, 在controller()之前执行
- $interval.cancel(timer)

- dig google.com  观察DNS服务器的响应内容

- angularjs 是完全使用JavaScript编写的客户端技术，一种构建动态Web应用的结构化框架

- AngularJS主要用于构建单页面Web应用

- $scope对象的生命周期处理有四个不同阶段
>- 创建 链接 更新 销毁

- 销毁作用域 $scope.$destory()

- ng-controller和ng-repeat指令会创建自己的子作用域并将它们附加到DOM元素上

- 控制器在AngularJS中的作用是增强视图

- 将控制器命名为[Name]Controller而不是[Name]Ctrl是一个最佳实践，比如: GoogleController

- 设计良好的应用会将复杂的逻辑放到指令和服务中

- 创建元素 angular.element('<p>')

- 获取元素 angular.element(document.querySelector('#testId'))

- 获取元素 angular.element(document.getElementById('test')

- 获取元素 angular.element(document).find('div')

- 获取元素 $document.find('div')
>- $document 等价于 angular.element(document)
>- $document需要注入

- 获取元素 angular.element($document[0].getElementById('test')
>- $document[0] 等价于 原生js的document

- ng-messages 权威教程 60page
- novalidate 不要使用 html5 验证表单
- ng-messages="signup_form.name.$error" ng-messages-multiple   同时含有多个错误提示信息
- ng-messages="signup_form.name.$error" ng-messages-include="templates/errors.html" 提示信息模板
>- ng-message="required"
>- ng-message="minlength"
>- ng-message="maxlength"

- ng-repeat
>- $index：遍历的进度（0...length-1）
>- $first：当元素是遍历的第一个时值为true
>- $middle：当元素处于第一个和最后元素之间时值为true
>- $last：当元素是遍历的最后一个时值为true
>- $even：当$index值是偶数时值为true
>- $odd：当$index值是奇数时值为true

- <circle ng-attr-cx="{{ cx }}"></circle>

- require会将控制器注入到其值所指定的指令中，并作为当前指令的链接函数的第四个参数

- $location 服务 123

- 路由模式 125
>- $locationProvider.html5Mode(false)
>- $locationProvider.hashPrefix('!')

- decorator() 拦截器 143

- $http 快捷方法 146
>- $http.jsonp("/api/users.json?callback=JSON_CALLBACK")
>- $cacheFactory 缓存设置 151

- $resource 156
>- var user = $resource('/web/huo/:id', {id: '@id'});
>- user.get({id: 123}, function (successFun) {}, function (errorFun) {})
>- user.save({id: 12}, {"username": "keewer"}, function (successFun) {}, function (errorFun) {})
>- get, query, save, delete, remove
>- $save(), $remove(), $delete() 这三个方法是在成功响应函数可以调用
>>- User.get({id: 123}, function (user) {
	user.name = "keewer";
	user.$save()
}, function (errorFun) {})

- promise是一种用异步方式处理值（或者非值）的方法

- angular-touch
- $swipe
- angular-gestures
- Hammer.js 触屏事件 373

-$cacheFactory 缓存 402

- $http 自定义缓存 403

```txt
$interval(fn,delay,[count],[invokeApply],[Pass]);
fn:一个将被反复执行的函数
delay：每次调用的间隔毫秒数值
count：循环次数的数值，如果没设置，则无限制循环
invokeApply：如果设置为false，则避开脏值检查，否则将调用$apply
Pass：函数的附加参数
```

```html
指令调用方式
<my-directive></my-directive>
<div my-directive></div>
<div class="my-directive"></div>
<!--directive:my-directive-->

含有表达式的自定义指令
<my-directive="someExpression">
</my-directive>
<div my-directive="someExpression">
</div>
<div class="my-directive:someExpression">
</div>
<!-- directive: my-directive someExpression -->
```

```txt
?: 如果在当前指令中没有找到所需要的控制器，会将null作为传给link函数的第四个参数
^: 如果添加了^前缀，指令会在上游的指令链中查找require参数所指定的控制器
?^: 将前面两个选项的行为组合起来，我们可选择地加载需要的指令并在父指令链中进行查找
没有前缀
如果没有前缀，指令将会在自身所提供的控制器中进行查找，如果没有找到任何控制器（或
具有指定名字的指令）就抛出一个错误
```

```txt
compile和link选项是互斥的
如果同时设置了这两个选项，那么会把compile所返回的函数当作链接函数，而link选项本身则会被忽略
```