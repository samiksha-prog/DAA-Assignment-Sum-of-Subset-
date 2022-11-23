# DAA-Assignment (Sum of Subset)
### Assignment Question:
Step 1: Create an array of size : x  
Step 2: Input an integer: m  
Step 3: Sort the array  
### Program A]  
Write a program to create a nxn array of “0” and “1”, such that, when summation of {n[i]*x[i]} is equal to integer “m”. Print the rows of nxn array resulting in “m” <br/>  
## Sum of Subset  
This program needs the logic of Sum of Subset. We need to find out 'n' subsets whose sum is equal to m and these subsets should be represented as the matrix of 0s and 1s. Subset sum problem is to find subset of elements that are selected from a given set whose sum adds up to a given number m. We are considering the set contains non-negative values. It is assumed that the input set is unique (no duplicates are presented).  
### Backtracking Algorithm for Subset Sum  
Backtracking can be used to make a systematic consideration of the elements to be selected.
Assume given set of 4 elements, say w[1] … w[4]. Tree diagrams can be used to design backtracking algorithms. The following tree diagram (Variable size tree) depicts approach of generating variable sized tuple.  
<p align="center">
  <img width="455" alt="image" src="https://user-images.githubusercontent.com/83723880/203628149-acaa0204-5245-43e4-a77b-914646d42db4.png">
</p>  
```
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
    /*int x[] = {11, 13, 24, 7};
    int size = 4;
    int m = 31;
    int subSet[size];
    subsetSum(x, subSet, size, 0, 0, 0, m);
    >= sum-(sum*0.25) && total <= sum+(sum*0.25)*/
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
### Program B]
Write a program to create “z” rows out of “n” rows of “nxn” array and predict the row such that {n[i]*x[i]} resulting in “m”.

