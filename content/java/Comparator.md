# Comparator and Comparable
## Person class
Let's assume we have a sample class `Person` which have few properties and we want to sort collection of `Person` object.

```java
public class Person {
	private String name;
	private int age;

	public Person(String name, int age) {
		this.name = name;
		this.age = age;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	@Override
	public String toString() {
		return String.format("%10s - %d", this.getName(), this.getAge());
	}
}
```

- A `Comparator` type object is used wherever a comparison needed for ordering or sorting. We can pass an new object of `Comparator` with an implementation of `public int compare(T a, Tb)` method

```java
// using a Comparator type object, which implements compare method
Arrays.sort(persons, new Comparator<Person>() {			
	@Override
	public int compare (Person p, Person q) {
		return q.getAge() - p.getAge(); // sort by age descending
	}
});
```

- After Java 8, we can a Lambda expression for sorting an array.
````java
// or Lambda expression
Arrays.sort(persons, (Person a, Person b) -> b.getAge() - a.getAge());
```
