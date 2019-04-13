# flutter_lifecycle_state

Make State support lifecycle method just like Android&#x27;s Activity#onCreate、 Activity#onResume、Activity#onPause、Activity#onDestroy.

参照Android端的Activity中的生命周期，在flutter中的State类中也实现了类似方法。

## Getting Started

使用方式：

### 1、给flutter端的app添加配置。

在MaterialApp中添加navigatorObservers监听器，这里的这个`routeObserver`是定义在我们包中的。

```
return MaterialApp(
  // 应用标题
  title: 'Flutter Demo',
  ...

  // Register the RouteObserver as a navigation observer.
  navigatorObservers: [routeObserver],
);
```

### 2、StateWithLifecycle使用方式：
将每个页面级别的Widget的State替换为我们的StateWithLifecycle，导包即可。然后我们可以选择重写onCreate、onPause、onResume、onDestroy方法，在这些方法内部执行对应的业务逻辑即可。

如果需要自定义当前页面的log标识的话，如下所示：给`state_with_lifecycle_tag`字段赋值即可。

```
@override
  void initState() {
    state_with_lifecycle_tag = "WidgetsTestPage";
    super.initState();
  }
```

