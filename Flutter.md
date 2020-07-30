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

class BottomNavigationWidget extends StatefulWidget {     //快速构建 stful
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



## 要实现的UI页面

#### 底部标签   

https://github.com/LiuC520/flutter_bottom_tab_bar



