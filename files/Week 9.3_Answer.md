## Answer

### Reasoning

This maze includes many high-cost (`9`) traps that appear to offer short paths but are actually inefficient.

Dijkstra’s algorithm is appropriate because:

* All edge weights are non-negative.
* We want the minimum total cost, not the shortest number of steps.

Approach:

1. Use a **min-heap (priority queue)** storing `(cost, (row, col))`.
2. Initialize the start node with cost `0`.
3. Repeatedly extract the node with the smallest cost.
4. For each neighbor:

   * Compute new cost.
   * Relax the edge if a cheaper path is found.
5. Stop early when reaching the destination.

The optimal path avoids most `9`s by taking a longer but cheaper route through `1`s.

---

### Optimal Path (Conceptual)

```
S ↓ → ↓ ↓ → → ↓ → → E
```

---

### Completed Code

```cpp
int dijkstra(vector<vector<int>>& grid, pair<int,int> start, pair<int,int> end) {
    int n = grid.size();
    int m = grid[0].size();

    vector<vector<int>> dist(n, vector<int>(m, INT_MAX));
    priority_queue<State, vector<State>, greater<State>> pq;

    dist[start.first][start.second] = 0;
    pq.push({0, start});

    vector<int> dr = {-1, 1, 0, 0};
    vector<int> dc = {0, 0, -1, 1};

    while (!pq.empty()) {
        auto [cost, pos] = pq.top();
        pq.pop();

        int r = pos.first;
        int c = pos.second;

        if (make_pair(r,c) == end) return cost;

        if (cost > dist[r][c]) continue;

        for (int i = 0; i < 4; i++) {
            int nr = r + dr[i];
            int nc = c + dc[i];

            if (nr >= 0 && nr < n && nc >= 0 && nc < m) {
                int newCost = cost + grid[nr][nc];

                if (newCost < dist[nr][nc]) {
                    dist[nr][nc] = newCost;
                    pq.push({newCost, {nr, nc}});
                }
            }
        }
    }

    return -1;
}
```

---

### Final Output

```
9
```
 