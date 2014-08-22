# Functional style Programming with java

1. very highly expressive

imperative style - how to do it
```java
// mutability
for (int i = 2; i < number; i++) {
  if (number % i == 0) return false;
}

return number > 1;
```

functional style - what to do it
Declarative
```java
// immutability
IntStream.range(2, number)
	.nonMatch(index -> number % index == 0);
```
```java
// immutability
Predicate<Integer> isDivisible = divisor -> number % divisor == 0;
IntStream.range(2, number)
	.nonMatch(index -> isDivisible(index));
```

ex) find the double of the first even number greater than 3
```java
List<Integer> values = Arrays.asList(1, 2, 3, 5, 4, 6, 7, 9, 10);
int result = 0;
for (int e : values) {
    if (e > 3 && e % 2 == 0) {
	    result = e * 2;
		break;
	}
}

values.stream()
	.filter(e -> e > 3)
	.filter(e -> e % 2 == 0)
	.map(e -> e * 2)
	.findFirst()
	.get(); // Optional because It's possible not present

// more expressive and more readable
// Lazy & Composition
// lazy until meet terminal operation
values.stream()
	.filter(::isGreaterThan3) // intellij recommand method reference
	.filter(::isEven)
	.map(doubleIt)
	.findFirst()
	.get();
```
```java
public static int totalValue(List<Integer> numbers, Selector selector) {
	int result = 0;
	for (int e : numbers) {
		if (selector.test(e)) result += 0;
	}

	return result;
}

return numbers.stream()
	.filter(selector)
	.reduce(0, Math:addExact);
```
```java
numbers.stream()
	.mapToInt(::doubleIt)
	.sum();

	// doubleIt : pure function
	// reference transparency

number.parallelStream()
	.mapToInt(::doubleIt)
	.sum();
```