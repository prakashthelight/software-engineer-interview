# Java Collections

## ArrayList

## Set - HashSet, LinkedHashSet and TreeSet

Let's create a sample Student class to be used as type here

```java
class Student {

	private String name;
	private int age;

	public Student(String name, int age) {
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
		return String.format("%s - %d", this.getName(), this.getAge());
	}
}
```
`HashSet Example`

```java
	Set<Student> students = new HashSet<>();
	students.add(new Student("Prakash", 30));
	students.add(new Student("John", 17));
	students.add(new Student("Chelsea", 40));
	students.add(new Student("Mike", 24));
	students.add(new Student("Harvey", 19));

	for (Student student : students) {
		System.out.println(student);
	}
```
`Output` Order of items retrieved is not guaranteed
```output
Chelsea - 40
Harvey - 19
Prakash - 30
John - 17
Mike - 24
```
`LinkedHashSet Example`
```java
	Set<Student> students = new HashSet<>();
	students.add(new Student("Prakash", 30));
	students.add(new Student("John", 17));
	students.add(new Student("Chelsea", 40));
	students.add(new Student("Mike", 24));
	students.add(new Student("Harvey", 19));

	for (Student student : students) {
		System.out.println(student);
	}
```
`Output` Order of items retrieved is same as inserted
```output
Prakash - 30
John - 17
Chelsea - 40
Mike - 24
Harvey - 19
```
`TreeSet Example`
```java
	Set<Student> students = new TreeSet<>(new Comparator<Student>() {			
		@Override
		public int compare(Student a, Student b) {			
			return Integer.compare(b.getAge(), a.getAge());
		}
	});

	students.add(new Student("Prakash", 30));
	students.add(new Student("John", 17));
	students.add(new Student("Chelsea", 40));
	students.add(new Student("Mike", 24));
	students.add(new Student("Harvey", 19));

	for (Student student : students) {
		System.out.println(student);
	}
```
`Output` Order of items retrieved is sorted
```output
Chelsea - 40
Prakash - 30
Mike - 24
Harvey - 19
John - 17
```

## Map - HashMap, LinkedHashMap and TreeMap
