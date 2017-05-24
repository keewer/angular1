>- run() 在config()之后执行, 在controller()之前执行
>- $interval.cancel(timer)

```txt
$interval(fn,delay,[count],[invokeApply],[Pass]);
fn:一个将被反复执行的函数
delay：每次调用的间隔毫秒数值
count：循环次数的数值，如果没设置，则无限制循环
invokeApply：如果设置为false，则避开脏值检查，否则将调用$apply
Pass：函数的附加参数
```