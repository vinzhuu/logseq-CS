tags:: [[Dart]]
---

- ## Constructor Types
	- Constructor 有如下几种类型:
		- Generative constructors  生成式构造函数
		  logseq.order-list-type:: number
		- Default constructors  默认构造函数
		  logseq.order-list-type:: number
		- Named constructors  命名构造函数
		  logseq.order-list-type:: number
		- Factory constructors  工厂构造函数
		  logseq.order-list-type:: number
		- Redirecting constructor  重定向构造函数
		  logseq.order-list-type:: number
		- Constant constructors  常量构造函数
		  logseq.order-list-type:: number
- ## Generative constructors
	- 创建一个实例, 并初始化 instance variables .
		- 使用 `this.field` 给 instance variables 赋值, 不写方法体.
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
	- ==注意: 一个 Class 中只能写一个 Generative constructor , 否则会报错 ==
- ## Default constructors
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
- ## Named constructors
	- 可以自己定义 constructor 的名称.
		- 好处是, 可以让 constructor 更具语义, 可读性更高.
	- ``` dart
	  class Point {
	    final double x;
	    final double y;
	  
	    // Named constructor
	    Point.origin(double x, double y) : this.x = x, this.y = y;
	  }
	  
	  void main(List<String> args) {
	    var p = Point.origin(0, 0);
	    print('Point coordinates: (${p.x}, ${p.y})');
	  }
	  ```
- ## Factory constructors
	-
- ## Redirecting constructors
	-
- ## Constant constructors
	-
	-
- ## 参考
	- [Dart Docs - Constructors](https://dart.dev/language/constructors)
	  logseq.order-list-type:: number