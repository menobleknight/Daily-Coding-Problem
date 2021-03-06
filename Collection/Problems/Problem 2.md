## Problem 2
***Asked by Uber.***
### Task
**Given an array of integers, return a new array such that each element at index** ***i*** **of the new array is the product of all the numbers in the original array except the one at** ***i.***
>**First line of input contains size of an array.**  
>**Second line of input contains elements of an array seperated by space.**  
### Sample Input
**5**  
**1 2 3 4 5** 
### Sample Output
**120 60 40 30 24**
### Explanation
**New array will be:**  
|**INDEX**|**PRODUCT**|
|---------|-----------|
|**0**|**2 * 3 * 4 * 5 = 120**|
|**1**|**1 * 3 * 4 * 5 = 60**|
|**2**|**1 * 2 * 4 * 5 = 40**|
|**3**|**1 * 2 * 3 * 5 = 30**|
|**4**|**1 * 2 * 3 * 4 = 24**|
### Sample Input
**3**  
**3 2 1** 
### Sample Output
**2 3 6**
### Explanation
**New array will be:** 
|**INDEX**|**PRODUCT**|
|---------|-----------|
|**0**|**2 * 1 = 2**|
|**1**|**3 * 1 = 3**|
|**2**|**3 * 2 = 6.**

### Approach 1: Using Division
>**Calculate PRODUCT of all elements of the original array.**  
>**Divide the PRODUCT by element at index** ***i*** **and store the resulting value in the new array at index** ***i.***
### Solution | Python
```python
def product(array):
    product_ = 1
    for i in array:
        product_ *= i
    return product_

size = int(input())
array = [int(x) for x in input().split()]
new_array = []
for i in array:
    new_array.append(product(array)//i)

print(new_array)
```
### Solution | C++
```cpp
#include <iostream>
#include <vector>
using namespace std;

int product(vector<int> &arr){
  int product_ = 1;
  for (auto i: arr){
    product_ *= i;
  }
  return product_;
}

int main() {
  vector<int> arr; 
  vector<int> new_array;
  int size, n;
  cin>>size;
  for (int i=0; i<size; i++){
    cin>>n;
    arr.push_back(n);
  }
  for (int j=0; j<arr.size(); j++){
    new_array.push_back(product(arr)/arr[j]);
  }
  for(auto k: new_array){
    cout<<k<<" ";
  }
  return 0;
}
```
### Approach 2: Without Division
>**Calculate PRODUCT of all elements, except element at index** ***i*** **and store that PRODUCT in the new array at index** ***i.***

### Solution | Python
```python
def product(array, i):
    product_ = 1
    for x in array:
        if not(x == i):
            product_ *= x
    return product_

size = int(input())
array = [int(x) for x in input().split()]
new_array = []
for i in array:
    new_array.append(product(array, i))

print(new_array)
```
### Short Solution | Python
```python
from functools import reduce

array = [int(x) for x in input().split()]
newArray = []

for i in array:
  newArray.append(reduce(lambda x, y: x * y, [x for x in array if not(x == i)]))

print(newArray)
```

### Solution | C++ 
```cpp
#include <iostream>
#include <vector>
using namespace std;

int product(vector<int> &arr, int i){
  int product_ = 1;
  for (auto x: arr){
    if (x != i){
      product_ *= x;
    }
  }
  return product_;
}

int main() {
  vector<int> arr; 
  vector<int> new_array;
  int size, n;
  cin>>size;
  for (int i=0; i<size; i++){
    cin>>n;
    arr.push_back(n);
  }
  for (int j=0; j<arr.size(); j++){
    new_array.push_back(product(arr, arr[j]));
  }
  for(auto k: new_array){
    cout<<k<<" ";
  }
  return 0;
}
```

|**:file_folder: [INDEX](https://github.com/theInvincible/Daily-Coding-Problem/blob/master/Collection/INDEX.md)**|
|----------------------------------------------------------------------------------------------------------------|
