tags:: [[Dart]]
---

- ## Constructor Types
	- Constructor 有如下几种类型:
		- 普通构造函数
		  logseq.order-list-type:: number
			- Generative constructors  生成式构造函数
			  logseq.order-list-type:: number
			- Named constructors  命名构造函数
			  logseq.order-list-type:: number
		- Default constructors  默认构造函数
		  logseq.order-list-type:: number
		- 高级构造函数 (在 Generative constructors 或 Named constructors 的语法基础上, 加关键字)
		  logseq.order-list-type:: number
			- Constant constructors  常量构造函数
			  logseq.order-list-type:: number
			- Factory constructors  工厂构造函数
			  logseq.order-list-type:: number
- ## Generative constructors
	- ### Define Generative constructors
		- 创建一个实例, 并初始化 instance variables .
			- 不写方法体 (使用 `this.field` 给 instance variables 初始化)
			  logseq.order-list-type:: number
				- ``` dart
				  class Point {
				    double? x;
				    double? y;
				  
				    // 一个 Class 中只能写一个 Generative constructor 
				    Point(this.x);
				    Point(this.x, this.y);
				  }
				  
				  void main(List<String> args) {
				    var p = Point(2, 3);
				    print('Point coordinates: (${p.x}, ${p.y})');
				  }
				  ```
			- 写方法体
			  logseq.order-list-type:: number
				- ``` dart
				  class Point {
				    double? x;
				    double? y;
				  
				    // 一个 Class 中只能写一个 Generative constructor 
				    Point(double x) {
				      this.x = x;
				      this.y = 0;
				      print("declarative constructor");
				    }
				  
				    Point(double x, double y) {
				      this.x = x;
				      this.y = y;
				      print("declarative constructor 2");
				    }
				  }
				  
				  void main(List<String> args) {
				    var p = Point(2, 3);
				    print('Point coordinates: (${p.x}, ${p.y})');
				  }
				  ```
	- ### Use Generative constructors
		- 使用 `ClassName()` 或 `new ClassName()` 语法, 调用构造函数创建对象 (最好省略 `new` ) .
- ## Named constructors
	- ### Define Named constructors
		- 可以自己定义 constructor 的名称.
			- 好处是, 可以让 constructor 更具语义, 可读性更高.
		- ``` dart
		  class Point {
		    double? x;
		    double? y;
		  
		    // Named constructor
		    Point.origin(double x, double y) : this.x = x, this.y = y;
		  }
		  
		  void main(List<String> args) {
		    var p = Point.origin(0, 0);
		    print('Point coordinates: (${p.x}, ${p.y})');
		  }
		  ```
	- ### Use Named Constructors
		- 使用 `ClassName.constructorName()` 或 `new ClassName.constructorName()` 语法, 调用构造函数创建对象  (最好省略 `new` ) .
	- ### Redirecting constructors
		-
- ## Default constructors
	- ### Define Default constructors
		- 如果不显式声明 constructors , Dart 会使用 Default constructor .
		- 这个 Default constructor 等价于没有参数的 Generative constructors .
		- ``` dart
		  class Point {
		    double? x;
		    double? y;
		  
		    // Default constructor
		  }
		  
		  void main(List<String> args) {
		    var p = Point();
		    print('Point coordinates: (${p.x}, ${p.y})');
		  }
		  ```
	- ### Use Default constructors
		- 使用 `ClassName()` 或 `new ClassName()` 语法, 调用构造函数创建对象 (最好省略 `new` ) .
- ## Constant constructors
	- ### Define Constant constructors
		- 使用 **同一个类** 中的  Constant constructors 创建的对象是同一个 (不管用的是不是同一个 Constant constructor )
		- 关键字: 语法上, 就是在 Generative constructors 或 Named constructors 前加上关键字 `const` .
		- 要求: 所有 Instance variables 都是 `final` 类型.
		- ``` dart
		  class Point {
		    final double? x;
		    final double? y;
		  
		    Point(this.x, this.y);
		    const Point.build(this.x, this.y);
		    const Point.origin(this.x, this.y);
		  }
		  
		  void main(List<String> args) {
		    Point p1 = const Point.build(0.0, 0.0);
		    Point p2 = const Point.build(0.0, 0.0);
		    Point p3 = const Point.origin(0.0, 0.0);
		    Point p4 = const Point.origin(0.0, 0.0);
		    print(identical(p1, p2)); // true
		    print(identical(p1, p3)); // true
		    print(identical(p3, p4)); // true
		  
		    Point p5 = Point(0.0, 0.0);
		    Point p6 = Point(0.0, 0.0);
		    print(identical(p5, p6)); // false
		    print(identical(p5, p1)); // false
		  }
		  ```
	- ### Use Constant constructors
		- 使用 `const ClassName()` 或 `const ClassName.constructorName()` 语法
			- ``` dart
			  class Point {
			    final double? x;
			    final double? y;
			  
			    const Point(this.x, this.y);
			    const Point.build(this.x, this.y);
			  }
			  
			  void main(List<String> args) {
			    Point p1 = const Point(0.0, 0.0);
			    Point p2 = const Point.build(0.0, 0.0);
			    print(identical(p1, p2)); // true
			  }
			  ```
		- 若使用 `ClassName()` / `new ClassName()` 或 `ClassName.constructorName()` / `new ClassName.constructorName()` 语法, 调用 Constant constructors , 那效果与 Generative constructors 或 Named constructors 无异.
			- ``` dart
			  void main(List<String> args) {
			    Point p1 = Point(0.0, 0.0);
			    Point p2 = Point.build(0.0, 0.0);
			    print(identical(p1, p2)); // false
			  }
			  ```
		- 如果变量加了 `const` 关键字, 则可以省略调用 Constant constructor 需要用到的 `const` .
			- 因为 `const` 变量被赋的值必须是 `const` 值 (参见 [[Dart Syntax/Variables]]  `const` 相关部分)
			- ``` dart
			  void main(List<String> args) {
			    const Point p3 = Point(0.0, 0.0);
			    const Point p4 = Point.build(0.0, 0.0);
			    print(identical(p3, p4)); // true
			  
			    const pointAndLine1 = const {
			      'point': [const Point(0, 0)],
			      'line': [const Point(1, 10), const Point(-2, 11)],
			    };
			    const pointAndLine2 = {
			      'point': [Point(0, 0)],
			      'line': [Point(1, 10), Point(-2, 11)],
			    };
			    print(identical(pointAndLine1, pointAndLine2)); // true
			  }
			  ```
