# C# Examples

## Arrays

```csharp
var a = new int[10];
var b = new int[] {1, 2, 3};
int[] c = {10, 20, 30};
```

## String
```csharp
var msg = "Hello World!";
var chars = msg.ToCharArray(); // to char array
var newMsg = new string(chars); // input char array
var firstChar = msg[0]; // character at index 0
```

## List
```csharp
var names = new List<string>();
names.Add("Tom");
names.Add("Peter");
names.Add("Mike");
names.Insert(0, "Alex");
names.Remove("Tom");
names.RemoveAt(1);

Console.WriteLine(names.Contains("Peter"));

foreach (var name in names)
{
	Console.WriteLine(name);
}

var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
for (var index = 0; index < salmons.Count; index++)  
{  
    Console.Write(salmons[index] + " ");  
}
```

## LinkedList
```csharp
var nodes = new LinkedList<string>();
nodes.AddLast("Tom");
nodes.AddFirst("Peter");
var peter = nodes.Find("Peter");
nodes.AddAfter(peter, "Mike");
nodes.AddBefore(peter, "Alex");

nodes.

Console.WriteLine(nodes.Contains("Tom")); // True
nodes.Remove("Tom");

// Output: Alex Peter Mike
foreach (var node in nodes)
{
	Console.Write(node + " ");
}
```

## IComparer

```csharp
class AgeComparer : IComparer<Employee>
{
	public int Compare(Employee e1, Employee e2)
	{
		return e1.Age - e2.Age;
	}
}
```


## HashSet

## SortedSet

## Dictionary

## SortedDictionary




## Stack

```csharp
var stack = new Stack<int>();
stack.Push(1);
stack.Push(2);
stack.Push(3);

Console.WriteLine(stack.Count); // size of stack - 3

stack.Push(4); // push at top
Console.WriteLine(stack.Peek()); // get top item - 4

stack.Pop(); // pop top item
Console.WriteLine(stack.Contains(2)); // True

```
