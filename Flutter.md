Flutter

最近刚入坑Flutter+Dart ,在这里记录一下笔记。

目前机器环境：Windows10+Flutter+Dart+VS Code+AndroidSDK+夜神模拟器

咒语：一切皆组件,一切皆组件,一切皆组件!!!

没有Mac 没有Android设备 555....

入门和小实例参考代码来自技术胖的博客，https://jspang.com

## 最简单的入门

编写应用程序时，通常会创建新的widget，这些widget是无状态的[`StatelessWidget`](https://docs.flutter.io/flutter/widgets/StatelessWidget-class.html)或者是有状态的[`StatefulWidget`](https://docs.flutter.io/flutter/widgets/StatefulWidget-class.html)， 具体的选择取决于您的widget是否需要管理一些状态。widget的主要工作是实现一个[`build`](https://docs.flutter.io/flutter/widgets/StatelessWidget/build.html)函数，用以构建自身。一个widget通常由一些较低级别widget组成。Flutter框架将依次构建这些widget，直到构建到最底层的子widget时，这些最低层的widget通常为[`RenderObject`](https://docs.flutter.io/flutter/rendering/RenderObject-class.html)，它会计算并描述widget的几何形状。

State*less* widgets 是不可变的, 这意味着它们的属性不能改变 - 所有的值都是最终的.

State*ful* widgets 持有的状态可能在widget生命周期中发生变化. 实现一个 stateful widget 至少需要两个类:

1. 一个 StatefulWidget类。
2. 一个 State类。 StatefulWidget类本身是不变的，但是 State类在widget生命周期中始终存在

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

#### 导航父子页面的跳转返回

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(title: '导航演示01', home: FirstScreen()));
}

class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('导航页面')),
      body: Center(
          child: RaisedButton(
        child: Text('查看商品详情页'),
        onPressed: () {
          Navigator.push(
              context, MaterialPageRoute(builder: (context) => SecondScreen()));
        },//MaterialPageRoute 路由组件
      )),
    );
  }
}

class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(title: Text('我的商品详情页')),
        body: Center(
            child: RaisedButton(
                child: Text('返回'),
                onPressed: () {
                  Navigator.pop(context);
                })));
  }
}
```

#### 导航的参数传递和接受

 构造函数参数应使用命名参数，命名参数中的必要参数要添加@required标注，这样有利于静态代码分析器进行检查。

另外，在继承widget时，第一个参数通常应该是Key，另外，如果Widget需要接收子Widget，那么child或children参数通常应被放在参数列表的最后。同样是按照惯例，Widget的属性应尽可能的被声明为final，防止被意外改变。

```dart
import 'package:flutter/material.dart';

class Product {
  final String title;
  final String description;
  Product(this.title, this.description);
}

void main() {
  runApp(MaterialApp(
    title: '数据传输demo',
    home: ProductList(
        products: List.generate(20, (i) => Product('商品$i', '编号为:$i'))),
  ));
}

class ProductList extends StatelessWidget {
  final List<Product> products;
  ProductList({Key key, @required this.products}) : super(key: key);
  //构造函数的写法
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('商品列表')),
      body: ListView.builder(
        itemCount: products.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(products[index].title),
            onTap: () {
              Navigator.push(context, MaterialPageRoute(builder:(context)=>ProductDetail(product:products[index])));
            },
          );
        },
      ),
    );
  }
}

class ProductDetail extends StatelessWidget {
  final Product product;
  ProductDetail({Key key, @required this.product}):super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title:Text('${product.title}')),
      body:Center(
        child: Text('${product.description}'),),
    );
  }}

```

#### 页面跳转并返回数据

找小姐姐例子

```dart
import 'package:flutter/material.dart';

void main(){
  runApp(MaterialApp(
    title:'页面跳转返回数据',
    home:FirstPage()
  ));
}

class FirstPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar:AppBar(title:Text("找小姐姐要电话")),
      body:Center(
        child: RouteButton(),
      )
    );
  }
}

//跳转的Button
class RouteButton extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return RaisedButton(
      onPressed:(){
          _navigateToXiaoJieJie(context);
      },
      child: Text('去找小姐姐'),
    );
  }

  _navigateToXiaoJieJie(BuildContext context) async{ //async是启用异步方法

    final result = await Navigator.push(//等待
      context, 
      MaterialPageRoute(builder: (context)=> XiaoJieJie())
      );

      Scaffold.of(context).showSnackBar(SnackBar(content:Text('$result')));
  }
}

class XiaoJieJie extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar:AppBar(
        title:Text('我是小姐姐')
      ),
      body:Center(
        child:Column(
          children: <Widget>[
            RaisedButton(
              child: Text('大长腿小姐姐'),
              onPressed: (){
                Navigator.pop(context,'大长腿:1511008888');
              },
            ) ,
            RaisedButton(
              child: Text('小蛮腰小姐姐'),
              onPressed: (){
                Navigator.pop(context,'大长腿:1511009999');
              },
            ) ,
          ],
        ) 
      ) ,
    );
  }
}
```



#### 静态资源和项目图片的处理

如果想配置项目资源文件，就需要使用`pubspec.yaml`文件，需要把资源文件在这里声明。

比如在项目根目录下新建了一个`images`文件夹，文件夹下面放了一个图片，图片的名称叫做`002.jpg`，那我们在`pubspec.yaml`文件里就要写如下代码进行声明。

```yml
  assets:
    - images/002.jpg
```

有了声明后，我们就可以直接在项目中引用这个文件了。

```dart
import 'package:flutter/material.dart';

void main()=>runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      child: Image.asset('images/002.jpg'),
    );
  }
}
```

#### Flutter的打包

这节留着以后再尝试吧，目前用不到此功能。

## 一些小实例

#### 底部导航栏制作

flutter create demo...                 创建新的flutter项目

flutter packages get      拉取packages到本地，实现了强大的库管理功能。

`..add()`是Dart语言的..语法，简单来说就是返回调用者本身。这里list后用了..add()，还会返回list，然后就一直使用..语法，能一直想list里增加widget元素。 最后我们调用了父类的`initState()`方法。

`BottomNavigationBar`组件里提供了一个相应事件`onTap`，这个事件自带一个索引值`index`，通过索引值我们就可以和我们list里的索引值相对应了。

main.dart

```dart
import 'package:flutter/material.dart';
import 'BottomNavigationWidget.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter BottomNaavigationBar',
      theme: ThemeData.light(),
      home: BottomNavigationWidget(),
    );
  }
}

```

BottomNavigationWidget.dart

使用`StatefulWidget`分为两个部分，第一个部分是继承与`StatefullWidget`，第二个部分是继承于`State`.其实`State`部分才是我们的重点，主要的代码都会写在`State`中。

```dart
import 'package:flutter/material.dart';
import 'pages/airplay_screen.dart';
import 'pages/email_screen.dart';
import 'pages/pages_screen.dart';
import 'pages/home_screen.dart';

class BottomNavigationWidget extends StatefulWidget {     //快速构建动态widget stful
  @override
  _BottomNavigationWidgetState createState() => _BottomNavigationWidgetState();
}

class _BottomNavigationWidgetState extends State<BottomNavigationWidget> {
  final _BottomNavigationColor = Colors.blue; //内部使用一般用下划线开头
  int _currentIndex = 0;
  List<Widget> list = List();

