Flutter

最近刚入坑Flutter+Dart ,在这里记录一下笔记。

目前机器环境：Windows10+Flutter+Dart+VS Code+AndroidSDK+夜神模拟器

咒语：一切皆组件,一切皆组件,一切皆组件!!!

没有Mac 没有Android设备 555....

## 最简单的入门

#### 空模板（Hello World示例)

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Wecolme to flutter',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Welcome to Flutter'),
        ),
        body: Center(
          child: Text('Hello World!!!'),
        ),
      ),
    );
  }
}
```

运行：可直接F5 debug run (此时可以 ctrl+s 使用热更新！)

或者在终端使用futter run ，后者可以使用R可以Restart项目, 使用O切换Andrioid/ios预览，使用P调用网格线。

#### Text Widget（简单使用）

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Text widget',
      home: Scaffold(
        body: Center(
          child: Text(
            'Hello widget! hello world! hello yantai! hello mieyi! hello xiaoqi! hello  qiqi! ',
            textAlign:TextAlign.center,
            maxLines: 1,
            overflow: TextOverflow.ellipsis,
            // 超出部分显示
            style: TextStyle(
              fontSize:25.0,
              color:Color.fromARGB(255, 255, 125, 125),
              //字体颜色
              decoration: TextDecoration.underline,
              decorationStyle: TextDecorationStyle.solid
              // 下划线为实线
            ),
            ),
        ),
      ),
    );
  }
}
```

#### Container Widget(简单使用)

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Text widget',
        home: Scaffold(
          body: Center(
            child: Container(
              child: Text('hello world', style: TextStyle(fontSize: 40.0)),
              alignment: Alignment.topLeft,
              width: 500.0,
              height: 400.0,
              // color: Colors.lightBlue,
              padding: EdgeInsets.fromLTRB(10.0, 30.0, 20.0, 20.0), //内边距
              margin: EdgeInsets.all(50.0), //外边距
              decoration: BoxDecoration(
                //渐变色！
                gradient: LinearGradient(colors: [
                  Colors.lightBlue,
                  Colors.greenAccent,
                  Colors.purple
                ]),
                border: Border.all(width: 5.0, color: Colors.pink[100]),
              ),
            ),
          ),
        ));
  }
}
```



#### Image组件（简单图片展示）

单图片及其常用属性

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Text widget',
      home: Scaffold(
        body: Center(
          child: Container(
              child: Image.network(
                'http://jingyile.cn/9.115.png',
                repeat: ImageRepeat.repeat, //重复
                // color: Colors.greenAccent,
                // colorBlendMode: BlendMode.modulate, //混合模式
                // fit:BoxFit.contain  //充满(比较常用)  
                //contain保持原比例   //fill以容器为基础  //cover裁剪图片了 
              ),
              width: 500.0,
              height: 500.0,
              color: Colors.black),
        ),
      ),
    );
  }
}
```

#### ListView组件（简介）

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Demo',
        home: Scaffold(
            appBar: AppBar(title: Text('ListView Widget')),
            body: ListView(children: <Widget>[
              ListTile(
                //tile 瓦片，用瓦片盖上完整房子
                leading: Icon(Icons.pregnant_woman),  //自带图标挺多
                title: Text('1'),
              ),
              ListTile(
                leading: Icon(Icons.perm_camera_mic),
                title: Text('2'),
              ),
              ListTile(
                leading: Icon(Icons.ac_unit),
                title: Text('3'),
              )
            ])));
  }
}
```

多图片的展示

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Text widget',
      home: Scaffold(
        appBar: new AppBar(title:new Text('listView Widget')),
        body:new ListView(
         children:<Widget>[
             //实例化对象可加new 也可以不加
           new Image.network('http://www.jingyile.cn/wp-content/themes/Saber/images/ts/8.jpg'),
           new Image.network('http://www.jingyile.cn/wp-content/themes/Saber/images/ts/7.jpg'),
           new Image.network('http://www.jingyile.cn/wp-content/themes/Saber/images/ts/6.jpg'),
           new Image.network('http://www.jingyile.cn/wp-content/themes/Saber/images/ts/4.jpg'),
         ],
        ),
        ),
    );
  }
}
```

#### ListView横向列表的使用

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Demo',
        home: Scaffold(
            appBar: AppBar(title: Text('ListView Widget')),
            body: Center(
              child: Container(
                height: 400.0,
                child: MyList(),
              ),
            )));
  }
}

