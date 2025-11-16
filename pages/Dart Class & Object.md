tags:: [[Dart]]
---

- ## 学习路线
	- Dart 的继承机制, 基于 `class` 和 `mixin` :
	- [[Dart Type Overview]]
	  logseq.order-list-type:: number
	- [[Dart Type Alias]]
	  logseq.order-list-type:: number
	- [[Dart Syntax/Class]]
	  logseq.order-list-type:: number
		- [[Dart Syntax/Variable Members]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Constructor]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Method Members]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Object's Type]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Callable Object]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Abstract Class]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Extend a class]]
		  logseq.order-list-type:: number
	- [[Dart Syntax/Mixin]]
	  logseq.order-list-type:: number
	- [[Dart Syntax/Extension Method]]
	  logseq.order-list-type:: number
-
- 标识符以 `_` 开头的成员, 是 `private` 的.
- ## Cascade notation
	- 参考: [Cascade notation](https://dart.dev/language/operators#cascade-notation)
	- 可以在对象后面接 **级联符号** `..` , 用来连续多次访问这个对象的属性和方法.
		- 在这过程中的返回值会被忽略, 最终返回这个对象本身.
		- ``` dart
		  StringBuffer sb = StringBuffer();
		  print(
		    sb
		    ..write('foo')
		    ..write('bar'),
		  ); // foobar
		  ```
	- 如果对象可能为 `null` , 可以将第一个使用 `..` 改为 `?..` .
		- 使用 `?..` 的效果是: 如果对象是 `null` , 则后续所有的级联操作都不会执行, 并最终返回 `null` (也即这个对象本身).
		- ``` dart
		  StringBuffer? sb = StringBuffer();
		  sb = null;
		  print(
		    sb
		    ?..write('foo')
		    ..write('bar'),
		  ); // null
		  ```