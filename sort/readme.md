# Содержание
[1. Сортировка пузырьком (Bubble sort)](#bubble)\
[2. Сортировка вставками (Insertion sort)](#insertion)\
[3. Сортировка выбором (Selection sort)](#selection)\
[4. Сортировка слиянием (Merge sort)](#merge)\
[5. Быстрая сортировка (Quick sort)](#quick)

<h1 id="bubble">1. Сортировка пузырьком (Bubble sort)</h1>

<p>
   <img src="/sort/src/Bubble-sort-example-300px.gif" width="600" height="300" /> 
</p>

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
<h1 id="insertion">2. Сортировка вставками (Insertion sort)</h1>

<p>
   <img src="/sort/src/insert.gif" width="600" height="300" /> 
</p>

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
<h1 id="selection">3. Сортировка выбором (Selection sort)</h1>

<p>
   <img src="/sort/src/selection.gif" width="600" height="300" /> 
</p>

Во всех случаях: Θ(𝑛^2)
```
private static void chooseSort(int[] arr) {
    int length = arr.length;
    for (int i = 0; i < length; ++i) {
        int idxMin = i;
        for (int j = i + 1; j < length; ++j) {
            if(arr[j] < arr[idxMin]){
                idxMin = j;
            }
        }
        int temp = arr[idxMin];
        arr[idxMin] = arr[i];
        arr[i] = temp;
    }
}
```
<h1 id="merge">4. Сортировка слиянием (Merge sort)</h1>

<p>
   <img src="/sort/src/merge.gif" width="600" height="300" /> 
</p>

Сложность алгоритма: O(n*log n)\
Затраты памяти: O(n)
```
private static void mergeSort(int[] arr) {
    if(arr != null && arr.length > 1){
        mergeSort(arr, arr.length);
    }
}

private static void mergeSort(int[] arr, int length) {
    if(length >= 2){
        int mid = length/2;
        int right = length - mid;
        int[] l = new int[mid];
        int[] r = new int[right];

        System.arraycopy(arr, 0, l, 0, mid);
        for (int i = mid; i < length; ++i) {
            r[i - mid] = arr[i];
        }
        mergeSort(l, mid);
        mergeSort(r, right);
        merge(arr, l, r , mid, right);
    }
}

private static void merge(int[] arr, int[] l, int[] r, int left, int right) {
    int i = 0, j = 0, k = 0;
    while(i < left && j < right){
        if(l[i] <= r[j]){
            arr[k++] = l[i++];
        }else{
            arr[k++] = r[j++];
        }
    }
    while(i < left){
        arr[k++] = l[i++];
    }
    while(j < right){
        arr[k++] = r[j++];
    }
}
```
<h1 id="quick">5. Быстрая сортировка (Quick sort)</h1>

<p>
   <img src="/sort/src/quick.gif" width="600" height="300" /> 
</p>

Худшее время: O(𝑛^2)\
Среднее время: O(n*log n)\
Лучшее время: O(n*log n)\
Затраты памяти: O(1) 
```
private static void quickSort(int[] arr, int low, int high) {
    if(low < high){
        int pivot = partition(arr, low, high);
        quickSort(arr, low, pivot - 1);
        quickSort(arr, pivot + 1, high);
    }
}

private static int partition(int[] arr, int low, int high) {
    int pivot = arr[high];
    int i = low;
    for (int j = low; j < high; ++j){
        if(arr[j] < pivot){
            swap(arr, i, j);
            ++i;
        }
    }
    swap(arr, i, high);
    return i;

}

private static void swap(int[] arr, int i, int j) {
    int temp = arr[i];
    arr[i] = arr[j];
    arr[j] = temp;
}
```



