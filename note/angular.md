- run() 在config()之后执行, 在controller()之前执行, 是angular所有应用第一个执行的应用
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

- $cacheFactory 缓存 402

- $http 自定义缓存 403

- constant() 在config()之前执行

- decorator() 可在原有的服务上添加属性和方法

- $route.updateParams({name:"beast"}) 更新路由参数

- $route.reload() 重新加载路由

- 默认的请求头保存在$httpProvider.defaults.headers.common对象中

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

```txt
验证用户登录 116
```

```txt
value()方法和constant()方法之间最主要的区别是，常量可以注入到配置函数中，而值不行。
通常情况下，可以通过value()来注册服务对象或函数，用constant()来配置数据。
```

```txt
novalidate: 屏蔽浏览器对表单的默认行为
ng-required="true": 验证必填
ng-minlength="3": 验证最小长度
ng-maxlength="8": 验证最大长度
ng-pattern="/^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/": 验证邮箱正则

获取表单属性格式： formName.inputFieldName.property
formName.inputFieldName.$pristine: 未修改为true, 未修改为false
formName.inputFieldName.$dirty: 只要用户修改过表单, 无论输入是否通过验证, 该值都返回true
formName.inputFieldName.$valid: 表单内容合法返回true
formName.inputFieldName.$invalid: 表单内容不合法返回true
formName.inputfieldName.$error.pattern: 验证正则的合法性, 验证不通过返回true, 验证通过返回false

样式类
.ng-pristine{}
.ng-dirty {}
.ng-valid {}
.ng-invalid {}
```

```js
$scope.$on("test", function(evt) {
  $scope.a++;
});
$scope.$emit("test", newVal);
```

```txt
Least Recenlty Used，最近最少使用(lru)
```

```txt
任何时候如果我们想要为请求添加全局功能，例如身份验证、错误处理等，在请求发送给服
务器之前或者从服务器返回时对其进行拦截，是比较好的实现手段
interceptors 拦截器
四种拦截器: request, responses, requestError, responseError

全局处理错误
统一进行身份验证一类的处理
对所有发出去的请求进行预处理
对所有收到的响应进行预处理
做一些增强用户体验的操作，例如显示一个进度条

request： 接收一个参数，它是 $http 中的标准 config 对象，同时也需要返回一个标准 config ，此时可以添加各类身份验证信息，同时也可在此启动进度条
requestError： 当有多个 Interceptor 的时候， requestError 会在前一个 Interceptor 抛出错误或者执行 $q.reject() 时执行，接收的参数就对应的错误
response:接受一个请求对象参数，可以不处理就直接返回，此时也可以将进度条显示为成功完成，当然，如果后端 API 返回自定义错误时，HTTP 的状态码仍然是 200 得话，便在这里处理自定义错误，也可以对返回数据做一些处理，注意要将进度条置为完成
responseError: 这个是重头戏，即可以处理标准的 Http 错误，如服务器没有响应时，或者 PHP 之类的 CGI 经常出现的 502 一类，还可以处理 HTTP 状态码不是 200 的各类自定义错误
```

```txt
interceptors 拦截器案例
http://www.tuicool.com/articles/eMZBN3

进度条
NProgress
NgProgress (NProgress for AngularJS)
rc-progress
progress-full-width
progress-svg

提示框：
toastr
ngToast (toast for AngularJS)
angular-toast
k-toast
notie
ng-notie
corner-notie
```

```txt
默认情况下，末尾斜杠（可以引起后端服务器不期望出现的行为）将从计算后的URL中剥离
这个可以通过$resourceProvider配置：
app.config(["$resourceProvider",function($resourceProvider){
	$resourceProvider.defaults.stripTrailingSlashes = false;
}])

$resource(url,[paramDefaults],[actions],options);
url: 一个参数化的url模板
paramDefaults: url参数的默认值
actions:用户对于resource行为的默认设置进行扩展的自定义配置的散列，该配置将会以$http.config的格式创建
	action : 字符串，action的名称，这个名称将成为resource对象方法的名称
	method ：字符串，http方法（不区分大小写，如GET, POST, PUT, DELETE, JSONP等）
	params ：对象，这次行动预先设定的参数。如果任何参数的值是一个函数，当一个参数值每一次需要获得请求时都会被执行（除非该参数被忽略的）
	url ：字符串，行为指定的网址。
	isArray ：boolean，如果为true，那么这个行为返回的对象是个数组。
	transformRequest ：函数/函数的数组。转换函数或者一个包含转换函数的数组。转换函数获取http请求体和请求头，并且返回他们的转换版（通常是序列化）
	transformResponse ：函数/函数的数组。转换函数或者一个包含转换函数的数组。转换函数获取http响应体和响应头，并且返回他们的转换版（通常是序列化）
	cache ：boolean，如果为true，一个默认的$http缓存将被作为请求的缓存，否则如果存在一个用$cacheFactory创建的缓存实例，则将用于缓存
	timeout ：数值，毫秒，超时则让请求中止
	withCredentials ：boolean，是否设置withcredentials flag的XHR对象, 查看更多信息的凭据
	responseType ：字符串，响应头类型
	interceptor ：对象，拦截对象有两个可选方法-response和responseError
options: 扩展$resourceProvider行为的自定义设置，唯一支持的选项是stripTrailingSlashes,boolean类型，如果为真，url尾部的斜杠会被移除（默认为true）
```