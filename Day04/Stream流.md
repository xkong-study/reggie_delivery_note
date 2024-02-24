为什么js里面的数组过滤就是arr(i->i%2)不需要new list但是java的stream流就需要new list重新存进去?


在JavaScript中，数组的过滤可以使用数组的高阶函数 filter，它会返回一个新的数组，该数组包含满足条件的元素。在JavaScript中，这是一种方便的语法。

```code
let arr = [1, 2, 3, 4, 5];
let newArr = arr.filter(i => i % 2 === 0);
// newArr 是 [2, 4]
```

在这里，filter 方法会创建一个新的数组 newArr，其中包含原始数组 arr 中满足条件的元素。

而在Java中的 Stream 流，由于其惰性求值（Lazy Evaluation）的特性，对于中间操作（如 filter）的执行只是定义了一个操作步骤，不会立即执行。只有在终端操作（如 collect）触发时，才会执行中间操作并生成最终的结果。

```code
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);
List<Integer> newList = list.stream()
                            .filter(i -> i % 2 == 0)
                            .collect(Collectors.toList());
// newList 是 [2, 4]
```
在上述 Java 代码中，filter 方法是中间操作，返回的是一个 Stream，而不是一个新的 List。collect 是一个终端操作，用于将 Stream 转换为 List，这时才会真正执行中间操作。


为什么java的stream流是惰性求值特性?

避免过早计算： 如果流是及早求值的，那么在创建流时就会立即计算所有的中间操作，这可能导致不必要的开销。使用惰性求值，只有在需要结果时才进行计算，避免了过早的计算。

这种设计选择是为了在处理大数据集时提供更好的性能和更灵活的操作方式。通过延迟执行，Java 的 Stream 可以更高效地处理大规模的数据集，并且可以根据需要进行定制化的操作链。    



