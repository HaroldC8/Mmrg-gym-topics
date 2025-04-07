# Maps & sets

```cpp
map<string, int> m = {{"John", 2}, {"Paul", 5}};
cout << m["John"] << endl;
m["Johnathan"] = 5;
m["John"] = 8;
cout << m["John"] << endl;

set<int> s = {1, 5, 6, 9};
s.insert(2);
cout << s.size() << endl;
s.insert(1);
cout << s.size() << endl;
```

- set `count`
- map and set `erase`

# Code complexity

```cpp
// O(n)
for(int i = 0; i < n; i++) {
	// Do something
}

// O(n^2)
for(int i = 0; i < n; i++) {
	for(int j = 0; j < n; j++) {
		// Do something
	}
}

// O(n*m)
for(int i = 0; i < n; i++) {
	for(int j = 0; j < m; j++) {
		// Do something
	}
}

// O(1)
int i = 0;
i++;
```

- [Complexity graph](https://www.linkedin.com/pulse/measuring-code-complexity-performance-withexamples-luis-soares-m-sc-)
- [Complexity table](https://miro.medium.com/v2/resize:fit:640/format:webp/1*bv5jWIWMDO2tFaWX-bwx1w.png)

- O(n) + O(n^2) = O(n^2)
- searching in maps or sets vs in vectors

# Example problems

## [Distinct Numbers](https://cses.fi/problemset/task/1621)
```cpp
void solve() {
	int n;
	cin >> n;
	set<int> s;
	for (int i = 0; i < n; i++) {
		int num;
		cin >> num;
		s.insert(num);
	}
	cout << s.size() << endl;
}
```

## [Where am I?](https://usaco.org/index.php?page=viewproblem2&cpid=964)
```cpp
void solve() {
	int n;
	string s;
	cin >> n >> s;
	
	for (int len = 1; len <= n; len++) {
		bool found = true;
		set<string> freq;
		for (int i = 0; i <= n - len; i++) {
		
			string cur = s.substr(i, len);
			if (freq.count(cur)) 
			{ 
				found = false;
				break;
			}
			freq.insert(cur);
		}
		
		if (found) {
			cout << len << endl;
			return;
		}
	}
}
```

## [Same Differences](https://codeforces.com/problemset/problem/1520/D)
```cpp
#include<bits/stdc++.h>

using namespace std;

int main()
{
    int t;
    cin >> t;
    while(t--) {
        int n;
        cin >> n;
        map<int, long long> m;
        for (int i = 0; i < n; i++)
        {
            int x;
            cin >> x;
            m[x-i]++;
        }
        long long res = 0;
        for(auto i: m) {
            if(i.second < 2) {
                continue;
            }
            res += i.second*(i.second-1)/2;
        }
        cout << res << endl;
    }
    return 0;
}
```

# References
[Competitive Programmer’s Handbook.pdf](https://cses.fi/book/book.pdf#page=27)