- ## Factory constructors
	- ### Define Factory constructors
		- 前面提到的 Generative constructors, Named Constructors, Constant constructors 都是不能写 `return` 语句的, 它们会自动创建一个对象并返回.
		- 而 Factory constructors 是不会自动创建对象的 (因此不能用 `this`), 需要开发者自己创建对象并返回.
		- ==语法上:==
			- 使用 `ClassName` 或 `ClassName.constructorName` 作为方法名.
			  logseq.order-list-type:: number
			- 使用 `factory` 修饰方法.
			  logseq.order-list-type:: number
			- 方法体内需要显式返回一个所属 class 的对象 (不能返回 null) .
			  logseq.order-list-type:: number
		- 获取实例时, 如果需要处理一些复杂的逻辑, 可以用 factory constructor .
			- 因为 factory constructor 可以灵活控制返回什么内容 (包括 `null` )
	- ### Factory constructor samples
		- Factory constructors 有如下几种经典使用场景:
		- #### 单例模式:
			- ``` dart
			  class Logger {
			    static Logger? _instance;
			  
			    factory Logger() {
			      if (_instance == null) {
			        _instance = Logger._internal();
			        return _instance!;
			      }
			      return _instance!;
			    }
			  
			    Logger._internal();
			  }
			  
			  void main(List<String> args) {
			    var logger1 = Logger();
			    var logger2 = Logger();
			    print(identical(logger1, logger2)); // true
			  }
			  
			  ```
		- #### 缓存对象
			- ``` dart
			  class User {
			    static final Map<int, User> _cache = {};
			  
			    final int id;
			    User._internal(this.id);
			  
			    factory User(int id) {
			      return _cache.putIfAbsent(id, () => User._internal(id));
			    }
			  }
			  
			  void main(List<String> args) {
			    var user1 = User(1);
			    var user2 = User(1);
			    var user3 = User(2);
			  
			    print(identical(user1, user2)); // true
			    print(identical(user1, user3)); // false
			  }
			  ```
		- #### 根据条件返回子类对象
			- ``` dart
			  abstract class Shape {
			    factory Shape(String type) {
			      if (type == 'circle') return Circle();
			      if (type == 'square') return Square();
			      throw ArgumentError('Unknown shape: $type');
			    }
			  }
			  
			  class Circle implements Shape {}
			  
			  class Square implements Shape {}
			  
			  void main(List<String> args) {
			    Shape shape1 = Shape('circle');
			    Shape shape2 = Shape('square');
			  
			    print(shape1.runtimeType); // Circle
			    print(shape2.runtimeType); // Square
			  }
			  ```
		- #### 复杂初始化
			- ``` dart
			  class Config {
			    final Map<String, dynamic> data;
			  
			    factory Config.load() {
			      var map = _loadConfigFromFile(); // 可能失败
			      return Config._internal(map ?? {});
			    }
			  
			    Config._internal(this.data);
			  }
			  ```
	- ### Use Factory constructors
		- 使用 `ClassName()` / `new ClassName()` 或 `ClassName.constructorName()` / `new ClassName.constructorName()` 语法, 调用构造函数创建对象  (最好省略 `new` ) .
- ## Constructor Name
	- Constructor 之间不能同名 (不管什么类型) , 所以 constructor 无法 **重载** .
		- 比如, 像这样会报错:
			- ``` dart
			  class Point {
			    final double? x;
			    final double? y;
			  
			    Point.origin(this.x, this.y);
			    const Point.origin(this.x);
			  }
			  ```
		- 这样也会报错:
			- ``` dart
			  class Point {
			    double? x;
			    double? y;
			  
			    Point(this.x);
			    Point(this.x, this.y);
			  }
			  ```
	- Constructor 可以和 Instance method 同名, 但不能和 Class method 同名 (因为都是通过 class 来调用的).
- ## Instance variable initialization
	- ### Instance variable initialization Types
		- Instance variable 的初始化有如下几种方式:
			- Initialize in the declaration (在声明时初始化)
			  logseq.order-list-type:: number
			- Use initializing formal parameters (使用初始化形参)
			  logseq.order-list-type:: number
			- Use an initializer list (使用初始化列表)
			  logseq.order-list-type:: number
	- ### Initialize in the declaration
		- 在声明时初始化
		- ``` dart
		  class Point {
		    double? x = 1.0;
		    double? y = 2.0;
		  
		    @override
		    String toString() {
		      return 'Point($x,$y)';
		    }
		  }
		  
		  void main(List<String> args) {
		    var p = Point();
		    print(p);
		  }
		  ```
	- ### Use initializing formal parameters
		-
- ## 参考
	- [Dart Docs - Constructors](https://dart.dev/language/constructors)
	  logseq.order-list-type:: number
	- [Dart Docs - Using constructors](https://dart.dev/language/classes#using-constructors)
	  logseq.order-list-type:: number
-