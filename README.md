# Migrating from FluentAssertions to Shouldly

This document provides a mapping between FluentAssertions and Shouldly assertion methods. It also highlights key differences and considerations when migrating.

---

## 🔄 FluentAssertions to Shouldly Mapping

| **FluentAssertions** | **Shouldly** |
|----------------------|-------------|
| `result.Should().Be(expected);` | `result.ShouldBe(expected);` |
| `result.Should().NotBe(unexpected);` | `result.ShouldNotBe(unexpected);` |
| `result.Should().BeNull();` | `result.ShouldBeNull();` |
| `result.Should().NotBeNull();` | `result.ShouldNotBeNull();` |
| `result.Should().BeTrue();` | `result.ShouldBeTrue();` |
| `result.Should().BeFalse();` | `result.ShouldBeFalse();` |
| `result.Should().BeSameAs(expected);` | `result.ShouldBeSameAs(expected);` |
| `result.Should().NotBeSameAs(unexpected);` | `result.ShouldNotBeSameAs(unexpected);` |
| `result.Should().BeOfType<T>();` | `result.ShouldBeOfType<T>();` |
| `result.Should().NotBeOfType<T>();` | `result.ShouldNotBeOfType<T>();` |
| `result.Should().BeGreaterThan(value);` | `result.ShouldBeGreaterThan(value);` |
| `result.Should().BeGreaterThanOrEqualTo(value);` | `result.ShouldBeGreaterThanOrEqualTo(value);` |
| `result.Should().BeLessThan(value);` | `result.ShouldBeLessThan(value);` |
| `result.Should().BeLessThanOrEqualTo(value);` | `result.ShouldBeLessThanOrEqualTo(value);` |
| `result.Should().BePositive();` | `result.ShouldBePositive();` |
| `result.Should().BeNegative();` | `result.ShouldBeNegative();` |
| `result.Should().BeInRange(low, high);` | `result.ShouldBeInRange(low, high);` |
| `result.Should().NotBeInRange(low, high);` | `result.ShouldNotBeInRange(low, high);` |
| `collection.Should().Contain(item);` | `collection.ShouldContain(item);` |
| `collection.Should().NotContain(item);` | `collection.ShouldNotContain(item);` |
| `collection.Should().BeEmpty();` | `collection.ShouldBeEmpty();` |
| `collection.Should().NotBeEmpty();` | `collection.ShouldNotBeEmpty();` |
| `collection.Should().HaveCount(count);` | `collection.Count.ShouldBe(count);` |
| `collection.Should().HaveCountGreaterThan(value);` | `collection.Count.ShouldBeGreaterThan(value);` |
| `collection.Should().HaveCountLessThan(value);` | `collection.Count.ShouldBeLessThan(value);` |
| `collection.Should().AllBeAssignableTo<T>();` | `collection.ShouldAllBeAssignableTo<T>();` |
| `collection.Should().OnlyHaveUniqueItems();` | `collection.ShouldAllBeUnique();` |
| `dictionary.Should().ContainKey(key);` | `dictionary.ShouldContainKey(key);` |
| `dictionary.Should().NotContainKey(key);` | `dictionary.ShouldNotContainKey(key);` |
| `dictionary.Should().ContainValue(value);` | `dictionary.ShouldContainValue(value);` |
| `dictionary.Should().NotContainValue(value);` | `dictionary.ShouldNotContainValue(value);` |
| `action.Should().Throw<T>();` | `action.ShouldThrow<T>();` |
| `action.Should().NotThrow();` | `action.ShouldNotThrow();` |
| `action.Should().ThrowExactly<T>();` | `action.ShouldThrowExactly<T>();` |
| `action.Should().Throw().WithMessage("message");` | `action.ShouldThrow().Message.ShouldBe("message");` |

---

## 📌 FluentAssertions to Shouldly: Row-by-Row Examples

### ✅ `Be()` vs `ShouldBe()`

```csharp
// FluentAssertions
int result = 42;
result.Should().Be(42);

// Shouldly
int result = 42;
result.ShouldBe(42);
```

---

### ❌ `NotBe()` vs `ShouldNotBe()`

```csharp
// FluentAssertions
int result = 42;
result.Should().NotBe(0);

// Shouldly
int result = 42;
result.ShouldNotBe(0);
```

---

### 📌 `BeNull()` vs `ShouldBeNull()`

```csharp
// FluentAssertions
string? name = null;
name.Should().BeNull();

// Shouldly
string? name = null;
name.ShouldBeNull();
```

