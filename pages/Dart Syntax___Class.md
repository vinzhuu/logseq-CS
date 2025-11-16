tags:: [[Dart]]
---

- ## Object-oriented
	- Dart 是一门 面向对象 (object-oriented) 的语言.
	- 每一个 `Object` 都是一个 `class` 的实例 (instance) .
- ## Class Members
	- `class` 有如下成员:
		- Methods
		  logseq.order-list-type:: number
			- Instance methods
			  logseq.order-list-type:: number
			- constructors
			  logseq.order-list-type:: number
		- data
		  logseq.order-list-type:: number
			- instance variables
			  logseq.order-list-type:: number
- ## Define a class
	- ### Instance variables
		- ``` dart
		  class Point {
		    double? x; // Declare instance variable x, initially null.
		    double? y; // Declare y, initially null.
		    double z = 0; // Declare z, initially 0.
		  }
		  ```
	- ### Instance methods
		-
- ## Create an object
	-
- ## Member access operators
	- 参考: [Other operators](https://dart.dev/language/operators#other-operators)
	- `.` : 成员访问 ( 对象不允许为 `null` )
	- `?.` : 条件成员访问 ( 对象允许为 `null` )
		- 如果对象为 `null` , 则表达式返回 `null` .
	- ``` dart
	  foo.bar;
	  foo?.bar;
	  
	  foo.bar();
	  foo?.bar();
	  ```
- ## Use an object's type
	- ### Get an object's type
		- 使用父类 `Object` 的 `runtimeType` 属性, 获取 一个 `Type` 类型的对象.
			- ``` dart
			  print('The type of a is ${a.runtimeType}');
			  ```
		- 不要使用 `runtimeType` 来比较对象的类型, 因为在运行时 `runtimeType` 可能会 **被裁剪或合并** .
		- 应使用下面的 **Type test operators** .
	- ### Type test operators
	  id:: 68ff7a45-d7e4-4ba1-9e8b-d109ae29b84c
		- 参考: [Type test operators](https://dart.dev/language/operators#type-test-operators)
		  id:: 6900bfad-e0d3-474f-a030-fe3ffa43d5f6
		- #### Type Check
			- `is` :
				- 若对象为 `null` , 则返回 `false` .
				  logseq.order-list-type:: number
				- 若对象不为 `null` :
				  logseq.order-list-type:: number
					- 属于指定 `type` , 则返回 `true` , 
					  logseq.order-list-type:: number
					- 不属于指定 `type` , 则返回 `false` ,
					  logseq.order-list-type:: number
			- `is!` :
				- 若对象为 `null` , 则返回 `true` .
				  logseq.order-list-type:: number
				- 若对象不为 `null` :
				  logseq.order-list-type:: number
					- 属于指定 `type` , 则返回 `false` ,
					  logseq.order-list-type:: number
					- 不属于指定 `type` , 则返回 `true` ,
					  logseq.order-list-type:: number
				- ``` dart
				  Object a = 1;
				  print(a is int); // true
				  print(a is Object); // true
				  
				  print(a is! int); // false
				  print(a is! String); // true
				  
				  int? b = null;
				  print(b is int); // false
				  print(b is! int); // true
				  ```
		- #### Typecast
			- `as` : 将对象强转为指定类型 (如果值为 `null` , 或者不是指定类型, 则会抛出异常).
				- ``` dart
				  (employee as Person).firstName = 'Bob';
				  ```
			- 或者, 也可以使用 `is` 来处理:
				- ``` dart
				  if (employee is Person) {
				    // 类型检查通过之后, 可以直接访问 Person 类型的属性
				    employee.firstName = 'Bob';
				  }
				  ```
- ## Callable objects
	- 参考: [Dart Docs - Callable objects](https://dart.dev/language/callable-objects)
	- 如果 `class` 定义了名称为 `call` 方法, 则可以直接使用该 `class` 的对象直接调用该方法.
	- ``` dart
	  class WannabeFunction {
	    String call(String a, String b, String c) => '$a $b $c!';
	  }
	  
	  void main() {
	    var wf = WannabeFunction();
	    // 直接使用 wf 对象调用 call 方法
	    print(wf('Hi', 'there,', 'gang'));
	    // 使用 wf.call() 调用 call 方法
	    print(wf.call('Hi', 'there,', 'gang'));
	  }
	  ```
- ## 参考
	- [Dart Docs - Classes](https://dart.dev/language/classes)
	  logseq.order-list-type:: number