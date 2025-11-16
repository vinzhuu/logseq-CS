tags:: [[Dart]]
---

- ## Object-oriented
	- Dart 是一门 面向对象 (object-oriented) 的语言.
	- 每一个 `Object` 都是一个 `class` 的实例 (instance) .
- ## Class Members
	- `class` 有如下成员:
		- Variables
		  logseq.order-list-type:: number
			- Instance variables
			  logseq.order-list-type:: number
			- Class variables (Static variables)
			  logseq.order-list-type:: number
		- Methods
		  logseq.order-list-type:: number
			- Instance methods
			  logseq.order-list-type:: number
			- 特殊的 Instance methods
			  logseq.order-list-type:: number
				- Operators (可以给 class 自定义运算符的实现)
				  logseq.order-list-type:: number
				- Getters & Setters
				  logseq.order-list-type:: number
			- Class methods (Static methods)
			  logseq.order-list-type:: number
		- Constructors
		  logseq.order-list-type:: number
- ## Variables
	- 通读: [[Dart Syntax/Variable Members]]
- ## Methods
	- 通读: [[Dart Syntax/Method Members]]
- ## Constructors
	- 通读: [[Dart Syntax/Constructor]]
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
- ## 参考
	- [Dart Docs - Classes](https://dart.dev/language/classes)
	  logseq.order-list-type:: number
	-
	-