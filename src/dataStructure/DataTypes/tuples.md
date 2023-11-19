# tuples

```ts
// 💡 Note: JS does not have Tuples.... TS have typed Arrays.
//    example

const typedList: readonly [number, boolean, string] = [5, true, "Elie"];
// making a typed list readonly is a good practice.
```

```go
// 💡 There is no Tuple in GO. don't confuse two return value with tuple it is noe

func returnSomething() (int,string){ // (int ,string) not a tuple
    return 53 , "Elie"
}
```

- Python List vs Tuple
  - You can think of Tuple like immutable Typed list
  - Tuples can be defined using ().
    ```python
        myTuple = (1 , 'Banana', 4)
    ```
  - Tuples are commonly used where you want a fixed-size ordered collection.
