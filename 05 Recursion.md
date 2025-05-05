
# Recursion

## Greatest common divisor
``` cpp
void gcd(int a, int b) {
    if(b == 0) {
        return a;
    }
    return gcd(b, a % b);
}
// a, b -> 12, 8 -> 8, 4 -> 4, 0
```

**Base cases are very important in recursion**. Without them you can will unexpected warnings, overflows and wrong answers. Example of base case above: `if(b == 0) { return a; }`.

## Example problem
> Count the number of paths in a grid from the upper left corner to the lower right corner where 0 is a walkable tile and 1 is a wall.

```cpp
int res = 0;

void searcher(vector<vector<int>> grid, int i = 0, int j = 0) {
    if(i < 0 || i >= grid.size() || j < 0 || j >= grid[i].size()) {
        return;
    }
    if(grid[i][j] == 1) {
        return;
    }
    if(i+1 == grid.size() && j+1 == grid[i].size()) {
        res++;
    }
    
    grid[i][j] = 1;

    searcher(grid, been, i+1, j);
    searcher(grid, been, i-1, j);
    searcher(grid, been, i, j+1);
    searcher(grid, been, i, j-1);
}
```

# Example problems

https://leetcode.com/problems/fibonacci-number/

[Divide apples](https://cses.fi/problemset/task/1623)
```cpp
#include <bits/stdc++.h>

using namespace std;

using ll = long long;

int n;

vector<long long> weights;

ll recurse_apples(int index, ll sum1, ll sum2) {

	// We've added all apples- return the absolute difference

	if (index == n) { return abs(sum1 - sum2); }

	// Try adding the current apple to either the first or second set

	return min(recurse_apples(index + 1, sum1 + weights[index], sum2),

	           recurse_apples(index + 1, sum1, sum2 + weights[index]));

}

int main() {

	cin >> n;

	weights.resize(n);

	for (int i = 0; i < n; i++) { cin >> weights[i]; }

	// Solve the problem starting at apple 0 with both sets being empty

	cout << recurse_apples(0, 0, 0) << endl;

}
```

https://leetcode.com/problems/number-of-islands/

Complexity: O(n^2) because recursion is at most n^2 times over n^2 loops

https://leetcode.com/problems/island-perimeter/
