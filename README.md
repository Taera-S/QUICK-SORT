# Quicksort
QuickSort is based on the Divide and Conquer strategy. It selects a pivot element and partitions the specified array around that pivot. QuickSort comes in a variety of flavors, each of which selects pivot in a unique way.

* Always choose the first element as the pivot.
* Always choose the last element as the pivot. 
* As the pivot, choose an element at random.
* As the pivot, use the median.

Partitioning is the most important operation in quickSort. Given an array and a pivot element x, the goal of partitioning is to place x in the correct position in the sorted array, with all smaller elements (less than x) placed before x and all larger elements (greater than x) placed after x. All of this should be completed in a linear manner.

## Algorithm’s Of QuickSort

* In the array, look for a "pivot" entry. For a single round, this object serves as the comparison point.
* Begin with the first item in the array (the left pointer).
* Begin a pointer (the right pointer) at the array's final item.
* Move the left pointer to the right when the value at the left pointer in the array is smaller than the pivot value (add 1). Continue until the pivot value is larger than or equal to the value at the left pointer.
* Move the right pointer to the left when the value at the right pointer in the array is larger than the pivot value (subtract 1). Continue until the pivot value is less than or equal to the value at the right pointer.
* Swap the values at these points in the array if the left pointer is less than or equal to the right pointer.
* Move the left pointer one space to the right and the right pointer one space to the left.
* Swap the values at these points in the table if the left pointer is less than or equal to the right pointer.<br />

## Example Of QuickSort

Unsorted Elements.<br />
<img width="510" alt="Picture1" src="https://user-images.githubusercontent.com/95191692/145232797-b5d4659e-24a7-4e1c-ac43-98b08f4a4cad.png">
<br />
<br />
Choose a pivot element.<br />
<img width="545" alt="Picture2" src="https://user-images.githubusercontent.com/95191692/145233066-d1d31f0f-56cf-4aa3-90bb-1c50129da657.png">
<br />
<br />
Beginning with the first index, the pivot element is compared to other elements.<br />
<img width="545" alt="Picture3" src="https://user-images.githubusercontent.com/95191692/145233069-54336fb9-9a34-4569-882e-e5ef762a0096.png">
<br />
<br />
If the element is larger than the pivot element, a second pointer is assigned to it.<br />
<img width="545" alt="Picture4" src="https://user-images.githubusercontent.com/95191692/145233072-8a8c44bf-d5e7-42c7-b518-f1d4e16287a9.png">
<br />
<br />
Other elements are compared to Pivot.<br />
<img width="510" alt="Picture5" src="https://user-images.githubusercontent.com/95191692/145233074-34c4c223-da7e-40e4-b40c-69aa1855d20f.png">
<br />
<br />
The operation is repeated to make the next larger element as the second pointer.<br />
<img width="510" alt="Picture6" src="https://user-images.githubusercontent.com/95191692/145233077-eca935a8-fe84-42fc-8407-47b80a234da2.png">
<br />
<br />
The procedure is repeated until the second-to-last element is reached.<br />
<img width="510" alt="Picture7" src="https://user-images.githubusercontent.com/95191692/145233078-fe1236b0-bb6b-454a-83cc-f1bf941d7d0b.png">
<br />
Then, the pivot element is switched with the second pointer.<br />

Again, pivot components are picked individually for the left and right sub-parts. Then step 2 is repeated.
Using recursion, choose the pivot element in each half and set it in the proper location.


<div class="begin-examples"></div>
Sorting the elements on the left of pivot using recursion.<br />
Sorting the elements on the right of pivot using recursion.
<div class="end-examples"></div>

|<img width=200/>|<img width=500/>|

## Implementation Of Quicksort

#### Implementation of QuickSort using C++

```cpp
#include<iostream>
using namespace std;

//swaping two elements high & low fuction
void swap(int* a, int* b) 
{ 
    int temp = *a; 
    *a = *b; 
    *b = temp; 
} 
//partitioning fuction
int partition(int arr[], int low, int high) 
{ 
    int pivot = arr[high];    // pivot 
    int i = (low - 1);  // Index of smaller element 
  
    for (int j = low; j <= high- 1; j++) 
    { 
        // If current element is smaller than or equal to pivot 
        if (arr[j] <= pivot) 
        { 
            i++;    // increment index of smaller element 
            swap(&arr[i], &arr[j]); 
        } 
    } 
    swap(&arr[i + 1], &arr[high]); 
    return (i + 1); 
}

//quicksort emplementation function
void quickSort(int arr[], int low, int high) 
{ 
    if (low < high) 
    { 
        // assigning pi
        int pi = partition(arr, low, high); 
  
        // sort elements before and after partition 
        quickSort(arr, low, pi - 1); 
        quickSort(arr, pi + 1, high); 
    } 
} 
 
 //display sorted elements fuction
void display(int arr[], int size) 
{ 
    for (int i=0; i < size; i++) 
        cout<<arr[i]<<", ";  
} 

int main()
{
  //declaring and accepting size of an arry
    int size;
    cout<<"\nEnter the size of elements : ";
    cin>>size;

    int arr[size];
    
    cout<<"\nBy using space enter the unsorted elements : ";

    for (int i = 0; i < size; ++i)
    {
        cin>>arr[i];
    }
    quickSort(arr, 0, size-1); 
    cout<<"\nSorted elements are : ";
    display(arr, size);
    return 0;
}
/*
OutPut
Enter the size of elements : 7
By using space enter the unsorted elements : 8 7 6 1 0 9 2
Sorted elements are : 0, 1, 2, 6, 7, 8, 9
*/
```