  @override
  void initState() {
    list
      ..add(HomeScreen()) //相当于建造者模式  链式添加
      ..add(EmailScreen())
      ..add(PagesScreen())
      ..add(AirplayScreen());
    super.initState();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: list[_currentIndex], //忘写这句了...
      bottomNavigationBar: BottomNavigationBar(
        items: [
          BottomNavigationBarItem(
            icon: Icon(
              Icons.home,
              color: _BottomNavigationColor,
            ),
           // ImageIcon(    //图片形式的icon
              //AssetImage("images/myapp.png"),     
              //NetworkImage('http://jingyile.cn/9.115.png'),   
              
            title: Text(
              'home',
              style: TextStyle(color: _BottomNavigationColor),
            ),
          ),
          BottomNavigationBarItem(
            icon: Icon(
              Icons.email,
              color: _BottomNavigationColor,
            ),
            title:
                Text('Email', style: TextStyle(color: _BottomNavigationColor)),
          ),
          BottomNavigationBarItem(
            icon: Icon(
              Icons.pages,
              color: _BottomNavigationColor,
            ),
            title:
                Text('Pages', style: TextStyle(color: _BottomNavigationColor)),
          ),
          BottomNavigationBarItem(
            icon: Icon(
              Icons.airplay,
              color: _BottomNavigationColor,
            ),
            title: Text('AipPlay',
                style: TextStyle(color: _BottomNavigationColor)),
          ),
        ],
        currentIndex: _currentIndex,
        onTap: (int index) {
          setState(() {
            _currentIndex = index;
          });
        },
        // type: BottomNavigationBarType.fixed   //这句可以控制显示效果
      ),
    );
  }
}
```

home_screen.dart

```dart
import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('home'),
      ),
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
            ),
            ),
        ),
    );
  }
}
```

#### 不规则的底部工具栏

mian.dart

```dart
import 'package:flutter/material.dart';
import 'bottom_appBar_demo.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      //自定义主题样本
      theme: ThemeData(
        primarySwatch: Colors.red, //很多，自测
      ),
      home: BottomAppBarDemo(),
    );
  }
}
```

bottom_appBar_demo.dart

```dart
import 'package:flutter/material.dart';
import 'each_view.dart';

class BottomAppBarDemo extends StatefulWidget {
  _BottomAppBarDemoState createState() => _BottomAppBarDemoState();
}

class _BottomAppBarDemoState extends State<BottomAppBarDemo> {
  List<Widget> _eachView; //创建视图数组
  int _index = 0; //数组索引，通过改变索引值改变视图

  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    _eachView = List();
    _eachView..add(EachView('Home'))..add(EachView('Me'));
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: _eachView[_index],
      floatingActionButton: FloatingActionButton(
        //FAB 可交互的浮动按钮
        onPressed: () {
          Navigator.of(context)
              .push(MaterialPageRoute(builder: (BuildContext context) {
            return EachView('New Page');
          }));
        },
        tooltip: 'Increment', // 提示 长按显示..
        child: Icon(
          Icons.add,
          color: Colors.white,
        ),
      ),
      floatingActionButtonLocation: FloatingActionButtonLocation.centerDocked,
      //完全融合！！！
      bottomNavigationBar: BottomAppBar(
        // BottomNavigationBar为底部导航栏
        // BottomAppBar为底部工具栏
        color: Colors.red,
        shape: CircularNotchedRectangle(),
        child: Row(
          mainAxisSize: MainAxisSize.max,
          mainAxisAlignment: MainAxisAlignment.spaceAround,
          children: <Widget>[
            IconButton(
                icon: Icon(Icons.home),
                color: Colors.white,
                onPressed: () {
                  setState(() {
                    _index = 0;
                  });
                }),
            IconButton(
                icon: Icon(Icons.airport_shuttle),
                color: Colors.white,
                onPressed: () {
                  setState(() {
                    _index = 1;
                  });
                }),
          ],
        ),
      ),
    );
  }
}
```

each_view.dart     动态widget代替上个实例的4个静态的

```dart
import 'package:flutter/material.dart';

class EachView extends StatefulWidget {
  String _title;
  EachView(this._title);
  @override
  _EachViewState createState() => _EachViewState();
}

class _EachViewState extends State<EachView> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar:AppBar(title:Text(widget._title)),
      body: Center(child:Text(widget._title)),
    );
  }
}
```

示例：<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200731154141130.png" alt="image-20200731154141130" style="zoom:50%;" />



#### 路由跳转的动画效果

原理：重写并继承`PageRouterBuilder`这个类里的`transitionsBuilder`方法。

main.dart

```dart
import 'package:flutter/material.dart';
import 'pages.dart';

void main()=>runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title:'Flutter Demo',
      theme: new ThemeData(
        primarySwatch: Colors.blue,
      ),
      home:FirstPage()
    );
  }
}
```

pages.dart

elevation 属性：这个值是AppBar 滚动时的融合程度，一般有滚动时默认是4.0，现在设置成0.0，就是和也main完全融合了。

```dart
import 'package:flutter/material.dart';
import 'custome_router.dart';

class FirstPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        backgroundColor: Colors.blue,
        appBar: AppBar(
          title: Text('FirstPage', style: TextStyle(fontSize: 36.0)),
          elevation: 0.0, //默认4.0 ，与底部button融合效果
        ),
        body: Center(
          child: MaterialButton(
            child: Icon(
              Icons.navigate_next,
              color: Colors.white,
              size: 64.0,
            ),
            onPressed: () {
              //  这段默认路由很基础，多写写记下来！！！
              // Navigator.of(context).push(
              //   MaterialPageRoute(
              //     builder:(BuildContext context){
              //        return SecondPage();
              Navigator.of(context).push(CustomRoute(SecondPage())); //自定义路由
            },
          ),
        ));
  }
}

class SecondPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        backgroundColor: Colors.pinkAccent,
        appBar: AppBar(
          title: Text(
            'SecondPage',
            style: TextStyle(fontSize: 36.0),
          ),
          backgroundColor: Colors.pinkAccent,
          leading: Container(), //文字居中
          elevation: 4.0,    //！
        ),
        body: Center(
          child: MaterialButton(
            child: Icon(Icons.navigate_before, color: Colors.white, size: 64.0),
            onPressed: () => Navigator.of(context).pop(),    //返回原页面
          ),
        ));
  }
}
```

custome_router.dart

核心：重写并继承`PageRouterBuilder`这个类里的`transitionsBuilder`方法。

- FadeTransition:渐隐渐现过渡效果，主要设置opactiy（透明度）属性，值是0.0-1.0。

- animate :动画的样式，一般使用动画曲线组件（CurvedAnimation）。
- curve: 设置动画的节奏，也就是常说的曲线，Flutter准备了很多节奏，通过改变动画取消可以做出很多不同的效果。
- transitionDuration：设置动画持续的时间，建议再1和2之间。

```dart
import 'package:flutter/material.dart';