//万物皆组件，可以单独写成class
class MyList extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return ListView(
      scrollDirection: Axis.horizontal, //横向
      // scrollDirection: Axis.vertical,  //竖向
      children: <Widget>[
        Container(
          height: 40.0,
          width: 40.0,
          color: Colors.lightBlue,
        ),
        Container(
          width: 40.0,
          height: 40.0,
          color: Colors.amber,
        ),
        Container(
          width: 40.0,
          height: 40.0,
          color: Colors.deepOrange,
        ),
        Container(
          width: 40.0,
          height: 40.0,
          color: Colors.deepOrangeAccent,
        ),
        Container(
          width: 40.0,
          height: 40.0,
          color: Colors.deepPurpleAccent,
        ),
        Container(
          width: 40.0,
          height: 40.0,
          color: Colors.green,
        ),
      ],
    );
  }
}

```

#### ListView动态列表的使用

```dart
import 'package:flutter/material.dart';

void main() =>
    runApp(MyApp(items: List<String>.generate(1000, (i) => "Item $i")));

class MyApp extends StatelessWidget {
  final List<String> items;
  MyApp({Key key, @required this.items}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Demo',
      home: Scaffold(
        appBar: AppBar(title: Text('ListView Widget')),
        body: ListView.builder(
            itemCount: items.length,
            itemBuilder: (context, index) {
              return ListTile(title: Text('${items[index]}'));
            }),
      ),
    );
  }
}
```

#### GridView网格列表的使用

参考文章：https://www.cnblogs.com/sundaysme/p/12560708.html

`gridDelegate`的类型是`SliverGridDelegate`，`SliverGridDelegate`其实是一个抽象类，而且一共有两个实现类：

- `SliverGridDelegateWithFixedCrossAxisCount`：用于固定列数的场景；
- `SliverGridDelegateWithMaxCrossAxisExtent`：用于子元素有最大宽度限制的场景；

关于几个参数的意义

- `crossAxisCount`：列数，即一行有几个子元素；

- `mainAxisSpacing`：主轴方向上的空隙间距；

- `crossAxisSpacing`：次轴方向上的空隙间距；

- `childAspectRatio`：子元素的宽高比例。

  ```dart
  import 'package:flutter/material.dart';
  
  void main() => runApp(MyApp());
  
  class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        title: 'Demo',
        home: Scaffold(
          appBar: AppBar(title: Text('ListView Widget')),
          body:GridView(
            gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
              crossAxisCount: 3,
              mainAxisSpacing: 2.0,    
              crossAxisSpacing: 3,     
              childAspectRatio: 0.7
            ),
            children: <Widget>[
              Image.network('http://img5.mtime.cn/mg/2020/07/27/185946.29931808.jpg',fit:BoxFit.cover),
              Image.network('http://img5.mtime.cn/mg/2020/07/27/141137.51502526_285X160X4.jpg',fit:BoxFit.cover),
              Image.network('http://img5.mtime.cn/mg/2020/07/27/185946.29931808.jpg',fit:BoxFit.cover),
              Image.network('http://img5.mtime.cn/mg/2020/07/27/132218.96111895_285X160X4.jpg',fit:BoxFit.cover),
              Image.network('http://img5.mtime.cn/mg/2020/07/27/185946.29931808.jpg',fit:BoxFit.cover),
              Image.network('http://img5.mtime.cn/mg/2020/07/27/123817.42229590_285X160X4.jpg',fit:BoxFit.cover)
            ],
          )
        ),
      );
    }
  }
  ```

  

#### RowWidget水平布局

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Row Widget Demo',
        home: Scaffold(
          appBar: AppBar(
            title: Text('水平方向布局'),
          ),
          body: Row(
            children: <Widget>[
              RaisedButton(
                  onPressed: () {},
                  color: Colors.redAccent,
                  child: Text('Red Button')),
              Expanded(
                child: RaisedButton(
                    onPressed: () {},
                    color: Colors.greenAccent,
                    child: Text('Green Button')),
              ),
              RaisedButton(
                  onPressed: () {},
                  color: Colors.yellowAccent,
                  child: Text('Yellow Button')),
              RaisedButton(
                  onPressed: () {},
                  color: Colors.blueAccent,
                  child: Text('Blue Button')),
            ],
          ),
        ));
  }
}
```

