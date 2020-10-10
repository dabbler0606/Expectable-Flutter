# 状态管理

## Provider

状态可能在多个组件中传递，此时我们需要集中式的来管理状态。

Flutter 官方推荐了一种最为简单的状态管理。Provider

依赖中添加

```dart
dependencies:
  provider: ^4.0.0
```

首先我们需要声明一个数据 Model，里面包含所共享的数据。

```java
class CountModel extends ChangeNotifier {
    final int _count = 0;
}
```

在所有共享此数据的 Widgets 顶层添加 Provider。表明此组件树可提供该 Model 数据。

```java
void main() => {
    ChangeNotifierProvider(
        create: (context) => CountModel(),
        child: MyApp(),
    );
}
```

这样，CountModel 供 MyApp 下的所有 Widget 共享。

使用时，我们需要包裹 Consumer 以表明该组件需要使用此共享 Model。

```java
class _CounterState extends State<Counter> {
    @override
    Widget build(BuildContext context) {
        return Consumer<CountModel> (
            builder: (context, counter, child) {
                return Text("hello world");
            }
        );
    }
}
```