class CustomRoute extends PageRouteBuilder {
  final Widget widget;
  CustomRoute(this.widget)
      : super(
            transitionDuration: const Duration(seconds: 1),  //持续时间
            pageBuilder: (BuildContext context, Animation<double> animation1,
                Animation<double> animation2) {
              return widget;
            },
            transitionsBuilder: (BuildContext context,
                Animation<double> animation1,
                Animation<double> animation2,
                Widget child) {
              // 渐隐渐现的路由动画效果
              return FadeTransition(
                opacity: Tween(begin: 0.0, end: 1.0).animate(CurvedAnimation(
                    parent: animation1, //父级动画
                    curve: Curves.fastOutSlowIn //动画曲线 快出慢进
                    )),
                child: child,
              );
            });
}
```

常用动画效果：

缩放动画效果：

```dart
return ScaleTransition(
  scale:Tween(begin:0.0,end:1.0).animate(CurvedAnimation(
    parent:animation1,
    curve: Curves.fastOutSlowIn
    )),
    child:child,
);
```

旋转+缩放动画效果：

```dart
return RotationTransition(
  turns:Tween(begin:0.0,end:1.0)
  .animate(CurvedAnimation(
    parent: animation1,
    curve: Curves.fastOutSlowIn
  )),
  child:ScaleTransition(
    scale:Tween(begin: 0.0,end:1.0)
    .animate(CurvedAnimation(
        parent: animation1,
        curve:Curves.fastOutSlowIn
    )),
    child: child,
  )
);
```

左右滑动动画效果 (常用)

```dart
return SlideTransition(
  position: Tween<Offset>(
    begin: Offset(-1.0, 0.0),
    end:Offset(0.0, 0.0)
  )
  .animate(CurvedAnimation(
    parent: animation1,
    curve: Curves.fastOutSlowIn
  )),
  child: child,
);
```

#### 毛玻璃效果实现

以后的开发中可能会用到，还是少用，对系统消耗较大。

mian.dart

```dart
import 'package:flutter/material.dart';
import 'frosted_glass_demo.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title:'Flutter Demo',
      theme:ThemeData(
        primarySwatch: Colors.blue,
      ),
      home:Scaffold(
        body:FrostedGlassDemo(),
      )
    );
  }
}
```

frosted_glass_demo.dart

`BackdropFilter`就是背景滤镜组件，使用它可以给父元素增加滤镜效果，它里边最重要的一个属性是`filter`。 `filter`属性中要添加一个滤镜组件，实例中我们添加了图片滤镜组件，并给了模糊效果。

```dart
import 'package:flutter/material.dart';
import 'dart:ui';   //引入ui库，因为ImageFilter Widget在这个里边。

class FrostedGlassDemo extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body:Stack(   //重叠的Stack Widget，实现重贴
        children: <Widget>[
          ConstrainedBox( //约束盒子组件，添加额外的限制条件到 child上。
            constraints: const BoxConstraints.expand(), //限制条件，可扩展的。
            child:Image.network('https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1545738629147&di=22e12a65bbc6c4123ae5596e24dbc5d3&imgtype=0&src=http%3A%2F%2Fpic30.photophoto.cn%2F20140309%2F0034034413812339_b.jpg')
          ),
          Center(
            child: ClipRect(  //裁切长方形
              child: BackdropFilter(   //背景滤镜器
                filter: ImageFilter.blur(sigmaX: 5.0,sigmaY: 5.0), //图片模糊过滤，横向竖向都设置5.0
                child: Opacity( //透明控件
                  opacity: 0.5,
                  child: Container(// 容器组件
                    width: 500.0,
                    height: 700.0,.
                    decoration: BoxDecoration(color:Colors.grey.shade200), //盒子装饰器，进行装饰，设置颜色为灰色
                    child: Center(
                      child: Text(
                        'JSPang',
                        style: Theme.of(context).textTheme.display3, //设置比较酷炫的字体
                      ),
                    ),
                  ),
                ),
              ),
            ),
          )
        ],
      )
    );
  }
}
```

#### 保持页面状态

在工作中切换页面，再切换回来时,要求页面状态不发生改变。

这能给APP浏览者最好的体验，几乎所有的APP都有这个需求，属于一个大众需求。

这个demo没有路由跳转，先简单实现一下吧，后面用的时候再深究。

with是dart的关键字，意思是混入的意思，就是说可以将一个或者多个类的功能添加到自己的类无需继承这些类， 避免多重继承导致的问题。

需要注意的是with后边是Mixin，而不是普通的Widget   !!!

main.dart

```dart
import 'package:flutter/material.dart';
import 'keep_alive_demo.dart';
void main()=>runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme:ThemeData(
        primarySwatch: Colors.blue,
      ),
      home:KeepAliveDemo()
    );
  }
} 

class KeepAliveDemo extends StatefulWidget {
  _KeepAliveDemoState createState() => _KeepAliveDemoState();
}
/*
with是dart的关键字，意思是混入的意思，
就是说可以将一个或者多个类的功能添加到自己的类无需继承这些类，
避免多重继承导致的问题。
SingleTickerProviderStateMixin 主要是我们初始化TabController时，
需要用到vsync ，垂直属性，然后传递this
*/
class _KeepAliveDemoState extends State<KeepAliveDemo> with SingleTickerProviderStateMixin {
  TabController _controller;

  @override
  void initState(){
    super.initState();
    _controller = TabController(length:3, vsync: this);
  }

  //重写被释放的方法，只释放TabController
  @override
  void dispose(){
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar:AppBar(
        title:Text('Keep Alive Demo'),
          //TabBar是切换组件，它需要设置两个属性。
//controller: 控制器，后边跟的多是TabController组件。
//tabs：具体切换项，是一个数组，里边放的也是Tab Widget。
        bottom:TabBar(
          controller: _controller,
          tabs:[
            Tab(icon:Icon(Icons.directions_car)),
            Tab(icon:Icon(Icons.directions_transit)),
            Tab(icon:Icon(Icons.directions_bike)),
          ],
        )
      ),
      body:TabBarView(
        controller: _controller,
        children: <Widget>[
          MyHomePage(),
          MyHomePage(),
          MyHomePage()
        ],
      )
    );
  }
}
```

keep_alive_demo.dart

```dart
import 'package:flutter/material.dart';

class MyHomePage extends StatefulWidget {

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

//混入AutomaticKeepAliveClientMixin，这是保持状态的关键
//然后重写wantKeppAlive 的值为true。
class _MyHomePageState extends State<MyHomePage> with AutomaticKeepAliveClientMixin {
  int _counter = 0;
  //重写keepAlive 为ture ，就是可以有记忆功能了。
  @override
  bool get wantKeepAlive => true;
  //声明一个内部方法，用来点击按钮后增加数量
  void _incrementCounter(){
    setState() => _counter++;
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body:Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text('点一下加1，点一下加1:'),
            Text(
              '$_counter',
              style:Theme.of(context).textTheme.display1,
            )
          ],
        ),
      ),
      //增加一个悬浮按钮，点击时触犯_incrementCounter方法
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ),
    );
  }
}
```

#### 一个不简单的搜索条

main.dart

```dart
import 'package:flutter/material.dart';
import 'search_bar_demo.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title:'Flutter Demo',
      theme: ThemeData.light(),
      home: SearchBarDemo()
    );
  }
}
```

search_bar_demo.dart

点击图标时执行`searchBarDelegate` 类，这个类继承与`SearchDelegate`类，继承后要重写里边的四个方法

```dart
import 'package:flutter/material.dart';
import 'asset.dart';

class SearchBarDemo extends StatefulWidget {
  _SearchBarDemoState createState() => _SearchBarDemoState();
}

class _SearchBarDemoState extends State<SearchBarDemo> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(title: Text('SearchBarDemo'), actions: <Widget>[
      IconButton(
          icon: Icon(Icons.search),
          onPressed: () {
            showSearch(context: context, delegate: searchBarDelegate());
          }
          // showSearch(context:context,delegate: searchBarDelegate()),
          ),
    ]));
  }
}
//点击图标时执行`searchBarDelegate` 类，这个类继承与`SearchDelegate`类，继承后要重写里边的四个方法

