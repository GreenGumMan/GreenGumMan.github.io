---
layout: posts
title:  "[CSES筆記］最大連續子陣列和"
date:   2026-07-19 10:20:38 +0800
---
# 問題

給定一陣列A，試求最大連續子陣列的和。

# 解

另陣列``dp[k]``為以``k``結尾連續子陣列的和最大值，則它會有兩種情況：

1. 達成該和的子陣列包含``k``與「以``k-1``結尾且和為``dp[k-1]``子陣列」。
2. 達成該和的子陣列只包含``k``。

由於是以``k``結尾，故選擇這兩種情況中最大的那一種。由此可知``dp ``的遞迴定義式：

```math
dp[k]=
\begin{cases}
A[0] & k=0\\
\max(dp[k-1]+A[k],\,A[k])&k\ge1
\end{cases}
```

由於所求連續陣列一定有唯一的結尾，故我們的目標變成：找出``dp[k] ``的最大值。由此設計出以下程式：

```Cpp
int best = a[0];
int dp_k = a[0];
for(int k=1;k<n;k++){
    dp_k = max(dp_k+a[k],a[k]);
    best = max(dp_k,best);
}
cout << best;
```

> 由於``dp[k]``只需要``dp[k-1]``即可求得，故我們並不需要使用函式遞迴也不需要使用陣列儲存結果，只需要儲存``dp[k-1]``即可。

> 這種解法將需要``O(n)``空間的動態規劃算法優化到``O(1)``空間。

# 完整解

```Cpp
#include<bits/stdc++.h>

using namespace std;

int main(){
    int n;
    cin >> n;
    
    vector<int> a(n);
    
    for(int i=0;i<n;i++){
       cin >> a[i];
    }
    
    int best = a[0];
    int dp_k = a[0];
    for(int k=1;k<n;k++){
        dp_k = max(dp_k+a[k],a[k]);
        best = max(dp_k,best);
    }
    cout << best;
}
```