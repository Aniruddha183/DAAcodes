# DAAcodes
# 1)Binary search code
import java.io.*;
import java.util.*;
 import java.util.Scanner;
 
 
public class BinarySearch{
   
   public static int binarySearch(int arr[], int x){
        int s =0,  e = arr.length-1;
        while(s<=e){
            int mid = s + (e-s)/2;
           
            if(arr[mid] == x){
                return mid;
            }
           
            if(arr[mid]<x){
                s = mid +1;
            }
            else{
                e = mid-1;
            }
        }
        return -1;
   
}
 
 
 
 
      
 
public static void main(String args[]){
    //BinarySearch ob = new BinarySearch();
             
             //Taking array as an input
             int n;
             int x;
            Scanner sc=new Scanner(System.in);
            System.out.print("Enter Array Size:");
            n=sc.nextInt();
            int[] arr = new int[n];
            System.out.println("Enter Array elements: ");
            for(int i=0; i<n; i++)
            {
                arr[i]=sc.nextInt();
            }
            System.out.print("Enter the target:");
            x = sc.nextInt();
           
           
            //calling the functions
            int result = binarySearch(arr,x);
            if(result == -1){
                System.out.println("element not present");
           
            }
            else{
                System.out.println("element present at index :" + result);
            }
}
}
 
 # 2)  Bubble sort
import java.util.*;
import java.io.*;
import java.util.Scanner;  
 
 
 
