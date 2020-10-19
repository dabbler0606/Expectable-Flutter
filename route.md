---
description: 路由是页面彼此相互跳转的根基
---

# 路由

## 路由

Flutter 中，我们可以创建多个页面部件。如下创建了两个命令路由。`/screen1` 和 `/screen2`。

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'hello',
      home: Screen1(),
      routes: <String, WidgetBuilder> {
        '/screen1': (_) => Screen1(),
        '/screen2': (_) => Screen2(),
      },
    );
  }
}
```

{% hint style="info" %}
 注意命名路由要以斜线 / 开头。
{% endhint %}

点击 Screen1 的按钮跳转到 Screen2

```dart
class Screen1 extends StatefulWidget {
  @override
  _Screen1State createState() => _Screen1State();
}

class _Screen1State extends State<Screen1> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          child: FlatButton(
            child: Text('跳转 screen2'),
            onPressed: () => Navigator.pushNamed(context, '/screen1'),
          )
        ),
      ),
    );
  }
}
```

Screen2:

```dart
class Screen2 extends StatefulWidget {
  @override
  _Screen2State createState() => _Screen2State();
}

class _Screen2State extends State<Screen2> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Container(
          child: FlatButton(
            child: Text('返回 Screen1'),
            onPressed: () => Navigator.pop(context),
          )
        ),
      ),
    );
  }
}
```



