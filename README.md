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

将每个页面级别的Widget的State替换为我们的StateWithLifecycle，导包即可。

然后我们可以选择重写`onCreate`、`onPause`、`onResume`、`onDestroy`方法，在这些方法内部执行对应的业务逻辑即可。

如果需要自定义当前页面的log标识的话，如下所示：给`tagInStateWithLifecycle`字段赋值即可。

```
@override
  void initState() {
    tagInStateWithLifecycle = "WidgetsTestPage";
    super.initState();
  }
```

### 3、注意事项：

①应用突然关闭后，flutter端不会再收到任何消息。

②flutter端的根页面正常关闭时，不会触发State#dispose方法，也就不会触发我们的onDestroy方法，这时如果需要是释放资源，就需要自己处理了


### 4、demo地址

[https://github.com/tinyvampirepudge/flutter_lifecycle_state_test](https://github.com/tinyvampirepudge/flutter_lifecycle_state_test)

