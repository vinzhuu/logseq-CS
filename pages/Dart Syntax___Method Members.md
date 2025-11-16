tags:: [[Dart]]
---

- ## Instance methods
	- 即, 不用 `static` 修饰的成员方法.
	- Instance methods 可以访问 Instance variables .
	- ``` dart
	  import 'dart:math';
	  
	  class Point {
	    final double x;
	    final double y;
	  
	    // Sets the x and y instance variables
	    // before the constructor body runs.
	    Point(this.x, this.y);
	  
	    double distanceTo(Point other) {
	      var dx = x - other.x;
	      var dy = y - other.y;
	      return sqrt(dx * dx + dy * dy);
	    }
	  }
	  ```
- ## Operator Instance Methods
	- 大部分 **运算符** 其实是具有特殊名称的 Instance Method .
	- 有且仅有如下运算符, 可以作为 Instance Method :
		- `<` , `>` , `<=` , `>=` , `==` 
		  logseq.order-list-type:: number
		- `-` , `+` ,  `/` , `~/` , `*` , `%` 
		  logseq.order-list-type:: number
		- `~` , `|` , `^` , `&`
		  logseq.order-list-type:: number
		- `<<` , `>>>` , `>>` 
		  logseq.order-list-type:: number
		- `[]=` , `[]`
		  logseq.order-list-type:: number
	- 使用 `operator` 关键字声明 Operator Instance Methods .
		- ``` dart
		  class Vector {
		    final int x, y;
		  
		    Vector(this.x, this.y);
		  
		    Vector operator +(Vector v) => Vector(x + v.x, y + v.y);
		    Vector operator -(Vector v) => Vector(x - v.x, y - v.y);
		  
		    @override
		    bool operator ==(Object other) =>
		        other is Vector && x == other.x && y == other.y;
		  
		    @override
		    int get hashCode => Object.hash(x, y);
		  }
		  
		  void main() {
		    final v = Vector(2, 3);
		    final w = Vector(2, 2);
		  
		    assert(v + w == Vector(4, 5));
		    assert(v - w == Vector(0, 1));
		  }
		  ```
	- 使用 Operator 的时候, 执行的是运算符左边对象的 Operator Instance Method
- ## Getters & Setters
	- ### What is  Getter & Setter
		- Getter 与 Setter 是用于读写对象 **属性** 的特殊方法.
		- 不是用 `obj.getXxx()` 来获取这个变量, 而是使用 `obj.field` .
			- `obj.field` 的值, 就是 `field` 属性的 `Getter` 方法返回的值 (除非后面给 `field` 另外赋了值).
		- 不是用 `obj.setXxx(value)` 来给这个变量赋值, 而是使用 `obj.field = value` .
			- 不管 `field` 属性的 `Setter` 方法内部做了什么,  `field` 被赋的值都是 `value` .
	- ### Implicit Getter & Setter
		- 所有的 Instance variables 都会生成隐式的 `Getter` Method .
		- 所有的 Non-fina Instance variables 和 `late final` Instance variables 都会生成隐式的 `Setter` Method .
			- 所有 非 `late` 的 `final` 变量, 需要在实例化时赋值, 后续用不到 `Setter` 方法
		- ``` dart
		  class Point {
		    double? x; // Declare instance variable x, initially null.
		    double? y; // Declare y, initially null.
		  }
		  
		  void main() {
		    var point = Point();
		    point.x = 4; // Use the setter method for x.
		    assert(point.x == 4); // Use the getter method for x.
		    assert(point.y == null); // Values default to null.
		  }
		  ```
	- ### Explicit Getter & Setter
		- 可以使用 `get` 和  `set` 显式声明 Getter & Setter .
			- 显式声明 Getter & Setter 的同时, 也是在声明同名变量, 所以不用另外再声明同名变量.
		- ``` dart
		  /// A rectangle in a screen coordinate system,
		  /// where the origin `(0, 0)` is in the top-left corner.
		  class Rectangle {
		    double left, top, width, height;
		  
		    Rectangle(this.left, this.top, this.width, this.height);
		  
		    // Define two calculated properties: right and bottom.
		    double get right => left + width;
		    set right(double value) => left = value - width;
		    double get bottom => top + height;
		    set bottom(double value) => top = value - height;
		  }
		  
		  void main() {
		    var rect = Rectangle(3, 4, 20, 15);
		    print(rect.left); // 3.0
		    print(rect.right); // 23.0
		  
		    rect.right = 12;
		    print(rect.left); // -8.0
		    print(rect.right); // 12.0
		  }
		  ```
	- ### Operators & Getter/Setter
		- 对 Class 中的属性执行 `++` , `+=` 这类会改变属性本身的值的运算符时.
		- Dart 会进行如下处理:
			- 先调用 getter 一次，获取值.
			  logseq.order-list-type:: number
			- 把值存到临时变量上, 进行运算
			  logseq.order-list-type:: number
			- 调用 setter 将值写会.
			  logseq.order-list-type:: number
		- Dart 会保证 Getter 和 Setter 分别 **只调用一次** , 避免产生副作用.
- ## Abstract methods
	- 如下方法可以被定义为 Abstract Method .
		- Instance Method
		  logseq.order-list-type:: number
		- Operator Instance Method
		  logseq.order-list-type:: number
		- Getter & Setter
		  logseq.order-list-type:: number
	- Abstract Method 只能存在于 [[Dart Syntax/Abstract Class]] 和 [[Dart Syntax/Mixin]] 中 .
	- 声明 Abstract Method 时, 方法 **无需 (且不能)** 使用 `abstract` 关键字修饰, 只要不写方法体就行.
		- ``` dart
		  abstract class Doer {
		    // Define instance variables and methods...
		  
		    void doSomething(); // Define an abstract method.
		  }
		  
		  class EffectiveDoer extends Doer {
		    void doSomething() {
		      // Provide an implementation, so the method is not abstract here...
		    }
		  }
		  ```
- ## 参考
	- [Dart Docs - Classes](https://dart.dev/language/classes)
	  logseq.order-list-type:: number
	- [Dart Docs - Methods](https://dart.dev/language/methods)
	  logseq.order-list-type:: number
	-