#### ColumnWidget垂直布局

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Row Widget Demo',
        home: Scaffold(
          appBar: AppBar(
            title: Text('垂直方向布局'),
          ),
          body: Center(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.center, //相对于当前文字居中对齐
              mainAxisAlignment: MainAxisAlignment.center,  //主轴
              children: <Widget>[
                Text('i am jingyile!'),
                // Expanded(
                // child:
                Text('i love running!\n'
                    'i love coding!\n'
                    'i love playing!\n'),
                // ),
                Text('i love meiyi!'),
              ],
            ),
          ),
        ));
  }
}
```

自行封装组件

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'Row Widget Demo',
        home: Scaffold(
          appBar: AppBar(
            title: Text('垂直方向布局'),
          ),
          body: Center(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.end, //相对于当前文字居中对齐
              mainAxisAlignment: MainAxisAlignment.start,
              children: <Widget>[
                mystyle1(),
                mystyle2(),
                Text('i love meiyi!'),
              ],
            ),
          ),
        ));
  }
}

class mystyle1 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return Text(
      'i am jingyile!',
      style: TextStyle(
        fontSize: 40.0,
        color: Color.fromARGB(255, 255, 125, 125),
        //字体颜色
      ),
    );
  }
}

class mystyle2 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return Text(
      'i love running!\n'
      'i love coding!\n'
      'i love playing!\n',
      style: TextStyle(
        fontSize: 40.0,
        color: Color.fromARGB(255, 255, 125, 125),
        //字体颜色
      ),
    );
  }
}

```

#### StackWidget层叠布局

简单的两个层叠组合 demo

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    var stack = new Stack(
      alignment: FractionalOffset(0.5, 0.9),  //对齐属性，一般只用于两个的层叠
      children: <Widget>[
        new CircleAvatar(
          //相当于头像
          backgroundImage: new NetworkImage(
              'http://img5.mtime.cn/mg/2020/07/27/185946.29931808.jpg'),
          radius: 100.0,
        ),
        new Container(
          decoration: BoxDecoration(color: Colors.white),
          padding: EdgeInsets.all(5.0),
          child: Text(
            'Hello!',
            style: TextStyle(
              fontSize: 20.0,
              color: Colors.black,
            ),
          ),
        )
      ],
    );
    return MaterialApp(
        title: 'Demo',
        home: Scaffold(
            appBar: AppBar(
              title: Text('头像demo'),
            ),
            body: Center(child: stack)));
  }
}
```

#### PositionedWidget层叠定位组件

一种比上述方式更方便的定位组件

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    var stack = new Stack(
      alignment: FractionalOffset(0.5, 0.9), //对齐属性，一般只用于两个的层叠
      children: <Widget>[
        new CircleAvatar(
          //相当于头像
          backgroundImage: new NetworkImage(
              'http://img5.mtime.cn/mg/2020/07/27/185946.29931808.jpg'),
          radius: 100.0,
        ),
        new Positioned(    //主角，像CSS的绝对定位
          top: 20.0,
          left: 80.0,
          child: Text(
            'hahaha',
            style: TextStyle(
              color: Colors.blue,
              fontSize: 25,
            ),
          ),
        ),
        new Positioned(    //主角
          top: 150.0,
          left: 20.0,
          child: Text(
            'lalala',
            style: TextStyle(
              color: Colors.green,
              fontSize: 25,
            ),
          ),
        ),
      ],
    );
    return MaterialApp(
        title: 'Demo',
        home: Scaffold(
            appBar: AppBar(
              title: Text('头像demo'),
            ),
            body: Center(child: stack)));
  }
}
```



#### CardWidget卡片布局组件

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    var card = new Card(
      child: Column(
        children: <Widget>[
          ListTile(
              title: Text('山东省烟台市莱山区',
                  style: TextStyle(fontWeight: FontWeight.w500)),
              subtitle: Text('17865569671'),
              leading: Icon(Icons.account_box, color: Colors.blue)),
          Divider(color: Colors.orange),
          ListTile(
              title: Text('甘肃省平凉市灵台县',
                  style: TextStyle(fontWeight: FontWeight.w500)),
              subtitle: Text('17865569671'),
              leading: Icon(Icons.account_box, color: Colors.blue)),
          Divider(color: Colors.orange),
          ListTile(
              title:
                  Text('云南省大理市', style: TextStyle(fontWeight: FontWeight.w500)),
              subtitle: Text('17865569671'),
              leading: Icon(Icons.account_box, color: Colors.blue)),
          Divider(color: Colors.orange),
        ],
      ),
    );
    return MaterialApp(
        title: 'Demo',
        home: Scaffold(
            appBar: AppBar(
              title: Text('卡片布局demo'),
            ),
            body: Center(child: card)));
  }
}
```

