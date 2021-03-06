Asked by Google.

**Given a list of numbers and a number K, return whether any two numbers from the list add up to K.** 
>**First line of input contains size of the list.**  
>**Second line of input contains space seperated elements of the list.**  
>**Third line of input contains K.**
### Sample Input
**4**  
**10 15 3 7**  
**17**
### Sample Output
**True**
### Explanation
**10 + 7 = 17. Hence, return True.**
### Sample Input
**4**  
**10 15 3 7**  
**16**
### Sample Output
**False**
### Explanation
**No any two numbers adds up to 16. Hence, return False.**

### Approach 1: Using 2 loops
>**Try every combination of two numbers from a list and check if they add up to K.** 

***:stopwatch: Time Complexity - O(n<sup>2</sup>), where n is length of the list.***   
***:floppy_disk: Space Complexity - O(1), because extra space is not used.***  

### Solution | Python
```python
def pairSum(numList, K):
    for i in numList:
        for j in numList:
            if (i + j) == K:
                return True
    return False
size = int(input())
numList = [int(x) for x in input().split()]
K = int(input())
print(pairSum(numList, K))
```
### Solution | C++
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

bool pairSum(vector<int> &numList, int K){
  for (int i=0; i<numList.size(); i++){
    for (int j=0; j<numList.size(); j++){
      if (numList[i] + numList[j] == K)
        return true;
    }
  }
  return false;
}

int main(){
  vector<int> numList;
  int size, K, n;
  cin>>size;
  for (int i=0; i<size; i++){
    cin>>n;
    numList.push_back(n);
  }
  cin>>K;
  cout<<(pairSum(numList, K) ? "True" : "False");
  return 0;
}
```
### Approach 2: Two-Pointers Technique
>**Sort the given list.**      
>**Take two pointers, pointing two start and end of the list, respectively.**   
>**Traverse through sorted array.**  
>>**Increase/Decrease their value based on the condition.**   

***:stopwatch: Time Complexity - O(nlogn) = O(nlogn) + O(n) = (Time Complexity of loop) + (Time Complexity of sort()).***  
***:floppy_disk: Space Complexity - O(1), because extra space is not used.***

### Solution | Python
```python
def pairSum(numList, K):
  start, end = 0, (len(numList) - 1)
  numList.sort()
  
  while start < end:
    if numList[start] + numList[end] == K:
      return True
    elif numList[start] + numList[end] < K:
      start += 1
    else:
      end -= 1
  return False

size = int(input())
numList = [int(x) for x in input().split()]
K = int(input())
print(pairSum(numList, K))
```
### Solution | C++
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

bool pairSum(vector<int> &numList, int K){
  int start = 0, end = (numList.size() - 1);
  sort(numList.begin(), numList.end());
  while (start < end){
    if (numList[start] + numList[end] == K)
      return true;
    else if(numList[start] + numList[end] < K)
      start += 1;
    else
      end -= 1;
  }
  return false;
}

int main(){
  vector<int> numList;
  int size, K, n;
  cin>>size;
  for (int i=0; i<size; i++){
    cin>>n;
    numList.push_back(n);
  }
  cin>>K;
  cout<<(pairSum(numList, K) ? "True" : "False");
  return 0;
}
```

### Reference
**:green_book: [GeeksforGeeks](https://www.geeksforgeeks.org/two-pointers-technique/)**    
**:notebook: [GitHub](https://github.com/liyin2015/Algorithms-and-Coding-Interviews/blob/master/two_pointer.pdf)**    
**:orange_book: [LeetCode](https://leetcode.com/articles/two-pointer-technique/)**   
**:notebook: [Medium](https://medium.com/@kevinlai76/algorithm-two-pointer-technique-a27103ed7ea1)**  

### Practice
:memo: **[HackerEarth](https://www.hackerearth.com/practice/basic-programming/implementation/basics-of-implementation/practice-problems/algorithm/pair-sum-1-0062d9ab/)**

|**:file_folder: [INDEX](https://github.com/theInvincible/Daily-Coding-Problem/blob/master/Collection/INDEX.md)**|
|----------------------------------------------------------------------------------------------------------------|
