# Two pointers

## Example problem
> Given a sorted array A, of size N, find if there exists any pair of elements (A[i], A[j]) such that their sum is equal to X.

### O(n^2) approach 
```cpp
bool isPairSum(vector<int>& A, int N, int X)
{
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (i == j) {
	            continue;
            }

            if (A[i] + A[j] == X) {
	            return true;
            }
        }
    }

    return false;
}
```

### Hashing O(n) but space is also O(n)
```cpp
bool isPairSum(vector<int>& A, int N, int X)
{
    set<int> s;
    for (int i = 0; i < N; i++) {
	    s.insert(X-A[i]);
    }
    for (int i = 0; i < N; i++) {
	    if(s.count(A[i]) > 0) {
		    return true;
	    }
    }

    return false;
}
```

### Two pointers O(n) space is O(1)
```cpp
bool isPairSum(vector<int>& A, int N, int X)
{
    int i = 0;

    int j = N - 1;

    while (i < j) {

        if (A[i] + A[j] == X) {
	        return true;
        }
        else if (A[i] + A[j] < X) {
	        i++;
        }
        else {
	        j--;
        }
    }
    return false;
}
```

# Example problems

https://leetcode.com/problems/valid-palindrome/description/

https://leetcode.com/problems/reverse-words-in-a-string/

https://codeforces.com/problemset/problem/1870/C

# References
https://www.geeksforgeeks.org/two-pointers-technique/