class searchBarDelegate extends SearchDelegate<String> {
//buildActions方法时搜索条右侧的按钮执行方法，我们在这里方法里放入一个clear图标。 当点击图片时，清空搜索的内容。
  @override
  List<Widget> buildActions(BuildContext context) {
    return [
      IconButton(
        icon: Icon(Icons.clear),
        onPressed: () => query = "",
      )
    ];
  }
//buildLeading，这个是搜索栏左侧的图标和功能的编写，这里我们才用AnimatedIcon，然后在点击时关闭整个搜索页面
  @override
  Widget buildLeading(BuildContext context) {
    return IconButton(
        icon: AnimatedIcon(
            icon: AnimatedIcons.menu_arrow, progress: transitionAnimation),
        onPressed: () => close(context, null));
  }
//buildResults方法，是搜到到内容后的展现，因为我们的数据都是模拟的，所以我这里就使用最简单的Container+Card组件进行演示了，不做过多的花式修饰了。
  @override
  Widget buildResults(BuildContext context) {
    return Container(
      width: 100.0,
      height: 100.0,
      child: Card(
        color: Colors.redAccent,
        child: Center(
          child: Text(query),
        ),
      ),
    );
  }
//buildSuggestions，这个方法主要的作用就是设置推荐，就是我们输入一个字，然后自动为我们推送相关的搜索结果，这样的体验是非常好的。
  @override
  Widget buildSuggestions(BuildContext context) {
    final suggestionList = query.isEmpty
        ? recentSuggest
        : searchList.where((input) => input.startsWith(query)).toList();
    return ListView.builder(
        itemCount: suggestionList.length,
        itemBuilder: (context, index) => ListTile(
              title: RichText(
                  text: TextSpan(
                      text: suggestionList[index].substring(0, query.length),
                      style: TextStyle(
                          color: Colors.black, fontWeight: FontWeight.bold),
                      children: [
                    TextSpan(
                        text: suggestionList[index].substring(query.length),
                        style: TextStyle(color: Colors.grey))
                  ])),
            ));
  }
}
```

asset.dart

`asset.dart`相当于数据文件，工作中这些数据是后台传递给我们，或者写成配置文件的，这里我们就以List的方式代替了。我们在这个文件中定义了两个List：

- searchList : 这个相当于数据库中的数据，我们要在这里进行搜索。
- recentSuggest ： 目前的推荐数据，就是搜索时，自动为我们进行推荐。

```dart
const searchList = [
  "jiejie-大长腿",
  "jiejie-水蛇腰",
  "gege1-帅气欧巴",
  "gege2-小鲜肉"
];

const recentSuggest = [
  "jiejie",
  "gege"
];
```

#### 模拟添加照片(流式布局)

main.dart

```dart
import 'package:flutter/material.dart';
import 'warp_demo.dart';

void main()=>runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: new ThemeData.dark(),
      home:WarpDemo()
    );
  }
}
```

warp_demo.dart

```dart
import 'package:flutter/material.dart';


//继承与动态组件
class WarpDemo extends StatefulWidget {
  _WarpDemoState createState() => _WarpDemoState();
}

class _WarpDemoState extends State<WarpDemo> {
  List<Widget> list;  //声明一个list数组

  @override
  //初始化状态，给list添加值，这时候调用了一个自定义方法`buildAddButton`
  void initState() { 
    super.initState();
    list = List<Widget>()..add(buildAddButton());
  }


  @override
  Widget build(BuildContext context) {
    //得到屏幕的高度和宽度，用来设置Container的宽和高
    final width = MediaQuery.of(context).size.width;
    final height = MediaQuery.of(context).size.height;



    return Scaffold(
      appBar: AppBar(
        title: Text('Wrap流式布局'),
      ),
      body:Center(
        child: Opacity(
          opacity: 0.8,
          child: Container(
            width: width,
            height: height/2,
            color: Colors.grey,
            child: Wrap(    //流式布局，
              children: list,
              spacing: 26.0,  //设置间距
            ),
          ),
        ),
      )
    );
  }

  Widget buildAddButton(){
    //返回一个手势Widget，只用用于显示事件
    return  GestureDetector(
      onTap:(){
        if(list.length<9){
          setState(() {
                list.insert(list.length-1,buildPhoto());
          });
        }
      },
      child: Padding(
        padding:const EdgeInsets.all(8.0),
        child: Container(
          width: 80.0,
          height: 80.0,
          color: Colors.black54,
          child: Icon(Icons.add),
        ),
      ),
    );
  }


  Widget buildPhoto(){
    return Padding(
        padding: const EdgeInsets.all(8.0),
        child: Container(
          width: 80.0,
          height: 80.0,
          color: Colors.amber,
          child: Center(
            child: Text('照片'),
          ),
        ),
    );
  }

}
```

`GestureDetector`它是一个Widget，但没有任何的显示功能，而只是一个手势操作，用来触发事件的。虽然很多Button组件是有触发事件的，比如点击，但是也有一些组件是没有触发事件的，比如：Padding、Container、Center这时候我们想让它有触发事件就需要再它们的外层增加一个`GestureDetector`，比如我们让Padding有触发事件，代码如下：

```dart
Widget buildAddButton(){
    return  GestureDetector(
      onTap:(){
        if(list.length<9){
          setState(() {
                list.insert(list.length-1,buildPhoto());
          });
        }
      },
      child: Padding(
        padding:const EdgeInsets.all(8.0),
        child: Container(
          width: 80.0,
          height: 80.0,
          color: Colors.black54,
          child: Icon(Icons.add),
        ),
      ),
    );
  }
```

#### Draggable控件实例

main.dart 文件：

```dart
import 'package:flutter/material.dart';
import 'draggable_demo.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title:'Flutter Demo',
      theme:ThemeData(
        primarySwatch: Colors.blue
      ),
      home:DraggableDemo()
    );
  }
}
```

draggable_demo.dart 文件

`DragTarget`是用来接收拖拽事件的控件，当把`Draggable`放到`DragTarget`里时，他会接收`Draggable`传递过来的值，然后用生成器改变组件状态。

- onAccept:当推拽到控件里时触发，经常在这里得到传递过来的值。
- builder: 构造器，里边进行修改child值。 

```dart
import 'package:flutter/material.dart';

import 'draggable_widget.dart';

class DraggableDemo extends StatefulWidget {
  @override
  _DraggableDemoState createState() => _DraggableDemoState();
}

class _DraggableDemoState extends State<DraggableDemo> {
  Color _draggableColor = Colors.grey;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: Stack(
      children: <Widget>[
        DraggableWidget(
          offset: Offset(80.0, 80.0),
          widgetColor: Colors.tealAccent,
        ),
        DraggableWidget(
          offset: Offset(180.0, 80.0),
          widgetColor: Colors.redAccent,
        ),
        Center(
            //接收
          child: DragTarget(onAccept: (Color color) {
            _draggableColor = color;
          }, builder: (context, candidateData, rejectedData) {
            return Container(
              width: 200.0,
              height: 200.0,
              color: _draggableColor,
            );
          }),
        )
      ],
    ));
  }
}
```

draggable_widget.dart 文件

`Draggable`控件负责就是拖拽，父层使用了`Draggable`，它的子元素就是可以拖动的，子元素可以实容器，可以是图片。用起来非常的灵活。

参数说明：

- `data`: 是要传递的参数，在`DragTarget`里，会接受到这个参数。当然要在拖拽控件推拽到`DragTarget`的时候。
- `child`:在这里放置你要推拽的元素，可以是容器，也可以是图片和文字。
- `feedback`: 常用于设置推拽元素时的样子，在案例中当推拽的时候，我们把它的颜色透明度变成了50%。当然你还可以改变它的大小。
- `onDraggableCanceled`:是当松开时的相应事件，经常用来改变推拽时到达的位置，改变时用`setState`来进行。

```dart
import 'package:flutter/material.dart';