---

### 🔍 `NotBeNull()` vs `ShouldNotBeNull()`

```csharp
// FluentAssertions
string? name = "John";
name.Should().NotBeNull();

// Shouldly
string? name = "John";
name.ShouldNotBeNull();
```

---

### 🔄 `BeTrue()` vs `ShouldBeTrue()`

```csharp
// FluentAssertions
bool isValid = true;
isValid.Should().BeTrue();

// Shouldly
bool isValid = true;
isValid.ShouldBeTrue();
```

---

### 🚫 `BeFalse()` vs `ShouldBeFalse()`

```csharp
// FluentAssertions
bool isActive = false;
isActive.Should().BeFalse();

// Shouldly
bool isActive = false;
isActive.ShouldBeFalse();
```

---

### 🔗 `BeSameAs()` vs `ShouldBeSameAs()`

```csharp
// FluentAssertions
object obj = new();
object reference = obj;
reference.Should().BeSameAs(obj);

// Shouldly
object obj = new();
object reference = obj;
reference.ShouldBeSameAs(obj);
```

---

### ❌ `NotBeSameAs()` vs `ShouldNotBeSameAs()`

```csharp
// FluentAssertions
object obj1 = new();
object obj2 = new();
obj1.Should().NotBeSameAs(obj2);

// Shouldly
object obj1 = new();
object obj2 = new();
obj1.ShouldNotBeSameAs(obj2);
```

---

### 🔄 `BeOfType<T>()` vs `ShouldBeOfType<T>()`

```csharp
// FluentAssertions
object number = 42;
number.Should().BeOfType<int>();

// Shouldly
object number = 42;
number.ShouldBeOfType<int>();
```
---
### 🚫 `NotBeOfType<T>()` vs `ShouldNotBeOfType<T>()`

```csharp
// FluentAssertions
object value = "hello";
value.Should().NotBeOfType<int>();

// Shouldly
object value = "hello";
value.ShouldNotBeOfType<int>();
```

---

### 🔼 `BeGreaterThan()` vs `ShouldBeGreaterThan()`

```csharp
// FluentAssertions
int number = 10;
number.Should().BeGreaterThan(5);

// Shouldly
int number = 10;
number.ShouldBeGreaterThan(5);
```

---

### 🔼 `BeGreaterThanOrEqualTo()` vs `ShouldBeGreaterThanOrEqualTo()`

```csharp
// FluentAssertions
int number = 10;
number.Should().BeGreaterThanOrEqualTo(10);

// Shouldly
int number = 10;
number.ShouldBeGreaterThanOrEqualTo(10);
```

---

### 🔽 `BeLessThan()` vs `ShouldBeLessThan()`

```csharp
// FluentAssertions
int number = 10;
number.Should().BeLessThan(20);

// Shouldly
int number = 10;
number.ShouldBeLessThan(20);
```

---

### 🔽 `BeLessThanOrEqualTo()` vs `ShouldBeLessThanOrEqualTo()`

```csharp
// FluentAssertions
int number = 10;
number.Should().BeLessThanOrEqualTo(10);

// Shouldly
int number = 10;
number.ShouldBeLessThanOrEqualTo(10);
```

---

### ➕ `BePositive()` vs `ShouldBePositive()`

```csharp
// FluentAssertions
int number = 10;
number.Should().BePositive();

// Shouldly
int number = 10;
number.ShouldBePositive();
```

---

### ➖ `BeNegative()` vs `ShouldBeNegative()`

```csharp
// FluentAssertions
int number = -5;
number.Should().BeNegative();

// Shouldly
int number = -5;
number.ShouldBeNegative();
```

---

### 🎯 `BeInRange(low, high)` vs `ShouldBeInRange(low, high)`

```csharp
// FluentAssertions
int number = 15;
number.Should().BeInRange(10, 20);

// Shouldly
int number = 15;
number.ShouldBeInRange(10, 20);
```

---

### 🚫 `NotBeInRange(low, high)` vs `ShouldNotBeInRange(low, high)`

```csharp
// FluentAssertions
int number = 25;
number.Should().NotBeInRange(10, 20);

// Shouldly
int number = 25;
number.ShouldNotBeInRange(10, 20);
```

---

### 🔍 `Contain(item)` vs `ShouldContain(item)`

```csharp
// FluentAssertions
var numbers = new List<int> { 1, 2, 3 };
numbers.Should().Contain(2);

// Shouldly
var numbers = new List<int> { 1, 2, 3 };
numbers.ShouldContain(2);
```

