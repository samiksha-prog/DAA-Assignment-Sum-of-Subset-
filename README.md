# DAA-Assignment (Sum of Subset)
### Assignment Question:
Step 1: Create an array of size : x  
Step 2: Input an integer: m  
Step 3: Sort the array  
### Program A]  
Write a program to create a nxn array of “0” and “1”, such that, when summation of {n[i]*x[i]} is equal to integer “m”. Print the rows of nxn array resulting in “m” <br/>  
## Sum of Subset  
This program needs the logic of Sum of Subset. We need to find out 'n' subsets whose sum is equal to m and these subsets should be represented as the matrix of 0s and 1s. Subset sum problem is to find subset of elements that are selected from a given set whose sum adds up to a given number m. We are considering the set contains non-negative values. It is assumed that the input set is unique (no duplicates are presented).  
The basic logic behind the algorithm is  
![IMG_20221124_013910](https://user-images.githubusercontent.com/83723880/203637756-ed4623ee-39ad-4051-883c-431ef198c6da.jpg)

### Backtracking Algorithm for Subset Sum 
<p align="center">
  <img width="455" alt="image" src="https://user-images.githubusercontent.com/83723880/203628149-acaa0204-5245-43e4-a77b-914646d42db4.png">
</p>
Backtracking can be used to make a systematic consideration of the elements to be selected.
Assume given set of 4 elements, say w[1] … w[4]. Tree diagrams can be used to design backtracking algorithms. The above tree diagram (Variable size tree) depicts approach of generating variable sized tuple.  

### Code:
```cpp
#include <iostream>  
using namespace std;  
void displaySubset(int set[], int subSet[], int size, int subsize){  
    int arr[size];  
    for(int i = 0; i < size; i++){  
        int flag=0;  
        int a=set[i];  
        for(int j=0; j < subsize; j++){
            if(a==subSet[j]){
                flag=1;
                break;
            }
        }
        if(flag==1)
            arr[i]=1;
        else
            arr[i]=0;
    }
    for(int i=0; i<size; i++)
        cout << arr[i] << "  ";
    cout << endl;
}
void subsetSum(int set[], int subSet[], int n, int subSize, int total, int nodeCount ,int sum){
    if(total == sum){
        displaySubset(set, subSet, n, subSize);
        subsetSum(set,subSet,n,subSize-1,total-set[nodeCount],nodeCount+1,sum);
        return;
    }else{
        for(int i = nodeCount; i < n; i++){
            subSet[subSize] = set[i];
            subsetSum(set,subSet,n,subSize+1,total+set[i],i+1,sum);
        }
    }
}
int main(){
    int n;
    cout << "Enter the array size: ";
    cin >> n;
    int x[n];
    cout << "Enter the array elements:\n";
    for(int i=0;i<n;i++){
        cin >> x[i];
    }
    int m;
    cout << "Enter the sum i.e. value of m: ";
    cin >> m;
    int subSet[n];
    cout << "Output matrix: \n";
    subsetSum(x, subSet, n, 0, 0, 0, m);
}
```
### Output:
<img width="300" alt="image" src="https://user-images.githubusercontent.com/83723880/203632541-b5422876-cdf3-4994-af4b-062c83014661.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/83723880/203632807-9ba238fe-0f5b-41a4-a324-4d2835defa03.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/83723880/203633393-7df18787-2c9d-4243-a706-ce680faac6a8.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/83723880/203633515-319577ac-57b4-4537-b8f5-7ee39884c8db.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/83723880/203633884-68939960-eec4-438c-a26f-79f762147f09.png">

### Program B]
Write a program to create “z” rows out of “n” rows of “nxn” array and predict the row such that {n[i]*x[i]} resulting in “m”.
### Code
```cpp
#include <iostream>
using namespace std;

void displaySubset(int set[], int subSet[], int size, int subsize){
    int arr[size];
    for(int i = 0; i < size; i++){
        int flag=0;
        int a=set[i];
        for(int j=0; j < subsize; j++){
            if(a==subSet[j]){
                flag=1;
                break;
            }
        }
        if(flag==1)
            arr[i]=1;
        else
            arr[i]=0;
    }
    for(int i=0; i<size; i++)
        cout << arr[i] << "  ";
    cout << endl;
}
void subsetSum(int set[], int subSet[], int n, int subSize, int total, int nodeCount ,int sum){
    if(total>= sum-(sum*0.25) && total <= sum+(sum*0.25)){
        displaySubset(set, subSet, n, subSize);
        subsetSum(set,subSet,n,subSize-1,total-set[nodeCount],nodeCount+1,sum);
        return;
    }else{
        for(int i = nodeCount; i < n; i++){
            subSet[subSize] = set[i];
            subsetSum(set,subSet,n,subSize+1,total+set[i],i+1,sum);
        }
    }
}
int main(){
    int n;
    cout << "Enter the array size: ";
    cin >> n;
    int x[n];
    int m;
    cout << "Enter the sum i.e. value of m: ";
    cin >> m;
    cout << "Input array:\n";
    for(int i=0;i<n;i++){
        cin >> x[i];
    }
    int subSet[n];
    cout << "Matrix that may result to sum " << m;
    subsetSum(x, subSet, n, 0, 0, 0, m);
}
```
### Output:
<img width="300" alt="image" src="https://user-images.githubusercontent.com/83723880/203636099-c8ec6883-4e9a-424a-b15e-7aec3132c44f.png">
<img width="300" alt="image" src="https://user-images.githubusercontent.com/83723880/203636529-3e069861-48af-4ec0-99a3-83703be509bc.png">