class DraggableWidget extends StatefulWidget {
  final Offset offset;
  final Color widgetColor;
  const DraggableWidget({Key key, this.offset, this.widgetColor}):super(key:key);
  _DraggableWidgetState createState() => _DraggableWidgetState();
}

class _DraggableWidgetState extends State<DraggableWidget> {
  Offset offset = Offset(0.0,0.0);
  @override
  void initState() {
    super.initState();
    offset = widget.offset;
  }

  @override
  Widget build(BuildContext context) {
   return Positioned(
     left: offset.dx,
     top:offset.dy,
     child: Draggable(  //拖拽
       data:widget.widgetColor,
       child: Container(
         width: 100,
         height: 100,
         color:widget.widgetColor,
       ),
       feedback:Container(
         width: 100.0,
         height: 100.0,
         color: widget.widgetColor.withOpacity(0.5),
       ),
       onDraggableCanceled: (Velocity velocity, Offset offset){
         setState(() {
            this.offset = offset;
         });
       },
     ),
   );
  }
}
```

#### Flutter中文网小实例

pubspec.yml

```yaml
dependencies:
  flutter:
    sdk: flutter


  # The following adds the Cupertino Icons font to your application.
  # Use with the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^0.1.3
  english_words: ^3.1.0
```

main.dart

```dart
import 'package:flutter/material.dart';
import 'package:english_words/english_words.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: '小熊饼干',
      // theme: ThemeData.dark(),
      theme: ThemeData(primarySwatch: Colors.orange),
      home: RandomWords(),
    );
  }
}

class RandomWords extends StatefulWidget {
  @override
  _RandomWordsState createState() => _RandomWordsState();
}

class _RandomWordsState extends State<RandomWords> {
  final _suggestions = <WordPair>[];                      //保存建议的单词对
  final _biggerFont = const TextStyle(fontSize: 18.0);    //增大字体！
  final _saved = new Set<WordPair>();                     //保存用户喜欢的单词对

  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: new AppBar(
        title: new Text('Startup Name Generator'),
        actions: <Widget>[
          new IconButton(icon: new Icon(Icons.favorite), onPressed: _pushSaved),
        ],
      ),
      body: _buildSuggestions(),
    );
  }

  void _pushSaved() {
    Navigator.of(context).push(
    new MaterialPageRoute(
      builder: (context) {
        final tiles = _saved.map(
          (pair) {
            return new ListTile(
              title: new Text(
                pair.asPascalCase,
                style: _biggerFont,
              ),
            );
          },
        );
        final divided = ListTile
          .divideTiles(
            context: context,
            tiles: tiles,
          )
          .toList();
          return new Scaffold(
          appBar: new AppBar(
            title: new Text('Saved Suggestions'),
          ),
          body: new ListView(children: divided),
        );
      },
    ),
    );
  }

