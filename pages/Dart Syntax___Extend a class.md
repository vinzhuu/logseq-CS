tags:: [[Dart]]
---

- ## Extend a class
	- 子类使用 `extend` 继承父类, 使用 `super` 引用父类.
	- ``` dart
	  class Television {
	    void turnOn() {
	      _illuminateDisplay();
	      _activateIrSensor();
	    }
	    // ···
	  }
	  
	  class SmartTelevision extends Television {
	    void turnOn() {
	      super.turnOn();
	      _bootNetworkInterface();
	      _initializeMemory();
	      _upgradeApps();
	    }
	    // ···
	  }
	  ```
- ## Overriding members
	- 子类可以重写 Instance Methods , 可以使用 `@override` 来表明是重写.
		- ``` dart
		  class Television {
		    // ···
		    set contrast(int value) {
		      // ···
		    }
		  }
		  
		  class SmartTelevision extends Television {
		    @override
		    set contrast(num value) {
		      // ···
		    }
		    // ···
		  }
		  ```
	- 子类中重写的方法, 有如下要求:
		- Return Type 
		  logseq.order-list-type:: number
			- 必须和父类一致, 或是其子类.
		- Parameter types
		  logseq.order-list-type:: number
			- 必须和父类一致, 或是其父类.
		- Positional parameters
		  logseq.order-list-type:: number
			- 数量必须和父类一致.
		- Generic methods
		  logseq.order-list-type:: number
			- 泛型方法, 不能重写非泛型方法.
			- 非泛型方法, 不能重写泛型方法.
		-
- ## Extend Constructors
	- 参见: [Named constructors](https://dart.dev/language/constructors#named-constructors)
	- 子类不会继承超类的 Named constructors .
	- 如果子类要使用 Named constructors , 需要子类自行实现.
-