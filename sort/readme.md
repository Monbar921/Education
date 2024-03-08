<h1>Сортировка пузырьком (Bubble sort)</h1>

![Example GIF](/src/Bubble-sort-example-300px.gif)

Худшее время: O(𝑛^2)\
Среднее время: O(𝑛^2)\
Лучшее время: O(n)\
Затраты памяти: O(n)
```
private static void bubbleSort(int[] arr) {
    int length = arr.length;
    for (int i = 0; i < length; ++i) {
        for (int j = 0; j < length - i - 1; ++j) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
```
<h1>Сортировка вставками (Insertion sort)</h1>

![Example GIF](/src/insert.gif)

Худшее время: O(𝑛^2)/
Среднее время: O(𝑛^2)\
Лучшее время: O(n)\
Затраты памяти: O(n)
```
private static void insertionSort(int[] arr) {
    int length = arr.length;
    for (int i = 0; i < length; ++i) {
        int j = i;
        int temp = arr[i];
        while (j > 0 && temp < arr[j - 1]){
            arr[j] = arr[j - 1];
            --j;
        }
        arr[j] = temp;
    }
}
```
<h1>Сортировка выбором (Selection sort)</h1>

<p>
   <img src="/sort/src/selection.gif" width="220" height="240" /> 
</p>

[//]: # (<img src="src/selection.gif" alt="Example GIF" width="200" height="150">)

Во всех случаях: Θ(𝑛^2)