//Tip: “驼峰命名法” (称为 “upper camel case” 或 “Pascal case” ), 表示字符串中的每个单词（包括第一个单词）都以大写字母开头。
  Widget _buildRow(WordPair pair) {
    final alreadySaved = _saved.contains(pair);
    return new ListTile(
      title: new Text(
        pair.asPascalCase,
        style: _biggerFont,
      ),
      trailing: new Icon(
      alreadySaved ? Icons.favorite : Icons.favorite_border,
      color: alreadySaved ? Colors.red : null,
    ),
    onTap: () {
      setState(() {
        if (alreadySaved) {
          _saved.remove(pair);
        } else {
          _saved.add(pair);
        }
      });
    },
    );
    
  }

  Widget _buildSuggestions() {    //构建显示建议单词对的ListView
    return new ListView.builder(
        padding: const EdgeInsets.all(16.0),
        // 对于每个建议的单词对都会调用一次itemBuilder，然后将单词对添加到ListTile行中
        // 在偶数行，该函数会为单词对添加一个ListTile row.
        // 在奇数行，该函数会添加一个分割线widget，来分隔相邻的词对。
        // 注意，在小屏幕上，分割线看起来可能比较吃力。
        itemBuilder: (context, i) {
          // 在每一列之前，添加一个1像素高的分隔线widget
          if (i.isOdd) return new Divider();

          // 语法 "i ~/ 2" 表示i除以2，但返回值是整形（向下取整），比如i为：1, 2, 3, 4, 5
          // 时，结果为0, 1, 1, 2, 2， 这可以计算出ListView中减去分隔线后的实际单词对数量
          final index = i ~/ 2;
          // 如果是建议列表中最后一个单词对
          if (index >= _suggestions.length) {
            // ...接着再生成10个单词对，然后添加到建议列表
            _suggestions.addAll(generateWordPairs().take(10));
          }
          return _buildRow(_suggestions[index]);
          // return Text(_suggestions[index].asPascalCase);
        });
  }
}
```



































## Widget常用组件

#### MaterialApp

MaterialApp是我们app开发中常用的符合MaterialApp Design设计理念的入口Widget

```dart
MaterialApp({
  Key key,
  this.title = '', // 设备用于为用户识别应用程序的单行描述
  this.theme, // 应用程序小部件使用的颜色。  
  this.home, // 应用程序默认路由的小部件,用来定义当前应用打开的时候，所显示的界面
 ----------------------------------------------不常用-------------------------------------------------   
  this.color, // 在操作系统界面中应用程序使用的主色。  
  this.routes = const <String, WidgetBuilder>{}, // 应用程序的顶级路由表
  this.navigatorKey, // 在构建导航器时使用的键。
  this.initialRoute, // 如果构建了导航器，则显示的第一个路由的名称
  this.onGenerateRoute, // 应用程序导航到指定路由时使用的路由生成器回调
  this.onUnknownRoute, // 当 onGenerateRoute 无法生成路由(initialRoute除外)时调用
  this.navigatorObservers = const <NavigatorObserver>[], // 为该应用程序创建的导航器的观察者列表
  this.builder, // 用于在导航器上面插入小部件，但在由WidgetsApp小部件创建的其他小部件下面插入小部件，或用于完全替换导航器
  this.onGenerateTitle, // 如果非空，则调用此回调函数来生成应用程序的标题字符串，否则使用标题。
  this.locale, // 此应用程序本地化小部件的初始区域设置基于此值。
  this.localizationsDelegates, // 这个应用程序本地化小部件的委托。
  this.localeListResolutionCallback, // 这个回调负责在应用程序启动时以及用户更改设备的区域设置时选择应用程序的区域设置。
  this.localeResolutionCallback, // 
  this.supportedLocales = const <Locale>[Locale('en', 'US')], // 此应用程序已本地化的地区列表 
  this.debugShowMaterialGrid = false, // 打开绘制基线网格材质应用程序的网格纸覆盖
  this.showPerformanceOverlay = false, // 打开性能叠加
  this.checkerboardRasterCacheImages = false, // 打开栅格缓存图像的棋盘格
  this.checkerboardOffscreenLayers = false, // 打开渲染到屏幕外位图的图层的棋盘格
  this.showSemanticsDebugger = false, // 打开显示框架报告的可访问性信息的覆盖
  this.debugShowCheckedModeBanner = true, // 在选中模式下打开一个小的“DEBUG”横幅，表示应用程序处于选中模式
}) 
```

#### ThemeData

ThemeData用于自定义应用程序的主题颜色和排版等

```dart
factory ThemeData({
  MaterialColor primarySwatch,// 定义一个单一的颜色以及十个色度的色块。
  Color primaryColor, // 应用程序主要部分的背景颜色(toolbars、tab bars 等)
  ----------------------------------------------不常用-------------------------------------------------   
  Brightness brightness, // 应用整体主题的亮度。用于按钮之类的小部件，以确定在不使用主色或强调色时选择什么颜色。
  Brightness primaryColorBrightness, // primaryColor的亮度。用于确定文本的颜色和放置在主颜色之上的图标(例如工具栏文本)。
  Color primaryColorLight, // primaryColor的浅色版
  Color primaryColorDark, // primaryColor的深色版
  Color accentColor, // 小部件的前景色(旋钮、文本、覆盖边缘效果等)。
  Brightness accentColorBrightness, // accentColor的亮度。
  Color canvasColor, //  MaterialType.canvas 的默认颜色
  Color scaffoldBackgroundColor, // Scaffold的默认颜色。典型Material应用程序或应用程序内页面的背景颜色。
  Color bottomAppBarColor, // BottomAppBar的默认颜色
  Color cardColor, // Card的颜色
  Color dividerColor, // Divider和PopupMenuDivider的颜色，也用于ListTile之间、DataTable的行之间等。
  Color highlightColor, // 选中在泼墨动画期间使用的突出显示颜色，或用于指示菜单中的项。
  Color splashColor,  // 墨水飞溅的颜色。InkWell
  InteractiveInkFeatureFactory splashFactory, // 定义由InkWell和InkResponse反应产生的墨溅的外观。
  Color selectedRowColor, // 用于突出显示选定行的颜色。
  Color unselectedWidgetColor, // 用于处于非活动(但已启用)状态的小部件的颜色。例如，未选中的复选框。通常与accentColor形成对比。也看到disabledColor。
  Color disabledColor, // 禁用状态下部件的颜色，无论其当前状态如何。例如，一个禁用的复选框(可以选中或未选中)。
  Color buttonColor, // RaisedButton按钮中使用的Material 的默认填充颜色。
  ButtonThemeData buttonTheme, // 定义按钮部件的默认配置，如RaisedButton和FlatButton。
  Color secondaryHeaderColor, // 选定行时PaginatedDataTable标题的颜色。
  Color textSelectionColor, // 文本框中文本选择的颜色，如TextField
  Color cursorColor, // 文本框中光标的颜色，如TextField
  Color textSelectionHandleColor,  // 用于调整当前选定的文本部分的句柄的颜色。
  Color backgroundColor, // 与主色形成对比的颜色，例如用作进度条的剩余部分。
  Color dialogBackgroundColor, // Dialog 元素的背景颜色
  Color indicatorColor, // 选项卡中选定的选项卡指示器的颜色。
  Color hintColor, // 用于提示文本或占位符文本的颜色，例如在TextField中。
  Color errorColor, // 用于输入验证错误的颜色，例如在TextField中
  Color toggleableActiveColor, // 用于突出显示Switch、Radio和Checkbox等可切换小部件的活动状态的颜色。
  String fontFamily, // 文本字体
  TextTheme textTheme, // 文本的颜色与卡片和画布的颜色形成对比。
  TextTheme primaryTextTheme, // 与primaryColor形成对比的文本主题
  TextTheme accentTextTheme, // 与accentColor形成对比的文本主题。
  InputDecorationTheme inputDecorationTheme, // 基于这个主题的 InputDecorator、TextField和TextFormField的默认InputDecoration值。
  IconThemeData iconTheme, // 与卡片和画布颜色形成对比的图标主题
  IconThemeData primaryIconTheme, // 与primaryColor形成对比的图标主题
  IconThemeData accentIconTheme, // 与accentColor形成对比的图标主题。
  SliderThemeData sliderTheme,  // 用于呈现Slider的颜色和形状
  TabBarTheme tabBarTheme, // 用于自定义选项卡栏指示器的大小、形状和颜色的主题。
  CardTheme cardTheme, // Card的颜色和样式
  ChipThemeData chipTheme, // Chip的颜色和样式
  TargetPlatform platform, 
  MaterialTapTargetSize materialTapTargetSize, // 配置某些Material部件的命中测试大小
  PageTransitionsTheme pageTransitionsTheme, 
  AppBarTheme appBarTheme, // 用于自定义Appbar的颜色、高度、亮度、iconTheme和textTheme的主题。
  BottomAppBarTheme bottomAppBarTheme, // 自定义BottomAppBar的形状、高度和颜色的主题。
  ColorScheme colorScheme, // 拥有13种颜色，可用于配置大多数组件的颜色。
  DialogTheme dialogTheme, // 自定义Dialog的主题形状
  Typography typography, // 用于配置TextTheme、primaryTextTheme和accentTextTheme的颜色和几何TextTheme值。
  CupertinoThemeData cupertinoOverrideTheme 
})
```

#### Scaffold

Scaffold翻译过来就是脚手架的意思，它实现了基本的 Material Design 可视化布局结构。

此类提供了用于显示drawer、snackbar和底部sheet的API。

简单的说，Scaffold就是一个提供 Material Design 设计中基本布局的 widget。

```dart
const Scaffold({
  Key key,
  this.appBar, // 标题栏
  this.body,  // 用于显示当前界面主要内容的Widget
  ---------------------------------------------不常用------------------------------------------------- 
  this.floatingActionButton, // 一个悬浮在body上的按钮，默认显示在右下角
  this.floatingActionButtonLocation, // 用于设置floatingActionButton显示的位置
  this.floatingActionButtonAnimator, // floatingActionButton移动到一个新的位置时的动画
  this.persistentFooterButtons, // 多状态按钮
  this.drawer, // 左侧的抽屉菜单
  this.endDrawer, //  右'侧的抽屉菜单
  this.bottomNavigationBar,// 底部导航栏。
  this.bottomSheet, // 显示在底部的工具栏
  this.backgroundColor,// 内容的背景颜色
  this.resizeToAvoidBottomPadding = true, // 控制界面内容 body 是否重新布局来避免底部被覆盖，比如当键盘显示的时候，重新布局避免被键盘盖住内容。
  this.primary = true,// Scaffold是否显示在页面的顶部
}) 
```

#### AppBar

```dart
    AppBar({
    Key key,
    this.title,//Toolbar 中主要内容，通常显示为当前界面的标题文字
    this.actions,//一个 Widget 列表，代表 Toolbar 中所显示的菜单，对于常用的菜单，通常使用 IconButton 来表示；对于不常用的菜单通常使用 PopupMenuButton 来显示为三个点，点击后弹出二级菜单
    ---------------------------------------------不常用------------------------------------------------- 
    this.leading,//在标题前面显示的一个控件，在首页通常显示应用的 logo；在其他界面通常显示为返回按钮
    this.automaticallyImplyLeading = true,
    this.flexibleSpace,//一个显示在 AppBar 下方的控件，高度和 AppBar 高度一样，可以实现一些特殊的效果，该属性通常在 SliverAppBar 中使用
    this.bottom,//一个 AppBarBottomWidget 对象，通常是 TabBar。用来在 Toolbar 标题下面显示一个 Tab 导航栏
    this.elevation = 4.0,//纸墨设计中控件的 z 坐标顺序，默认值为 4，对于可滚动的 SliverAppBar，当 SliverAppBar 和内容同级的时候，该值为 0， 当内容滚动 SliverAppBar 变为 Toolbar 的时候，修改 elevation 的值
    this.backgroundColor,//APP bar 的颜色，默认值为 ThemeData.primaryColor。改值通常和下面的三个属性一起使用
    this.brightness,//App bar 的亮度，有白色和黑色两种主题，默认值为 ThemeData.primaryColorBrightness
    this.iconTheme,//App bar 上图标的颜色、透明度、和尺寸信息。默认值为 ThemeData.primaryIconTheme
    this.textTheme,//App bar 上的文字样式。默认值为 ThemeData.primaryTextTheme
    this.primary = true,
    this.centerTitle,//标题是否居中显示，默认值根据不同的操作系统，显示方式不一样,true居中 false居左
    this.titleSpacing = NavigationToolbar.kMiddleSpacing,
    this.toolbarOpacity = 1.0,
    this.bottomOpacity = 1.0,
    })