public class BubbleSort{
    public static void bubbleSort(int arr[]){
        int n = arr.length;
        for(int i =1; i< n; i++){
            for(int j =0; j < n-i; j++){
                if(arr[j]> arr[j+1]){
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }
   
   public static  void PrintArray(int arr[]){
        int n = arr.length;
        for(int i = 0; i<n; i++){
            System.out.print(arr[i]+ " ");
        }
    }
   
    public static void main(String args[]){
       // BubbleSort ob = new BubbleSort();
        int n;  
        Scanner sc=new Scanner(System.in);  
        System.out.print("Enter the number of elements you want to store: ");  
       
        n=sc.nextInt();  
       
        int[] arr = new int[n];  
        System.out.println("Enter the elements of the array: \n");  
        for(int i=0; i<n; i++)  
        {  
     
        arr[i]=sc.nextInt();  
        }  
        bubbleSort(arr);
        System.out.println("Sorted array is: ");
        PrintArray(arr);
       
    }
}


# 3)Merge sort
import java.util.Scanner;
import java.util.*;
import java.io.*;
 
public class MergeSort {
     
        public static void merge(int[] arr , int s , int e){
 
        int mid = (s + e)/2;
        int len1 = mid - s + 1; //length of first half
        int len2 = e - mid; //length of second half
        int[] arr1 = new int[len1];
        int[] arr2 = new int[len2];
 
       
 //copy elements in these arrays;
        int originalArrayIndex = s;
        for(int i = 0; i < len1; i++){
            arr1[i] = arr[originalArrayIndex++];
        }
 
//originalArrayIndex = mid + 1;
 
        for(int i = 0; i < len2; i++){
            arr2[i] = arr[originalArrayIndex++];
        }
 
        //merge two sorted arrays;
        originalArrayIndex = s;
 
        int idx1 = 0;
        int idx2 = 0;
        while(idx1 < len1 && idx2 < len2){
            if(arr1[idx1] < arr2[idx2]){
                arr[originalArrayIndex++] = arr1[idx1++];
            }
            else {
                arr[originalArrayIndex++] = arr2[idx2++];
            }
        }
 
        //if in arr1 elements are remaining
        while(idx1 < len1){
            arr[originalArrayIndex++] = arr1[idx1++];
        }
        //if in arr2 elements are remaining
        while(idx2 < len2){
            arr[originalArrayIndex++] = arr2[idx2++];
        }
    }
 
    public static void mergeSort(int[] arr , int s , int e){
        //base case
        if(s >= e)
            return;
 
        int mid = (s + e)/2;
        //left Part
        mergeSort(arr , s , mid);
        //right part
        mergeSort(arr , mid + 1 , e);
        merge(arr , s , e);
    }
 
 
     
     
     public static void main(String[] args) {
        int n;  
        Scanner sc=new Scanner(System.in);  
        System.out.print("Enter the number of elements you want to store: ");  
       
        n=sc.nextInt();  
       
        int[] arr = new int[n];  
        System.out.println("Enter the elements of the array: \n");  
        for(int i=0; i<n; i++)  
        {  
     
        arr[i]=sc.nextInt();  
        }
       
       
        mergeSort(arr , 0 , n - 1);
        System.out.println("sorted array: ");
        for(int i = 0; i < n; i++){
            System.out.print(arr[i] + " ");
        }
    }
}


# 4)Quick Sort
import java.util.Scanner;
 
public class QuickSort {
 
 
    public static void quickSort(int[] arr , int s , int e){
        //base case
        if(s >= e)
            return;
 
        //take the partition
        int p = partition(arr , s , e);
 
        //left part sort
        quickSort(arr , s , p - 1);
 
        //right part sort
        quickSort(arr , p + 1 , e);
 
    }
 
    public static int partition(int[] arr , int s , int e){
 
        int pivot = arr[s];
        int count = 0;
        //count of elements smaller than pivot element
        for(int i = s + 1; i <= e; i++){
            if(arr[i] <= pivot)
                count++;
        }
 
        int pivotIdx = s + count;
 
        //put pivot element at correct position
        int temp = pivot;
        arr[s] = arr[pivotIdx];
        arr[pivotIdx] = temp;
 
        int sIdx = s;
        int eIdx = e;
 
        //make smaller elements lie before pivot & larger elements after pivot
        while(sIdx < pivotIdx && eIdx > pivotIdx){
 
            //move sIdx++ till we find element greater than pivot element in left side
            while(arr[sIdx] <= pivot){
                sIdx++;
            }
            //move eIdx-- till we find smaller elements than pivot in right side
            while(arr[eIdx] > pivot){
                eIdx--;
            }
            //swap the values if found
            if(sIdx < pivotIdx && eIdx > pivotIdx){
                temp = arr[sIdx];
                arr[sIdx] = arr[eIdx];
                arr[eIdx] = temp;
 
                sIdx++;
                eIdx--;
            }
        }
        return pivotIdx;
    }
   
      public static void main(String[] args) {
       int n;  
        Scanner sc=new Scanner(System.in);  
        System.out.print("Enter the number of elements you want to store: ");  
       
        n=sc.nextInt();  
       
        int[] arr = new int[n];  
        System.out.println("Enter the elements of the array: \n");  
        for(int i=0; i<n; i++)  
        {  
     
        arr[i]=sc.nextInt();  
        }
 
        quickSort(arr , 0 , n - 1);
        System.out.println("Sorted array :");
        for(int i = 0; i < n; i++){
            System.out.print(arr[i] + " ");
        }
    }
}

# 5) coin change
class CoinChanger{
     
 
    int coinChangeProblem(int[] coins, int sum){
     
        int totalCoins = coins.length;
 
        // Creating array which stores subproblems' solutions
        double[][] arr = new double[totalCoins + 1][sum + 1];
 
        // Initialising first row with +ve infinity
        for(int j = 0; j <= sum; j++){
            arr[0][j] = Double.POSITIVE_INFINITY;
        }        
     
        // Initialising first column with 0
        for(int i = 1; i <= totalCoins; i++){
            arr[i][0] = 0;
        }
 
        // Implementing the recursive solution
        for(int i = 1; i <= totalCoins; i++){
            for(int j = 1; j <= sum; j++){
                if(coins[i - 1] <= j)
                    arr[i][j] = min(1 + arr[i][j - coins[i - 1]], arr[i - 1][j]);
                else
                    arr[i][j] = arr[i - 1][j];
            }
        }
 
        return (int)arr[totalCoins][sum];
    }
 
    // Helper function for the recursive solution.
    double min(double a, double b){
      if(a <= b){
        return a;
      }
      else{
        return b;
      }
    }
   
    public static void main(String[] args){
     
      int[] coins = {5, 7, 8, 9};
      int sum = 15;
 
      CoinChanger m = new CoinChanger();
      System.out.println("At least " + m.coinChangeProblem(coins, sum)
      + " coins are required to make a value of " + sum);
    }
  }



# 6) prims algorithm
// A Java program for Prim's Minimum Spanning Tree (MST)
// algorithm. The program is for adjacency matrix
// representation of the graph
 
import java.io.*;
import java.lang.*;
import java.util.*;
 
class MST {
 
    // Number of vertices in the graph
    private static final int V = 5;
 
    // A utility function to find the vertex with minimum
    // key value, from the set of vertices not yet included
    // in MST
    int minKey(int key[], Boolean mstSet[]) {
        // Initialize min value
        int min = Integer.MAX_VALUE, min_index = -1;
 
        for (int v = 0; v < V; v++)
            if (mstSet[v] == false && key[v] < min) {
                min = key[v];
                min_index = v;
            }
 
        return min_index;
    }
 
    // A utility function to print the constructed MST
    // stored in parent[]
    void printMST(int parent[], int graph[][]) {
        System.out.println("Edge \tWeight");
        for (int i = 1; i < V; i++)
            System.out.println(parent[i] + " - " + i + "\t"
                    + graph[i][parent[i]]);
    }
 
    // Function to construct and print MST for a graph
    // represented using adjacency matrix representation
    void primMST(int graph[][]) {
        // Array to store constructed MST
        int parent[] = new int[V];
 
        // Key values used to pick minimum weight edge in
        // cut
        int key[] = new int[V];
 
        // To represent set of vertices included in MST
        Boolean mstSet[] = new Boolean[V];
 
        // Initialize all keys as INFINITE
        for (int i = 0; i < V; i++) {
            key[i] = Integer.MAX_VALUE;
            mstSet[i] = false;
        }
 
        // Always include first 1st vertex in MST.
        key[0] = 0; // Make key 0 so that this vertex is
        // picked as first vertex
        parent[0] = -1; // First node is always root of MST
 
        // The MST will have V vertices
        for (int count = 0; count < V - 1; count++) {
            // Pick thd minimum key vertex from the set of
            // vertices not yet included in MST
            int u = minKey(key, mstSet);
 
            // Add the picked vertex to the MST Set
            mstSet[u] = true;
 
            // Update key value and parent index of the
            // adjacent vertices of the picked vertex.
            // Consider only those vertices which are not
            // yet included in MST
            for (int v = 0; v < V; v++)
 
                // graph[u][v] is non zero only for adjacent
                // vertices of m mstSet[v] is false for
                // vertices not yet included in MST Update
                // the key only if graph[u][v] is smaller
                // than key[v]
                if (graph[u][v] != 0 && mstSet[v] == false
                        && graph[u][v] < key[v]) {
                    parent[v] = u;
                    key[v] = graph[u][v];
                }
        }
 
        // print the constructed MST
        printMST(parent, graph);
    }
 
    public static void main(String[] args) {
        /*
         * Let us create the following graph
         * 2 3
         * (0)--(1)--(2)
         * | / \ |
         * 6| 8/ \5 |7
         * | / \ |
         * (3)-------(4)
         * 9
         */
        MST t = new MST();
        int graph[][] = new int[][] { { 0, 2, 0, 6, 0 },
                { 2, 0, 3, 8, 5 },
                { 0, 3, 0, 0, 7 },
                { 6, 8, 0, 0, 9 },
                { 0, 5, 7, 9, 0 } };
 
        // Print the solution
        t.primMST(graph);
    }
}
// This code is contributed by Aakash Hasija
 
 



