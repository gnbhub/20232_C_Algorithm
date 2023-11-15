| 작성자  |   날짜   | 언어    |
| ------- | --------- | ------- |
| 강선우  | 23.11.15  | c  |

# 


  

### 풀이 과정  


### 소스 코드

```c
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>

using namespace std;

vector<vector<int>> graph;
vector<int> visited_dfs, visited_bfs;

void dfs(int node) {
    visited_dfs[node] = 1;
    cout << node << " ";

    for (int i : graph[node]) {
        if (!visited_dfs[i]) {
            dfs(i);
        }
    }
}

void bfs(int start) {
    queue<int> q;
    visited_bfs[start] = 1;
    q.push(start);

    while (!q.empty()) {
        int current = q.front();
        q.pop();
        cout << current << " ";

        for (int i : graph[current]) {
            if (!visited_bfs[i]) {
                visited_bfs[i] = 1;
                q.push(i);
            }
        }
    }
}

int main() {
    int N, M, V;
    cin >> N >> M >> V;

    // 그래프 초기화
    graph.resize(N + 1);
    visited_dfs.resize(N + 1, 0);
    visited_bfs.resize(N + 1, 0);

    for (int i = 0; i < M; ++i) {
        int a, b;
        cin >> a >> b;
        graph[a].push_back(b);
        graph[b].push_back(a);
    }

    
    for (int i = 1; i <= N; ++i) {
        sort(graph[i].begin(), graph[i].end());
    }

    dfs(V);
    cout << "\n";

    bfs(V);
    cout << "\n";

    return 0;
}

```

### 결과 화면

