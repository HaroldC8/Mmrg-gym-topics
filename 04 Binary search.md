# Binary search 

A search algorythm that works in `O(log(n))` time.

- Array has to be sorted
- Can also be used with [monotonic functions](https://usaco.guide/silver/binary-search#binary-search-on-monotonic-functions) 


``` cpp
vector<int> arr;

void binary_search(int a, int b) {
  int n = arr.size();
  int a = 0, b = n-1; 
  while (a <= b) 
  { 
    int k = a+(b-a)/2; 
    if (array[k] == x) 
    { 
      // x found at index k 
    } 
    if (array[k] > x) b = k-1; 
    else a = k+1; 
  }
}
```

# Example problems

https://leetcode.com/problems/first-bad-version/description/

https://leetcode.com/problems/peak-index-in-a-mountain-array/

https://codeforces.com/problemset/problem/1904/B

https://codeforces.com/problemset/problem/1850/E
