## Question

You are given a 2D ASCII maze where each cell has a movement cost. Your goal is to compute the **minimum cost path** from `S` to `E` using **Dijkstra’s algorithm**.

### Maze Layout

```
S 1 9 9 9 9
1 1 9 1 1 9
9 1 9 1 9 9
9 1 1 1 9 9
9 9 9 1 1 1
9 9 9 9 9 E
```

### Rules

* Move in **4 directions only** (up, down, left, right).
* Each number = **cost to enter that cell**.
* `S` = cost 0, `E` = cost 0.
* Cells with `9` are **valid but expensive traps**.
* Return the **minimum total cost**.

---

## Task

Fill in the missing parts of the Dijkstra implementation:

```cpp
#include <bits/stdc++.h>
using namespace std;

typedef pair<int, pair<int,int>> State;

int dijkstra(vector<vector<int>>& grid, pair<int,int> start, pair<int,int> end) {
    int n = grid.size();
    int m = grid[0].size();

    vector<vector<int>> dist(n, vector<int>(m, INT_MAX));
    priority_queue<State, vector<State>, greater<State>> pq;

    // TODO: initialize start

    while (!pq.empty()) {
        // TODO: get current node

        // TODO: early exit if reached end

        // TODO: skip outdated states

        // TODO: check 4 neighbors and relax edges
    }

    return -1;
}

int main() {
    vector<vector<int>> grid = {
        {0,1,9,9,9,9},
        {1,1,9,1,1,9},
        {9,1,9,1,9,9},
        {9,1,1,1,9,9},
        {9,9,9,1,1,1},
        {9,9,9,9,9,0}
    };

    pair<int,int> start = {0,0};
    pair<int,int> end = {5,5};

    cout << dijkstra(grid, start, end) << endl;
}
```
 