# Java Examples


## Number Parsing

```java
// throws java.lang.NumberFormatException for bad strings
int i = Integer.parseInt("12");
float f = Float.parseFloat("1.2");
long l = Long.parseLong("12000");
double d = Double.parseDouble("3.14");

// or with Objects instead of primitives (parsed the same):
Integer i = Integer.valueOf("42");
Float f = Float.valueOf("1.2");
Long l = Long.valueOf("1000");
Double d = Double.valueOf("3.14");
```
## Common String Operations

```java
// initializing
String s = "hello world"; // string literal
String s = String.valueOf(123);
String s = new String("hello"); // string parameter
String s = new String(new char[] {'h', 'e', 'l', 'l', 'o'}); // char array parameter

char c = s.charAt(index);
int res = s.compareTo("abd"); // == -1 (compare lexicographically; also: compareToIgnoreCase)

boolean b1 = s.contains("abc"); // true

boolean b2 = s.endsWith("efg"); // true
boolean b3 = s.equalsIgnoreCase("AbCDeFg"); // true
byte[] bytes = s.getBytes(); // {97, 98, 99} (array of 8-bit numbers [-128,127])
int i1 = s.indexOf('d'); // or with string "d"; can also use lastIndexOf()
int i2 = s.indexOf('f', startIndex);
boolean empty = s.isEmpty();
int len = s.length();
boolean b4 = s.matches("[a-z]*");
String s2 = s.replace('a', 'A');
String s3 = s.replace("ab", "AB");
String s4 = s.replaceAll("[a-z]", "x");
String[] arr = s.split("[0-9]"); // split around digits and remove them from output
boolean b5 = s.startsWith("abc"); // true
String sub = s.substring(startIncluding, endExcluding);

char[] chars = s.toCharArray();

String lower = s.toLowerCase(); // also: toUpperCase
String trimmed = s.trim(); // remove any leading/trailing whitespace
```

## Threads

```java
public static void main(String[] args) {
    Thread thread = new Thread(new MyRunnable());
    thread.start();
}

private static class MyRunnable implements Runnable {
    @Override
    public void run() {
        // ...
    }
}
```

## Threadpool (`ExecutorService`)

```java
import java.util.concurrent.*;

ExecutorService pool = Executors.newFixedThreadPool(4);
// or:
ExecutorService pool = new ThreadPoolExecutor(4, 4, 0L, TimeUnit.MILLISECONDS, new LinkedBlockingQueue<Runnable>());

pool.submit(new Runnable() {
    @Override
    public void run() {
      // ...
    }
});

// can also submit a Callable that returns a value (instead of Runnable's void):
Future<String> result = pool.submit(new Callable<String>() {
    @Override
    public String call() throws Exception {
        return null;
    }
});

result.get(); // blocking until the future completes
```



## Random

```java
Random rnd = new java.util.Random();
int i = rnd.nextInt(5); // exclusive of upper bound
```

## Inheritance

```java
interface Fruit {
  String name();
}

interface Serializable {
    String serialize();
}

interface MySerializable extends Serializable {}

class Orange implements Fruit, MySerializable {
    @Override
    public String name() {
        return null;
    }

    @Override
    public String serialize() {
        return null;
    }
}

// class and interface inheritance
class BaseFruit {
    // ...
}

class Apple extends BaseFruit implements Serializable {
    @Override
    public String serialize() {
        return null;
    }
}
```

## Try/Catch/Finally

```java
try {
    // ...
} catch (IllegalArgumentException | NullPointerException e) {
    // ...
} finally {
    // ...
}
```

## Enums

```java
public enum Color {
    Yellow,
    Green
}

public enum Size {
    Small(1),
    Medium(2),
    Large(2);

    private int size;

    private Size(int size) {
        this.size = size;
    }

    public int getSize() {
        return size;
    }
}
```

## Regex

```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

Pattern pattern = Pattern.compile("...");
Matcher matcher = pattern.matcher(input);

if (matcher.find()) {
    String firstGroup = matcher.group(0);
    // ...
} else {
    // no match found
}
```



## Generics

```java
// generic classes:
class FruitWriter<S, T extends Fruit & Serializable> {
    public FruitWriter(S s) {
        // ...
    }

    public String write(T t) {
        return t.name();
    }
}

// generic methods:
public <T, E> T foo(T t, E e) {
    return t;
}

// bounded wildcard:
interface HasWord {}
class Baz<T> {}
public void foo(Baz<? extends HasWord> bazWithWord) {
    // method foo only accepts types that extends HasWord
}
```

## Iterator

```java
interface Iterator<T> {
    boolean hasNext();
    T next();
    void remove();
}
```

## Iterable

```java
class MyList<T> implements Iterable<T> {

    public Iterator<T> iterator() {
        Iterator<T> it = new Iterator<T>() {
            public boolean hasNext() {
                // TODO: implement
            }

            public T next() {
                // TODO: implement
            }

            public void remove() {
                // TODO: implement
            }
        };

        return it;
    }
}
```

## Comparator

```java
import java.util.Comparator;
import java.util.Objects;

class IntegerComparator implements Comparator<Integer> {

    @Override
    public int compare(Integer o1, Integer o2) {
        if (o1 < o2) return -1;
        else if (Objects.equals(o1, o2)) return 0;
        else return 1;
    }
}
```