```

#### Navigator

`Navigator`是一个路由管理的组件，它提供了打开和退出路由页方法。

`Navigator`通过一个栈来管理活动路由集合。通常当前屏幕显示的页面就是栈顶的路由。

`Navigator`提供了一系列方法来管理路由栈，最常用的两个方法：

Navigator类中第一个参数为context的**静态方法**都对应一个Navigator的**实例方法**，

```dart
Navigator.push(BuildContext context, Route route)  等价于
Navigator.of(context).push(Route route)
    
Future push(BuildContext context, Route route)
//将给定的路由入栈（即打开新的页面），返回值是一个`Future`对象，用以接收新路由出栈（即关闭）时的返回数据。
bool pop(BuildContext context, [ result ])
//将栈顶路由出栈，`result`为页面关闭时返回给上一个页面的数据。
```

#### MaterialPageRoute

`MaterialPageRoute`继承自`PageRoute`类，`PageRoute`类是一个抽象类，表示占有整个屏幕空间的一个模态路由页面，它还定义了路由构建及切换时过渡动画的相关接口及属性。`MaterialPageRoute` 是Material组件库提供的组件，它可以针对不同平台，实现与平台页面切换动画风格一致的路由切换动画：

- 对于Android，当打开新页面时，新的页面会从屏幕底部滑动到屏幕顶部；当关闭页面时，当前页面会从屏幕顶部滑动到屏幕底部后消失，同时上一个页面会显示到屏幕上。
- 对于iOS，当打开页面时，新的页面会从屏幕右侧边缘一致滑动到屏幕左边，直到新页面全部显示到屏幕上，而上一个页面则会从当前屏幕滑动到屏幕左侧而消失；当关闭页面时，正好相反，当前页面会从屏幕右侧滑出，同时上一个页面会从屏幕左侧滑入。

```dart
MaterialPageRoute({
    WidgetBuilder builder,//WidgetBuilder类型的回调函数，它的作用是构建路由页面的具体内容，返回值是一个widget。我们通常要实现此回调，返回新路由的实例。
    ---------------------------------------------不常用-------------------------------------------------
    RouteSettings settings,//包含路由的配置信息，如路由名称、是否初始路由（首页）。
    bool maintainState = true,//默认情况下，当入栈一个新路由时，原来的路由仍然会被保存在内存中，如果想在路由没用的时候释放其所占用的所有资源，可以设置maintainState为false。
    bool fullscreenDialog = false,//表示新的路由页面是否是一个全屏的模态对话框
    //在iOS中，如果fullscreenDialog为true，新页面将会从屏幕底部滑入（而不是水平方向）。
  })
```

#### Text

```dart
const Text(this.data, // 内容
{
  Key key,
  this.textAlign, // 对齐方式
  this.overflow, // 超出屏幕显示方式
  this.maxLines, // 最大行数
  this.style, // 样式
  ---------------------------------------------不常用-------------------------------------------------
  this.strutStyle, // 使用的支柱风格
  this.textDirection, // 文本方向
  this.locale, //
  this.softWrap, // 是否允许换行显示
  this.textScaleFactor, // 每个逻辑像素的字体像素数，
  this.semanticsLabel, // 文本的另一个语义标签
})

// 可以显示不同样式textSpan的段落。
const Text.rich(this.textSpan, {
  Key key,
  this.style,
  this.strutStyle,
  this.textAlign,
  this.textDirection,
  this.locale,
  this.softWrap,
  this.overflow,
  this.textScaleFactor,
  this.maxLines,
  this.semanticsLabel,
})

// 需配合Text.rich一起使用
const TextSpan({
  this.style,   //样式
  this.text,   //内容
  this.children,  //一个TextSpan的数组，也就是说TextSpan可以包括其他TextSpan
  this.recognizer, //用于对该文本片段上用于手势进行识别处理
});
```

#### TextStyle

```dart
const TextStyle({
  this.inherit = true,//是否继承父 Text 的样式，默认为 true 如果为false，且样式没有设置具体的值，则采用默认值
  this.color, // 字体颜色
  this.fontSize, // 字体大小
  this.decoration, // 装饰
  this.decorationColor,// 装饰颜色
  this.decorationStyle, // 装饰样式
  ---------------------------------------------不常用-------------------------------------------------  
  this.fontWeight, 
  this.fontStyle,  
  this.letterSpacing, // 字间距
  this.wordSpacing, // 字符间距
  this.textBaseline,
  this.height, // 行高
  this.locale,
  this.foreground, // 前景色
  this.background, // 背景色
  this.shadows, // 阴影
  this.debugLabel,
  String fontFamily, // 字体
  List<String> fontFamilyFallback,
  String package,
})
```

#### Container

`Container`是一个组合类容器，它本身不对应具体的`RenderObject`，它是`DecoratedBox`、`ConstrainedBox、Transform`、`Padding`、`Align`等组件组合的一个多功能容器，所以我们只需通过一个`Container`组件可以实现同时需要装饰、变换、限制的场景。

```dart
Container({
  this.child,
  this.alignment,
  double width,//容器的宽度
  double height, //容器的高度
  this.padding, //容器内补白，属于decoration的装饰范围
  this.margin,//容器外补白，不属于decoration的装饰范围
  Color color, // 背景色
  ---------------------------------------------不常用------------------------------------------------- 
  Decoration decoration, // 背景装饰    
  Decoration foregroundDecoration, //前景装饰
  BoxConstraints constraints, //容器大小的限制条件
  this.transform, //变换
})
```

- 容器的大小可以通过`width`、`height`属性来指定，也可以通过`constraints`来指定；如果它们同时存在时，`width`、`height`优先。实际上Container内部会根据`width`、`height`来生成一个`constraints`。
- `color`和`decoration`是互斥的，如果同时设置它们则会报错！实际上，当指定`color`时，`Container`内会自动创建一个`decoration`。

#### ListView

emmm,先简单参考入门篇

`ListView`是最常用的可滚动组件之一，它可以沿一个方向线性排布所有子组件，并且它也支持基于Sliver的延迟构建模型。

```dart
ListView({
  ...  
  //可滚动widget公共参数
  Axis scrollDirection = Axis.vertical,  //默认竖向
  //  scrollDirection: Axis.horizontal, //横向
  //  scrollDirection: Axis.vertical,  //竖向
  bool reverse = false,
  ScrollController controller,
  bool primary,
  ScrollPhysics physics,
  EdgeInsetsGeometry padding,

  //ListView各个构造函数的共同参数  
  double itemExtent,
  bool shrinkWrap = false,
  bool addAutomaticKeepAlives = true,
  bool addRepaintBoundaries = true,
  double cacheExtent,

  //子widget列表
  List<Widget> children = const <Widget>[], //！！！
})
```

可滚动组件通过一个List来作为其children属性时，只适用于子组件较少的情况，这是一个通用规律，并非`ListView`自己的特性，像`GridView`也是如此。

`ListView.builder`适合列表项比较多（或者无限）的情况，因为只有当子组件真正显示的时候才会被创建，也就说通过该构造函数创建的`ListView`是支持基于Sliver的懒加载模型的。

```dart
ListView.builder({
  // ListView公共参数已省略  
  ...
  @required IndexedWidgetBuilder itemBuilder,
  int itemCount,
  ...
})
```

- `itemBuilder`：它是列表项的构建器，类型为`IndexedWidgetBuilder`，返回值为一个widget。当列表滚动到具体的`index`位置时，会调用该构建器构建列表项。
- `itemCount`：列表项的数量，如果为`null`，则为无限列表

小例子：

```dart
ListView.builder(
    itemCount: 100,
    itemExtent: 50.0, //强制高度为50.0
    itemBuilder: (BuildContext context, int index) {
      return ListTile(title: Text("$index"));
    }
);
```



#### ListTile

```dart
const ListTile({
    Key key,
    this.leading,              // item 前置图标
    this.title,                // item 标题
    ---------------------------------------------不常用------------------------------------------------- 
    this.subtitle,             // item 副标题
    this.trailing,             // item 后置图标
    this.isThreeLine = false,  // item 是否三行显示
    this.dense,                // item 直观感受是整体大小
    this.contentPadding,       // item 内容内边距
    this.enabled = true,
    this.onTap,                // item onTap 点击事件
    this.onLongPress,          // item onLongPress 长按事件
    this.selected = false,     // item 是否选中状态
  })
