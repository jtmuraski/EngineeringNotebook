Yield is a keyword used in iterator blocks to provide the next value or signal the end of an iteration. Can come in two forms: ```yield return``` and ```yield break```

Microsoft Doc: [yield statement - provide the next element in an iterator | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/yield)
yield return example:
```
// return every even number in the iteration
IEnumberable<int> ProduceEvenNumber(int upto)
{
	for(int i = 0; i < upto; i += 2)
	{
		yield return i;
	}
}
```

Calling a yielded iterator example:
```
var numbers = ProduceEvenNumbers(5); 
Console.WriteLine("Caller: about to iterate."); 
foreach (int i in numbers) 
{ 
	Console.WriteLine($"Caller: {i}"); 
} 

IEnumerable<int> ProduceEvenNumbers(int upto) 
{ 
	Console.WriteLine("Iterator: start."); 
	for (int i = 0; i <= upto; i += 2) 
	{ 
		Console.WriteLine($"Iterator: about to yield {i}"); 
		yield return i; 
		Console.WriteLine($"Iterator: yielded {i}"); 
	} 
	Console.WriteLine("Iterator: end."); 
} 
	
	// Output: 
	// Caller: about to iterate. 
	// Iterator: start. 
	// Iterator: about to yield 0 
	// Caller: 0 
	// Iterator: yielded 0 
	// Iterator: about to yield 2 
	// Caller: 2 
	// Iterator: yielded 2 
	// Iterator: about to yield 4 
	// Caller: 4 
	// Iterator: yielded 4 
	// Iterator: end.
```
Notice that when the ProduceEvennumbers function is called to assign it to ```var numbers``` it doesn't actually run until ```numbers``` is used! it then returns the value i one at a time as it iterates through.