---

### ❌ `NotContain(item)` vs `ShouldNotContain(item)`

```csharp
// FluentAssertions
var numbers = new List<int> { 1, 2, 3 };
numbers.Should().NotContain(4);

// Shouldly
var numbers = new List<int> { 1, 2, 3 };
numbers.ShouldNotContain(4);
```

---

### 📭 `BeEmpty()` vs `ShouldBeEmpty()`

```csharp
// FluentAssertions
var emptyList = new List<int>();
emptyList.Should().BeEmpty();

// Shouldly
var emptyList = new List<int>();
emptyList.ShouldBeEmpty();
```

---

### 📦 `NotBeEmpty()` vs `ShouldNotBeEmpty()`

```csharp
// FluentAssertions
var numbers = new List<int> { 1, 2, 3 };
numbers.Should().NotBeEmpty();

// Shouldly
var numbers = new List<int> { 1, 2, 3 };
numbers.ShouldNotBeEmpty();
```
---
### 🔢 `HaveCount(count)` vs `Count.ShouldBe(count)`

```csharp
// FluentAssertions
var numbers = new List<int> { 1, 2, 3 };
numbers.Should().HaveCount(3);

// Shouldly
var numbers = new List<int> { 1, 2, 3 };
numbers.Count.ShouldBe(3);
```

---

### 🔼 `HaveCountGreaterThan(value)` vs `Count.ShouldBeGreaterThan(value)`

```csharp
// FluentAssertions
var numbers = new List<int> { 1, 2, 3, 4 };
numbers.Should().HaveCountGreaterThan(3);

// Shouldly
var numbers = new List<int> { 1, 2, 3, 4 };
numbers.Count.ShouldBeGreaterThan(3);
```

---

### 🔽 `HaveCountLessThan(value)` vs `Count.ShouldBeLessThan(value)`

```csharp
// FluentAssertions
var numbers = new List<int> { 1, 2 };
numbers.Should().HaveCountLessThan(5);

// Shouldly
var numbers = new List<int> { 1, 2 };
numbers.Count.ShouldBeLessThan(5);
```

---

### 🏷️ `AllBeAssignableTo<T>()` vs `ShouldAllBeAssignableTo<T>()`

```csharp
// FluentAssertions
var items = new List<object> { "Hello", "World" };
items.Should().AllBeAssignableTo<string>();

// Shouldly
var items = new List<object> { "Hello", "World" };
items.ShouldAllBeAssignableTo<string>();
```

---

### 🔄 `OnlyHaveUniqueItems()` vs `ShouldAllBeUnique()`

```csharp
// FluentAssertions
var numbers = new List<int> { 1, 2, 3, 4 };
numbers.Should().OnlyHaveUniqueItems();

// Shouldly
var numbers = new List<int> { 1, 2, 3, 4 };
numbers.ShouldAllBeUnique();
```

---

### 🔑 `ContainKey(key)` vs `ShouldContainKey(key)`

```csharp
// FluentAssertions
var dictionary = new Dictionary<string, int> { { "age", 30 } };
dictionary.Should().ContainKey("age");

// Shouldly
var dictionary = new Dictionary<string, int> { { "age", 30 } };
dictionary.ShouldContainKey("age");
```

---

### 🚫 `NotContainKey(key)` vs `ShouldNotContainKey(key)`

```csharp
// FluentAssertions
var dictionary = new Dictionary<string, int>();
dictionary.Should().NotContainKey("name");

// Shouldly
var dictionary = new Dictionary<string, int>();
dictionary.ShouldNotContainKey("name");
```

---

### 📌 `ContainValue(value)` vs `ShouldContainValue(value)`

```csharp
// FluentAssertions
var dictionary = new Dictionary<string, int> { { "age", 30 } };
dictionary.Should().ContainValue(30);

// Shouldly
var dictionary = new Dictionary<string, int> { { "age", 30 } };
dictionary.ShouldContainValue(30);
```

---

### 🚫 `NotContainValue(value)` vs `ShouldNotContainValue(value)`

```csharp
// FluentAssertions
var dictionary = new Dictionary<string, int> { { "age", 30 } };
dictionary.Should().NotContainValue(25);

// Shouldly
var dictionary = new Dictionary<string, int> { { "age", 30 } };
dictionary.ShouldNotContainValue(25);
```

---

### ❗ `Throw<T>()` vs `ShouldThrow<T>()`

