---
title: 合并队列题解
published: 2025-01-20
pinned: true
description: 题解修改
tags: [Markdown, Blogging]
category: Examples
licenseName: "Unlicensed"
author: emn178
sourceLink: "https://github.com/emn178/markdown"
draft: false
---

完善程序（一）合并序列
有两个长度为 N 的单调不降序列 A 和 B，序列的每个元素都是小于 10^9 的非负整数。在 A 和 B 中各取一个数相加可以得到 N^2 个和，求其中第 k 小的和。

> ```cpp
> #include <iostream>
> using namespace std;
> const int maxn = 100005;
> int n;
> long long k;
> int a[maxn], b[maxn];
>
> int* upper_bound(int *a, int *an, int ai) {
>   int l=0, r = an - a;
>   while (l < r) {
>     int mid = (l+r)>>1;
>     if (a[mid] > ai) {
>       r = mid;
>     } else {
>       l = mid+1;
>     }
>   }
>   return a + l;
> }
>
> long long get_rank(int sum) {
>   long long rank = 0;
>   for (int i = 0; i < n; i++) {
>     rank += upper_bound(b, b+n, sum - a[i]) - b;
>   }
>   return rank;
> }
>
> int solve() {
>   int l=0, r = ____(4)____;
>   while (l < r) {
>     int mid = ((long long)l + r) >> 1;
>     if (get_rank(mid) < k) {
>       l = mid+1;
>     } else {
>       r = mid;
>     }
>   }
>   return l;
> }
>
> int main() {
>   cin>>n>>k;
>   for (int i=0;i<n;i++) cin>>a[i];
>   for (int i=0;i<n;i++) cin>>b[i];
>   cout << solve() << endl;
>   return 0;
> }
> ```
>
> **单选题 36.** (4)处应填
