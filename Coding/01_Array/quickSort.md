## 复杂度

1. 时间复杂度 $O(NlogN)$
	1. 最好 $O(NlogN)$
	2. 最坏 $O(N^2)$
2. 空间复杂度 $O(logN)$

## 步骤

1. 从数列中挑出一个元素，称为 "基准"（pivot）
2. 重新排序数列，所有元素比基准值小的摆放在基准左边，比基准值大（等于）的元素摆在基准的右边。在这个分区退出之后，该基准就处于数列的中间位置。这个称为分区（partition）操作
3. 递归地（recursive）把小于基准值元素的子数列和大于基准值元素的子数列排序

## 代码

``` java
private static void quickSort0(int[] array, int low, int high) {  
    if (low >= high) return;  
    int i = low, j = high, index = array[i]; // 取最左边的数作为基准数  
    while (i < j) {  
        // 从右向左 找第一个小于index的数/交换  
        while (i < j && array[j] >= index) {  
            j--;  
        }  
        if (i < j) {  
            array[i++] = array[j];  
        }  
        // 从左向右 找第一个大于index的数/交换  
        while (i < j && array[i] < index) {  
            i++;  
        }  
        if (i < j) {  
            array[j--] = array[i];  
        }  
    }  
    array[i] = index; // 将基准数填入最后的坑  
    quickSort(array, low, i - 1);  
    quickSort(array, i + 1, high);  
}
```