```















































## 要实现的UI页面

#### 底部标签   

参考：https://github.com/LiuC520/flutter_bottom_tab_bar

我的实现：https://github.com/jingyile/Flutter_bottom_bar

#### 图标库

https://material.io/resources/icons



#### 启动页

main.dart

```dart
import 'package:flutter/material.dart';
import 'splash_screen.dart';

void main() =>runApp(MyApp()) ;

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'demo',
      theme: ThemeData.light(),
      home:SplashScreen()
    );
  }
}
```

splash_screen.dart

```dart
import 'package:flutter/material.dart';
import 'home_page.dart';

class SplashScreen extends StatefulWidget {
  _SplashScreenState createState() => _SplashScreenState();
}

class _SplashScreenState extends State<SplashScreen>
    with SingleTickerProviderStateMixin {
  AnimationController _controller;
  Animation _animation;

  void initState() {
    super.initState();
    _controller = AnimationController(
        vsync: this, duration: Duration(milliseconds: 10000));
    _animation = Tween(begin: 0.0, end: 1.0).animate(_controller);
    /*动画事件监听器，
    它可以监听到动画的执行状态，
    这里只监听动画是否结束，
    如果结束则执行页面跳转动作。 */
    _animation.addStatusListener((status) {
      if (status == AnimationStatus.completed) {
        Navigator.of(context).pushAndRemoveUntil(
            MaterialPageRoute(builder: (context) => MyHomePage()),
            (route) => route == null);
      }
    });
    //播放动画
    _controller.forward();
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    final width = MediaQuery.of(context).size.width;
    final height = MediaQuery.of(context).size.height;
    return FadeTransition(
      //透明度动画组件
      opacity: _animation, //执行动画
      child: Image.asset(
          //网络图片
          'img/启动页.png',
          // scale: 2.0,  //进行缩放
          // width: width,
          // height: height,
          fit: BoxFit.cover // 充满父容器
          ),
    );
  }
}
```

home_page.dart

```dart
import 'package:flutter/material.dart';

class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('首页')),
      body: Center(
        child: Text("我是首页"),
      ),
    );
  }
}
```

#### 登录页

main.dart

```dart
import 'package:flutter/material.dart';
import 'login_page.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Sample App',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: LoginPage(),
    );
  }
}
```

login_page.dart

```dart
import 'package:flutter/material.dart';

class LoginPage extends StatefulWidget {
  @override
  _LoginPageState createState() => _LoginPageState();
}

class _LoginPageState extends State<LoginPage> {
  final _formKey = new GlobalKey<FormState>();

  String _userID;
  String _password;
  bool _isChecked = true;
  bool _isLoading;
  IconData _checkIcon = Icons.check_box;

  void _changeFormToLogin() {
    _formKey.currentState.reset();
  }

  void _onLogin() {
    final form = _formKey.currentState;
    form.save();

    if (_userID == '') {
      _showMessageDialog('账号不可为空');
      return;
    }
    if (_password == '') {
      _showMessageDialog('密码不可为空');
      return;
    } else {
      _showMessageDialog('账号:' + _userID + '\n 密码:' + _password);
      return;
    }
  }

  void _showMessageDialog(String message) {
    showDialog(
      context: context,
      builder: (BuildContext context) {
        // return object of type Dialog
        return AlertDialog(
          title: new Text('提示'),
          content: new Text(message),
          actions: <Widget>[
            new FlatButton(
              child: new Text("ok"),
              onPressed: () {
                Navigator.of(context).pop();
              },
            ),
          ],
        );
      },
    );
  }

  Widget _showEmailInput() {
    return Padding(
      padding: const EdgeInsets.fromLTRB(15.0, 10.0, 0.0, 0.0),
      child: new TextFormField(
        maxLines: 1,
        obscureText: false, //是否是密码
        autofocus: false,
        style: TextStyle(
          fontSize: 15,
          color: Colors.grey[400],
        ),
        decoration: new InputDecoration(
            hintText: '请输入手机号',
            icon: ImageIcon(
              AssetImage('img/登录页账号.png'),
              color: Colors.grey[400],
            )),
        onSaved: (value) => _userID = value.trim(),
      ),
    );
  }

  Widget _showPasswordInput() {
    return Padding(
      padding: const EdgeInsets.fromLTRB(15.0, 10.0, 0.0, 0.0),
      child: new TextFormField(
        maxLines: 1,
        obscureText: true, //是否是密码
        autofocus: false,
        style: TextStyle(
          fontSize: 15,
          color: Colors.grey[400],
        ),
        decoration: new InputDecoration(
            hintText: '请输入登录密码',
            icon: ImageIcon(
              AssetImage('img/登录页密码.png'),
              color: Colors.grey[400],
            )),
        onSaved: (value) => _password = value.trim(),
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        body: ListView(
      children: <Widget>[
        Container(
          // height: 400,
          padding: const EdgeInsets.fromLTRB(0, 200, 0, 0),
          child: Image(
            image: AssetImage('img/登录页图标.png'),
            height: 70,
          ),
        ),
        Container(
          padding: const EdgeInsets.fromLTRB(45, 100, 55, 0),
          child: Text(
            '欢迎登录！',
            style: TextStyle(
              fontSize: 26,
              color: Colors.blueGrey,
            ),
          ),
        ),
        Form(
          key: _formKey,
          child: Container(
            height: 142,
            padding: const EdgeInsets.fromLTRB(45, 20, 55, 0),
            child: Column(
              children: <Widget>[
                _showEmailInput(),
                _showPasswordInput(),
              ],
            ),
          ),
        ),
        Container(
          height: 100,
          padding: const EdgeInsets.fromLTRB(55, 50, 55, 0),
          child: FlatButton(
            child: Text('登录', style: TextStyle(fontSize: 18)),
            textColor: Colors.white,
            color: Colors.blue,
            shape: RoundedRectangleBorder(
                borderRadius: BorderRadius.circular(8.0)),
            onPressed: () {
              _onLogin();
            },
          ),
        ),
      ],
    ));
  }
}
```

