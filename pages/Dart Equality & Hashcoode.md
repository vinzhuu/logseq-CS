tags:: [[Dart]]
---

- ## Identical()
	- 参考: [Dart API - identical function](https://api.dart.dev/dart-core/identical.html)
	- `dart:core` 库中的顶级函数: 检查两个对象引用是否指向同一对象.
		- 所有的对象都有一个 `identity` 用于区别于其他对象.
	- 对于 [[Dart Type - Number]] :
		- 如果两个 Integer 值相等, 则他们的引用指向的是同一对象.
		- 如果两个 Double 具有相同的二进制表示, 则他们的引用指向的是同一对象.
	- 对于 [[Dart Type - Record]] :
		- Record 没有一个持久的 `identity` , 因为编译器可能会将其组成部分拆分又重建.
		- 所以, 当两个 Record 的所有字段都相同时, 两个对象可能是同一个, 也可能不是.
	- ``` dart
	  var o = new Object();
	  var isIdentical = identical(o, new Object()); // false, different objects.
	  isIdentical = identical(o, o); // true, same object.
	  isIdentical = identical(const Object(), const Object()); // true, const canonicalizes.
	  isIdentical = identical([1], [1]); // false, different new objects.
	  isIdentical = identical(const [1], const [1]); // true.
	  isIdentical = identical(const [1], const [2]); // false.
	  isIdentical = identical(2, 1 + 1); // true, integers canonicalize.
	  
	  var pair = (1, "a"); // Create a record.
	  isIdentical = identical(pair, pair); // true or false, can be either.
	  
	  var pair2 = (1, "a"); // Create another(?) record.
	  isIdentical = identical(pair, pair2); // true or false, can be either.
	  
	  isIdentical = identical(pair, (2, "a")); // false, not identical values.
	  isIdentical = identical(pair, (1, "a", more: true)); // false, wrong shape.
	  ```
-
- 参考:
	- [Dart Docs - Implementing map keys](https://dart.dev/libraries/dart-core#implementing-map-keys)
	  logseq.order-list-type:: number
	- [Dart API - Object - operator == method](https://api.dart.dev/dart-core/Object/operator_equals.html)
	  logseq.order-list-type:: number
- ---
- ## `operator ==`
	- Object 中 `==` 的默认行为是, 比较两个对象是否是同一个.
	- 重写 `==` 方法, 必须满足如下 **等价关系 (equivalence relation)** :
		- 必须返回布尔值, 且不能抛出异常.
		  logseq.order-list-type:: number
		- 自反性 (Reflexive) : `o == o` 必须为 `true` .
		  logseq.order-list-type:: number
		- 对称型 (Symmetric) : `o1 == o2` 和 `o2 == o1` 必须结果一致.
		  logseq.order-list-type:: number
		- 传递性 (Transitive) : 如果 `o1 == o2` 和 `o2 == o3` 为 `true` , 则 `o1 == o3` 也为 `true` .
		  logseq.order-list-type:: number
- ## Hashcode
	-
- ## Overriding
	- `operator ==` 和 `hashCode()` , 要么都不重写, 要么要一起重写.
-