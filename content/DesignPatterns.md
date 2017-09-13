# Design Patterns

## Creational Design Patterns

### Singleton

```java
public class SingletonLogger {

	private static final Object lock = new Object();
	private static SingletonLogger instance;

	private SingletonLogger() {
	}

	public static SingletonLogger getInstance() {
		synchronized (lock) {
			if (instance == null) {
				instance = new SingletonLogger();
			}
		}

		return instance;
	}

	public void log (String str) {
		System.out.println(str);
	}
}
```
### Factory
### Abstract Factory
### Builder
### Prototype

## Structural Design Patterns

### Adapter
### Bridge
### Composite
### Decorator
### Facade
### Flyweight
### Proxy
### MVC

## Behavioral Design Patterns
### Observer
### State
### Strategy
### Template
### Visitor
### Command
### Iterator
