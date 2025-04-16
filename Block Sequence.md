# 🧠 Problem Notes

## 📌 Problem Title: [Block Sequence](https://codeforces.com/problemset/problem/1881/E)
**Rating:** 1500  
**Tags:** Dynamic Programming (Knapsack Variation)  
**Status:** ✅ Solved

---

## 💭 First Thought:
- first number indicates the length of the block.
- Deleting a **number** affects the blocks *before* that number not the after ones.
- Considered implementing DP, as  larger problem was dependent on smaller subproblems.
---

## 📚 Editorial Insight:
- discovered that DP can  be implemented in reverse .
- *dp[ i ]* depends on either *dp[ i+1 ]* or *dp[ i+1+a[i] ]*.
- Similar to knapsack but somehow different.
---

## ✨ Key Takeaways:
- Trick 1: For DP problems, explore patterns in unconventional way.
- Trick 2: Knapsack problems often appear with variation.

---

## 🧾 Code:
<details>
<summary>Click to expand</summary>

```cpp
// My code
#include<bits/stdc++.h>
using namespace std;
void solve(){
    int n;cin>>n;
    vector<int>a(n);
    for(auto &it:a)cin>>it;
    int dp[n+1];
    dp[n]=0;
    for(int i=n-1;i>=0;i--){
        dp[i]=dp[i+1]+1;
        if(i+a[i]+1<=n)dp[i]=min(dp[i+a[i]+1],dp[i]);
    }
    cout<<dp[0]<<endl;
}
int main(){
    int t;cin>>t;
    while(t--)solve();
}
