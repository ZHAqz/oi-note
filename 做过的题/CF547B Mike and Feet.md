和[[所有子数组最小值之和]]非常像唯一的不同就是再统计答案的时候统计`a[i]`对应的最大长度，基于一个重要的观察：答案序列是单调不增的
```cpp
#include <bits/stdc++.h>
using namespace std;
using ll = long long;
#define endl '\n'
const int N = 200005;

int n, a[N], l[N], r[N], cnt[N];
stack<int> st;

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0); cout.tie(0);
    cin >> n;
    for(int i = 1; i <= n; i++) cin >> a[i];
    for(int i = 1; i <= n; i++) {
        while(!st.empty() && a[st.top()] >= a[i]) {
            r[st.top()] = i - 1;
            st.pop();
        }
        st.push(i);
    }
    while(!st.empty()) {
        r[st.top()] = n;
        st.pop();
    }
    for(int i = n; i >= 1; i--) {
        while(!st.empty() && a[st.top()] > a[i]) {
            l[st.top()] = i + 1;
            st.pop();
        }
        st.push(i);
    }
    while(!st.empty()) {
        l[st.top()] = 1;
        st.pop();
    }
    for(int i = 1; i <= n; i++) {
        cnt[r[i] - l[i] + 1] = max(cnt[r[i] - l[i] + 1], a[i]);
    }
    for(int i = n; i >= 1; i--) {
        cnt[i] = max(cnt[i + 1], cnt[i]);
    }
    for(int i = 1; i <= n; i++) cout << cnt[i] << ' ';
}
```