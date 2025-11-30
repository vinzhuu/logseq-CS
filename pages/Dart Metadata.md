tags:: [[Dart]]
---

- ## Syntax
	- `Metadata` 就是给代码提供额外的 **静态信息 (static information)** 的语法.
	- 语法: `@` 后跟一个 运行时常量 (compile-time constant) , 或者是 一个 constant constructor .
- ## Built-in annotations
	- ### @Deprecated
		- 参考: [Dart API - Deprecated](https://api.dart.dev/dart-core/Deprecated-class.html)
		- #### Using @Deprecated
			- 作用:
				- 用于将某个 `feature` 标记为: "之后的版本弃用" .
				- `feature` 可以是 API 的任何组成部分: 可以是整个库, 也可以是某个参数.
			- Deprecated Superclass :
				- 如果父类中的某个 `feature` 被标记为已弃用, 子类不会继承这个状态.
			- message 最佳实践:
				- 在 `message` 中说明 **替代方案** 和 **可能被移除的日期/版本** .
			- ``` dart
			  class Television {
			    /// Use [turnOn] to turn the power on instead.
			    @Deprecated('Use turnOn instead')
			    void activate() {
			      turnOn();
			    }
			  
			    /// Turns the TV's power on.
			    void turnOn() {
			      // ···
			    }
			    // ···
			  }
			  ```
		- #### @deprecated (不推荐使用)
			- `deprecated` 是 Dart 内置库 `annotations.dart` 中的一个常量.
			- ``` dart
			  const Deprecated deprecated = Deprecated("next release");
			  ```
		- #### Deprecated 的构造方法
			- `@Deprecated.extend()` : 弃用 `extend` 该类.
			- `@Deprecated.implement()` : 弃用 `implement` 或 `mixin` 该类.
			- `@Deprecated.subclass()` : 弃用 `extend`, `implement` 或 `mixin` 该类.
			- `@Deprecated.mixin()` : 弃用 `mixin` 该类.
			- `@Deprecated.instantiate()` ：弃用 **实例化** 该类。
			- `@Deprecated.optional()` ：弃用 **参数的可选性** (即之后可能改为必填)
	- ### @override
		- 将 Instance Members 标记为对 **superclass** 或 **interface** 中同名成员的 **override** 或 **implement** .
		- 具体参见: [[Dart Syntax/Extend a class]]
	-
- ## Analyzer-supported annotations
- ## Custom annotations
	- ``` dart
	  class Todo {
	    final String who;
	    final String what;
	  
	    const Todo(this.who, this.what);
	  }
	  
	  @Todo('Dash', 'Implement this function')
	  void doSomething() {
	    print('Do something');
	  }
	  ```
- ## package:meta
	- 使用 `@Target` 指定注解可以使用的地方.
		- 参见: [package:meta](https://pub.dev/packages/meta)
	- ``` dart
	  import 'package:meta/meta_meta.dart';
	  
	  @Target({TargetKind.function, TargetKind.method})
	  class Todo {
	    // ···
	  }
	  ```
- ## 参考
	- [Dart Docs - Metadata](https://dart.dev/language/metadata)
	  logseq.order-list-type:: number
-