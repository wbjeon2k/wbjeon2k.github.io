---
layout: post
categories: ps Codeforces
tags: greedy implementation
date: 2021-02-10 20:00 +0900
title: "Codeforces #356 Div.2"
---

## Codeforces #356 Div.2

본격적으로 Competitive Programming 연습을 하기 위해서 지난 [Codeforces](https://codeforces.com/) 라운드 들을 upsolve 하기 시작했다.

대회처럼 virtual participation 을 통해 연습을 하니, 시간을 정해두고 푸는것은 역시 다르다는 생각이 든다.

대회 시간에 완전히 AC를 받지 못한 문제들을 돌아보는 포스트다.

# D. Bear and Tower of Cubes

부피 $X$ 가 주어졌을때, $X$ 보다 작으면서 블럭들의 개수를 최대로 하는 M 을 아무거나 찾는 문제다.

남은 부피가 $X$ 일때 $a^3 <= X$ 인 $a$ 를 찾는것은 쉽지만,

개수를 최대로 하기 위해서는 $(a^3) - 1 - (a-1)^3$ 또한 관찰을 해야하는 greedy 문제다.

Greedy 문제들을 많이 풀어보지 않아서 이 쪽에 약하다는걸 느끼는 문제였다.

# E. Bear and Square Grid

TLE가 나더라도 문제를 풀어보는 시도를 적극적으로 해야한다는걸 배운 문제다.

아무리 생각해도 $O(N^2*K)$, K의 범위를 생각하면 $O(N^3)$ 내로 풀 수가 없어서 TLE를 내지 않고 풀 수 있는 방법이 없다고 생각했지만,

내가 생각했던 풀이가 정해가 맞았다. $K^2$ 사각형을 놓을 수 있는 모든 자리를 고려하면서 4가지 방향에 대해 모두 탐색 해야한다.

아이디어 자체는 straight forward 하지만, 구현 하기에 어려운 문제였다.

PS 의 본질은 아이디어가 아니라, 그것을 구체적으로 옮기는 연습인것을 까먹으면 안된다.

```cpp
// codeforces
// https://codeforces.com/contest/680/problem/D

#define _CRT_SECURE_NO_WARNINGS
#include <bits/stdc++.h>
using namespace std;

#define ll long long

#define pii pair<int, int>
#define pll pair<ll, ll>
#define MAXI 100100
#define cplx complex<double>
const double PI = acos(-1);
const ll INF = INT_MAX / 2;
// interactive: fflush(stdout);

ll n, k;

inline ll cube(ll a) { return a * a * a; }

ll bisearch(ll a) {
    ll lo, hi;
    lo = 1;
    hi = a;
    while (lo + 1 < hi) {
        ll mid = (lo + hi) / 2;

        if (cube(mid) > a) {
            hi = mid;
        }
        else lo = mid;

    }
    return lo;
}

pll ans = { 0,0 };

void blocks(ll capacity, ll blk, ll csum) {
    if (capacity < 0) return;

    if (capacity == 0) {
        ans = max(ans, make_pair(blk, csum));
        return;
    }

    ll a, b, largest;
    largest = 1;
    while (cube(largest + 1) <= capacity) ++largest;
    //a = capacity - cube(largest);
    //b = cube(largest) - 1 - cube(largest - 1);
    blocks(capacity - cube(largest), blk + 1, csum + cube(largest));
    if (largest >= 1) blocks(cube(largest) - 1 - cube(largest - 1), blk + 1, csum + cube(largest - 1));
    return;
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(NULL);
    //cout.tie(NULL);

    //ifstream cin; cin.open("input.txt");

    cin >> n;
    blocks(n, 0, 0);

    printf("%lld %lld\n", ans.first, ans.second);

    return 0;
}

```

```cpp
// codeforces
//https://codeforces.com/contest/680/problem/E

#define _CRT_SECURE_NO_WARNINGS
#include <bits/stdc++.h>
using namespace std;

#define ll long long

#define pii pair<int, int>
#define pll pair<ll, ll>
#define MAXI 100100
#define cplx complex<double>
const double PI = acos(-1);
const ll INF = INT_MAX / 2;
// interactive: fflush(stdout);

ll n, k;

int board[505][505];
int dx[4] = { -1,0,1,0 };
int dy[4] = { 0,1,0,-1 };

ll ans = 0;
int component[200200], csize[200200];

inline bool isinside(int x, int y) {
    if (x<1 || x>n || y<1 || y>n) return false;
    return true;
}

void printboard() {
    for (int i = 1; i <= n; ++i) {
        for (int j = 1; j <= n; ++j) {
            printf("%d ", board[i][j]);
        }
        printf("\n");
    }
}

int dfs(int x, int y, int comp) {
    int ret = 0;
    board[x][y] = comp;
    for (int i = 0; i < 4; ++i) {
        int nx, ny;
        nx = x + dx[i];
        ny = y + dy[i];
        if (!isinside(nx, ny)) continue;
        if (board[nx][ny] != -1) continue;
        board[nx][ny] = comp;
        ret += dfs(nx, ny, comp);
    }
    ret++;
    return ret;
}

void findcc() {
    int comp = 0;
    for (int i = 1; i <= n; ++i) {
        for (int j = 1; j <= n; ++j) {
            if (board[i][j] == -1) {
                ++comp;
                int ccsize = dfs(i, j, comp);
                csize[comp] = ccsize;
            }

        }
    }
}

set<int> st;

int tsize = 0;
void findadj(int x, int y) {
    st.clear();
    vector<int> visited;
    tsize = 0;
    //top edge
    for (int i = y; i < y + k; ++i) {
        if (!isinside(x - 1, i)) continue;
        if (board[x - 1][i]) {
            visited.push_back(board[x - 1][i]);
        }
    }
    //bottom edge
    for (int i = y; i < y + k; ++i) {
        if (!isinside(x + k, i)) continue;
        if (board[x + k][i]) {
            visited.push_back(board[x + k][i]);
        }
    }
    //left edge
    for (int i = x; i < x + k; ++i) {
        if (!isinside(i, y - 1)) continue;
        if (board[i][y - 1]) {
            visited.push_back(board[i][y - 1]);
        }
    }
    //right edge
    for (int i = x; i < x + k; ++i) {
        if (!isinside(i, y + k)) continue;
        if (board[i][y + k]) {
            visited.push_back(board[i][y + k]);
        }
    }

    sort(visited.begin(), visited.end());

    if (visited.size() == 0) {
        tsize = 0;
        return;
    }

    tsize = csize[visited[0]];
    int last = visited[0];
    for (int i = 1; i < visited.size(); ++i) {
        if (visited[i] == last) continue;
        last = visited[i];
        tsize += csize[visited[i]];
    }
    /*
    for(auto iter = st.begin() ; iter != st.end();++iter){
        tsize += csize[*iter];
    }
    */
}

void findinside(int x, int y) {
    for (int i = x; i < x + k; ++i) {
        for (int j = y; j < y + k; ++j) {
            if (board[i][j] == 0) continue;
            csize[board[i][j]]--;
        }
    }
}

void restore(int x, int y) {
    for (int i = x; i < x + k; ++i) {
        for (int j = y; j < y + k; ++j) {
            if (board[i][j] == 0) continue;
            csize[board[i][j]]++;
        }
    }
}

void findans() {

    for (int i = 1; i + k <= n + 1; ++i) {
        findinside(i, 1);
        for (int j = 1; j + k <= n + 1; ++j) {
            findadj(i, j);
            ans = max(ans, k * k + tsize);
            if (j + k != n + 1) {
                for (int x = i; x < i + k; ++x) {
                    csize[board[x][j]]++;
                    csize[board[x][j + k]]--;
                }
            }
        }
        restore(i, n - k + 1);
    }
}



int main() {
    ios::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);

    //ifstream cin; cin.open("input.txt");

    cin >> n >> k;

    for (int i = 0; i < n; ++i) {
        string s;
        cin >> s;
        for (int j = 1; j <= n; ++j) {
            if (s[j - 1] == '.') board[i + 1][j] = -1;
            else board[i + 1][j] = 0;
        }
    }
    findcc();
    findans();


    printf("%lld\n", ans);


    return 0;
}


```