```csharp
// FluentAssertions
Action action = () => throw new InvalidOperationException();
action.Should().Throw<InvalidOperationException>();

// Shouldly
Action action = () => throw new InvalidOperationException();
action.ShouldThrow<InvalidOperationException>();
```

---

### ✅ `NotThrow()` vs `ShouldNotThrow()`

```csharp
// FluentAssertions
Action action = () => Console.WriteLine("Hello");
action.Should().NotThrow();

// Shouldly
Action action = () => Console.WriteLine("Hello");
action.ShouldNotThrow();
```

---

### ❗ `ThrowExactly<T>()` vs `ShouldThrowExactly<T>()`

```csharp
// FluentAssertions
Action action = () => throw new InvalidOperationException();
action.Should().ThrowExactly<InvalidOperationException>();

// Shouldly
Action action = () => throw new InvalidOperationException();
action.ShouldThrowExactly<InvalidOperationException>();
```

---

### 🎯 `Throw().WithMessage("message")` vs `ShouldThrow().Message.ShouldBe("message")`

```csharp
// FluentAssertions
Action action = () => throw new InvalidOperationException("Something went wrong");
action.Should().Throw<InvalidOperationException>()
    .WithMessage("Something went wrong");

// Shouldly
Action action = () => throw new InvalidOperationException("Something went wrong");
action.ShouldThrow<InvalidOperationException>().Message.ShouldBe("Something went wrong");
```
---

### 🔍 `IsEquivalentTo()` vs `ShouldDeepEqual()`

**Important:** `IsEquivalentTo()` from FluentAssertions should be replaced with `ShouldDeepEqual()` from the **DeepEqual** library for deeper object assertions.

```csharp
// FluentAssertions
var obj1 = new List<string>();

List<object> expected = [obj1,  3];
List<object> actual = [obj1 , 3];

actual.Should().BeEquivalentTo(expected);

// Shouldly (with DeepEqual)
actual.ShouldDeepEqual(expected);
```
---

### 🔍 `BeSubsetOf()` vs `ShouldBeSubsetOf()`

**Important:** use `ShouldBeSubsetOf()` to compare two collections without the need to compare the order of those items. 

```csharp
// FluentAssertions
List<int> expected = [1, 2, 3];
List<int> actual = [3, 2, 1];

actual.Should().BeSubsetOf(expected);

// Shouldly (with DeepEqual)
actual.ShouldBeSubsetOf(expected);
```


---

### 🔀 `ShouldSatisfyRespectively()` vs `ShouldSatisfyAllConditions()`

#### FluentAssertions:

```csharp
List<string> names = ["Peter", "Margot", "Hodor"];

names.ShouldSatisfyRespectively(
    peter => peter.Should().StartWith("P"),
    margot => margot.Should().Contain("got"),
    hodor => hodor.Length.Should().Be(5));
```

#### Shouldly:

```csharp
List<string> names = ["Peter", "Margot", "Hodor"];

names.ShouldSatisfyAllConditions(
    () => names[0].ShouldStartWith("P"),
    () => names[1].ShouldContain("got"),
    () => names[2].Length.ShouldBe(5));
```

---

### 📌 `AllSatisfy()` Migration

#### FluentAssertions:

```csharp
List<int> numbers = [10, 20, 30];

numbers.Should().AllSatisfy(result =>
{
    result.Should().BeGreaterThan(5);
});
```

#### Shouldly:

```csharp
List<int> numbers = [10, 20, 30];

foreach (var number in numbers)
{
    number.ShouldBeGreaterThan(5);
}
```

**Alternative:** If the collection is mutable, you can use `.ForEach()`:

```csharp
numbers.ForEach(number => number.ShouldBeGreaterThan(5));
```

---

## ℹ️ Additional Notes

- **Nullable vs Non-Nullable Comparisons:**  
  `ShouldBe()` does not allow comparisons between nullable and non-nullable types.

  ```csharp
  decimal? expected = 10m;
  decimal actual = 10m;

  // This will throw an error in Shouldly:
  actual.ShouldBe(expected); // ❌ Cannot compare nullable with non-nullable
  ```

- **For mutable collections, `.ForEach()` can be used instead of a `foreach` loop:**

  ```csharp
  List<int> items = [1, 2, 3];
  items.ForEach(i => i.ShouldBeGreaterThan(0));
  ```

---

This guide should help smoothly migrate from **FluentAssertions** to **Shouldly** while considering key differences. 🚀
