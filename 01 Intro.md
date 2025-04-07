# Introduction to C++

Example program *hello.cpp*
``` cpp
#include<iostream>
#include<bits/stdc++.h>

using namespace std;

int main()
{
  string name;
  cin >> name;
  cout << "Hello, " << name << "!\n";
  return 0;
}
```

- Libraries and `#include<bits/stdc++.h>` (don't use for personal projects)

# Data types and data structures

```cpp
bool b = false; // true=1 false=0
int i = 2; // 32bit - max ~10^9
double d = 5.6;
char c = 'H';
string s = "Hello";

long l = 123456; //64bit
long long ll = 987654321; // max ~10^18
```

```cpp
int array[4];
vector<int> v0(4, 1); // 1 1 1 1
vector<int> v1 = {2, 12, 54, 31, 8};
vector<string> v2 = {"Hello", "World!"};

pair<int, int> p0 = make_pair(1, 2);
pair<int, string> p1 = {1, "Hello"};

queue<int> q;
```
- queue: `push`, `pop`, `front`
- vector: `push_back`, `pop_back`, `v[1]` - indexing
- pair: `make_pair`, `p.first`, `p.second`

# Operators, statements 

``` cpp
int i = 2;
i++; // 3
i += 4; // 7
i--; // 6
i -= 2; // 4
i *= 5; // 20
i /= 4; // 5
i %= 3; // 5 % 3 = 2 remainder

// &&, ||, ! operators
if(i == 1) {
    //Do something 
}
else {
    //Do something
}
```

[Watermelon](https://codeforces.com/problemset/problem/4/A)

# Loops

```cpp
for(int i = 0; i < n; i++) {
  // Do something
}

vector<int> v(5, 0)
for(auto i: v) {
  // Do something
}

while(!v.empty()) {
  // Do something
  v.pop_back();
}
```

# Functions

``` cpp
#include<bits/stdc++.h>

using namespace std;

void hello() {
  cout << "hello" << endl;
}

int calc(int a, int b) {
  int sum = a+b;
  return sum;
}

int main()
{
  hello();    
  cout << calc(2, 3) << endl;
  return 0;
}
```

# Input types

```cpp
#include<bits/stdc++.h>

using namespace std;

int main()
{
  // standart input/output from command line 
  int i;
  cin >> i;
  cout << i << endl;
	
  // standart input get whole line (until encounter \n)
  string s;
  getline(cin, s);

  // read and write to file
  freopen("input.txt", "r", stdin);
  cin >> i;
  freopen("output.txt", "w", stdout);
  cout << i;
  // or
  ifstream ifs("input.txt", ifstream::in);
  ifs >> i;
  ofstream ofs("output.txt", ofstream::out);
  ofs << i;
    
  return 0;
}
```

[Team](https://codeforces.com/problemset/problem/231/A)

[Fence Painting](https://usaco.org/index.php?page=viewproblem2&cpid=567)

[Sviestuvai-2023-1et](https://codeforces.com/gym/547716/problem/C)

# Example problems

## [Watermelon](https://codeforces.com/problemset/problem/4/A)
```cpp
void solve() {
	int M;
	cin >> M;
	if(M % 2 == 0 && M != 2) {
		cout << "YES";
	}
	else {
		cout << "NO";
    }
}
```

## [Team](https://codeforces.com/problemset/problem/231/A)
```cpp
void solve() {
	int n;
	cin >> n;
	int res = 0;
	for (int i = 0; i < n; i++)
	{
		int p, v, t;
		cin >> p >> v >> t;
		if(p+v+t >= 2) {
			res++;
		}
	}
	cout << res << endl;
}
```

## [Fence Painting](https://usaco.org/index.php?page=viewproblem2&cpid=567) 
```cpp
void solve() {
    int a, b, c, d;
    cin >> a >> b >> c >> d;
    int total = (b - a) + (d - c);
	int intersection = max(min(b, d) - max(a, c), 0);
	cout << total - intersection << "\n";
}
```

```cpp
void solve() {
	vector<bool> cover(100);

	int a, b, c, d;
	cin >> a >> b >> c >> d;

	for (int i = a; i < b; i++) 
	{ 
		cover[i] = true; 
	}
	for (int i = c; i < d; i++) 
	{ 
		cover[i] = true; 
	}

	int ans = 0;
	for (int i = 0; i < cover.size(); i++) 
	{ 
		ans += cover[i]; 
	}
	cout << ans << endl;
}
```

## Sviestuvai-2023-1et
```cpp
#include<bits/stdc++.h>

using namespace std;

int main()
{
    int n;
    cin >> n;
    vector<int> a(n);
    for (int i = 0; i < n; i++)
    {
        cin >> a[i];
    }
    sort(a.begin(), a.end());
    
    int mn = 1e9+1;
    int j = 1;
    for (int i = 1; i < n; i++)
    {
        if(a[i]-a[i-1] < mn) {
            mn = a[i]-a[i-1];
            j = i;
        }
    }
    cout << a[j-1] << "\n" << a[j] << endl;

    return 0;

}
```
# References
[Competitive Programmer’s Handbook](https://cses.fi/book/book.pdf#page=14)
