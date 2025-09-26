<details>
  <summary> <h2>Binary Search with Loops</h2> </summary>

```java
public static boolean binary_search(int arr[], int target) {
        int i = 0;
        int j = arr.length - 1;
        while (i <= j) {
            int mid = i + (j - i) / 2;
            if (arr[mid] == target)
                return true;
            else if (arr[mid] < target)
                i = mid + 1;
            else
                j = mid - 1;
        }

        return false;
    }
```
</details>

<details>
  <summary> <h2>Binary Search using Recursion </h2> </summary>

```java
 public static int binarySearch(int[] arr, int low, int high, int key) {
        if (low <= high) {
            int mid = low + (high - low) / 2;

            if (arr[mid] == key) return mid;

            if (arr[mid] > key) 
                return binarySearch(arr, low, mid - 1, key);

            return binarySearch(arr, mid + 1, high, key);
        }
        return -1;
    }
    }
```
</details>



<details>
  <summary> <h2> Selection Sort </h2> </summary>

```java
   // suppose first elm is minm and compare with all find new min and swap them
    public static void selectionSort(int arr[]) {
        for (int i = 0; i < arr.length - 1; i++) {

            int min_idx = i;
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[min_idx] > arr[j]) {
                    min_idx = j;
                }
            }

            int temp = arr[i];
            arr[i] = arr[min_idx];
            arr[min_idx] = temp;

        }
        System.out.println(Arrays.toString(arr));
    }
```
</details>   




<details>
  <summary> <h2> Insertion Sort </h2> </summary>

```java
 
    // key ki psn find krenge prvs array me [prvs | next ]
    public static void insertion(int arr[]) {
        for (int i = 1; i < arr.length; i++) {
            int key = arr[i];
            int j = i - 1;
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j--;
            }
            arr[j + 1] = key;
        }

        System.out.println(Arrays.toString(arr));
    }
```    
</details>


<details>
  <summary> <h2> Bubble Sort </h2> </summary>

```java
 
 // biggest or smallest nikal kr ayega last me
    public static void bubble(int arr[]) {
        for (int i = 0; i < arr.length - 1; i++) {
            for (int j = 0; j < arr.length - 1 - i; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }

        System.out.println(Arrays.toString(arr));
    }
    
</details> 