## Comparable

```java
class MyClass implements Comparable<MyClass> {

    @Override
    public int compareTo(MyClass o) {
        if (this < o) return -1;
        else if (this.equals(o)) return 0;
        else return 1;
    }
}
```

## Collections

- The following overview is *greatly simplified* and leaves out many details/interfaces/methods

```java
// Implementing this interface allows an object to be the target of the "foreach" statement
interface Iterable<E> {
    Iterator<E> iterator();
}

// The root interface in the collection hierarchy
interface Collection<E> extends Iterable<E> {
    // added in Collection only:
    int size();
    boolean isEmpty();
    boolean contains(Object o);
    boolean containsAll(Collection<?> c);
    Object[] toArray();
    <T> T[] toArray(T[] a);
    boolean add(E e);
    boolean addAll(Collection<? extends E> c);
    boolean remove(Object o);
    boolean removeAll(Collection<?> c);
    boolean retainAll(Collection<?> c);
    void clear();
}

interface List<E> extends Collection<E> {
    // added in List only:
    E get(int index);
    E set(int index, E element);
    void add(int index, E element);
    E remove(int index);
    int indexOf(Object o);
    int lastIndexOf(Object o);
    List<E> subList(int fromIndex, int toIndex);
}

class Stack<E> implements List<E> {
    E push(E item);
    E pop();
    E peek();
}

interface Queue<E> extends Collection<E> {
    boolean add(E e);
    boolean offer(E e);
    E remove();
    E poll();
    E element();
    E peek();
}

interface Set<E> extends Collection<E>

class ArrayList<E> implements List<E>
class LinkedList<E> implements List<E>, Queue<E>
class HashSet<E> implements Set<E>
class TreeSet<E> implements Set<E>
```

```java
interface Map<K, V> {
    int size();
    boolean isEmpty();
    boolean containsKey(Object key);
    boolean containsValue(Object value);
    V get(Object key);
    V put(K key, V value);
    V remove(Object key);
    void putAll(Map<? extends K, ? extends V> m);
    void clear();
    Set<K> keySet();
    Collection<V> values();
    Set<Map.Entry<K, V>> entrySet();
}

class HashMap<K,V> implements Map<K, V>
class TreeMap<K,V> implements Map<K, V>
```

## Instanceof

- A well-designed object-oriented program should almost *never* use `instanceof`

```java
public void doSomething(Object obj) {
    if (obj instanceof Foo) {
        Foo foo = (Foo) obj;
        // do something with foo
    } else if (obj instanceof Bar) {
        Bar bar = (Bar) obj;
        // do something with bar
    } else {
        // do something with obj
    }
}
```

## Varargs

- A shortcut to creating an array manually
- Inside method varargs parameter is seen as an array
- Varargs parameter must be the last one, and only one in a method signature

```java
public void foo(String... strings) {
    // strings is treated like an array here
}

// invocation:
foo();
foo("a");
foo("a", "b");
foo(new String[]{"a", "b"});
```

## Read/Write File

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;

Charset charset = Charset.forName("UTF-8")
Path path = Paths.get("/path/to/file");
```

**Read**

```java
try (BufferedReader reader = Files.newBufferedReader(file, charset)) {
    String line = null;
    while ((line = reader.readLine()) != null) {
        // process line
    }
} catch (IOException x) {
    // handle
}

// alternatively:
List<String> lines = Files.readAllLines(path, charset) // other overloads available
```

**Write**

```java
String s = ...;

try (BufferedWriter writer = Files.newBufferedWriter(file, charset)) {
    writer.write(s, 0, s.length());
} catch (IOException x) {
    System.err.format("IOException: %s%n", x);
}

// alternatively:
Files.write(path, lines, charset);
```

## Synchronized

```java
class MyClass {

    public synchronized void foo() {
        // synchronizes on the *instance* of the class
    }

    public synchronized void bar() {
        // also synchronizes on the *instance* of the class, sharing the same monitor with foo()
    }

    public void baz() {
        synchronized(this) {
            // same as bar/baz
        }
    }

    private final Object myLock = new Object();

    public void unrelated() {
        synchronized(myLock) {
            // ...
        }
    }
}
```

## Locks, Semaphores

**Lock**

```java
import java.util.concurrent.TimeUnit;
import java.util.concurrent.locks.Lock;
import java.util.concurrent.locks.ReentrantLock;

Lock lock = new ReentrantLock();
lock.lock(); // acquire the lock, block until acquired
boolean locked = lock.tryLock(); // acquire the lock if it's free
boolean locked = lock.tryLock(50, TimeUnit.MILLISECONDS); // acquire the lock if it's free within the given waiting time
lock.unlock(); // release lock, can only be done by thread that acquired lock
```

Other types of locks include `ReadWriteLock` and `StampedLock`.

**Semaphore**

```java
import java.util.concurrent.Semaphore;

Semaphore semaphore = new Semaphore(3); // initialize with 3 permits
semaphore.acquire(); // acquires a permit from this semaphore, blocking until one is available
boolean acquired = semaphore.tryAcquire(); // aquire a permit only if one is available
semaphore.release(); // release a permit, *no* requirement that releasing thead acquired a permit
```
