Common elements in all row of a given matrix in Java
Here, in this page we will discuss the program to find the common elements in all row of a given matrix in Java Programming language. We will discuss algorithm along it’s code.

Common elements in all row of a given matrix in Java
Method 1 :
In this algorithm we will check for every element in first row, if that is present in other rows or not.

For checking the presence, take one variable count.
Now, run a loop from index 1 to M.
Take a variable flag =0;
Now, run a loop from index 0 to N, if (x==mat[i][j]) set flag =1 and break the loop.
After coming out from loop check if(flag==1) set, count++.
At last, check if count == M-1, print that value.
Time and Space Complexity :
Time complexity: O(M*M*N)
Space complexity: O(1)
Common Element in all rows of the matrix
Method 1 : Code in Java
Run
class Main
{
   
    public static void main(String args[])
    {
        int mat[][] = {{10, 20, 30, 40},
                       {15, 25, 35, 30},
                       {27, 30, 37, 48},
                       {32, 33, 39, 30}};
        
        int N=4, M=4;
        
        for (int j = 0; j < N; j++){   
            int x = mat[0][j], count = 0;
            
            for (int i = 1; i < M; i++){
                int flag = 0;
                    for(int k = 0; k < N; k++){
                        if(x==mat[i][k]){
                            flag = 1;
                            mat[i][k] = -1;
                            break;
                        }        
                    }
                if(flag==1){
                    count++;   
            }
        }
        
        if (count==M-1)
           System.out.print(x);
            
        }
    }
}
 
Output :
30
Method 2:
In this method we will use map.
We initially insert all elements of the first row in an map.
For every other element in remaining rows, we check if it is present in the map.
If it is present in the map and is not duplicated in current row, we increment count of the element in map by 1, else we ignore the element.
If the currently traversed row is the last row, we print the element if it has appeared m-1 times before. 
Method 2 : Code in Java
Run
import java.util.*;
 
class Main
{
    static int M = 4;
    static int N =5;
     
    static void printCommonElements(int mat[][])
    {
     
        Map<Integer,Integer> mp = new HashMap<>();
         
        for (int j = 0; j < N; j++)
            mp.put(mat[0][j],1);
             
        for (int i = 1; i < M; i++)
        {
            for (int j = 0; j < N; j++)
            {
                if (mp.get(mat[i][j]) != null && mp.get(mat[i][j]) == i)
                {
                    mp.put(mat[i][j], i + 1);
                    if (i == M - 1)
                        System.out.print(mat[i][j] + " ");
                }
            }
        }
    }
    public static void main(String[] args)
    {
        int mat[][] =
        {
            {1, 2, 1, 4, 8},
            {3, 7, 8, 5, 1},
            {8, 7, 7, 3, 1},
            {8, 1, 2, 7, 9},
        };
     
        printCommonElements(mat);
    }
}
Output :
8 1
