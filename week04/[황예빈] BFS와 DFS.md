| 작성자  |   날짜   | 언어    |
| ------- | --------- | ------- |
| 황예빈  | 23.11.07  | c++  |

# BFS와 DFS


 - https://www.acmicpc.net/problem/1260
  

### 풀이 과정  

STL 백터를 사용해 2차원 벡터를 만들어 그래프를 초기화 시켜준 후 
각 노드와 연결된 상태를 그래프로 표현 

방문할 노드를 큐에 넣고 
큐가 비어있지 않을 때까지 반복하면서 
1) 출력 pop
2) 해당 노드랑 연결된 노드를 방문한 적 없으면 큐에 push
3) 방문 체크 배열에 방문했다고 표시
4) 방문했으면 출력만하고 끝 

### 소스 코드

```
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>



using namespace std;


int n, m, v; // 노드, 간선, 탐색을 시작할 정점의 번호

vector<vector<int>> graph;
vector<int> bfs_chk;

void bfs(int now){ // 현재 방문 중인 노드를 argument로 받음 

    bfs_chk[now] = 1; // 현재 노드를 방문했다고 표시해주고 

    queue<int> q; // 큐를 선언 
    q.push(now); 

    while(!q.empty()){
        now = q.front(); // q에 있는 노드를 순차적으로 방문
        q.pop();
        cout << now << " " ;

        for (int i = 0; i < graph[now].size(); i ++){ // 해당 노드와 연결된 노드를 순차적으로 방문 

            int next = graph[now][i]; 
            if (!bfs_chk[next]) {
                bfs_chk[next] = 1;
                q.push(next); // 큐에다가 next 노드를 push 해줌 
            }// 방문을 안했으면 
            
        }
        
    }

}



int main(){

    cin >> n >> m >> v;

    graph.resize(n + 1); // (노드 개수 + 1 ) ^2 형태의 배열을 만듬 

    bfs_chk.assign(n+1 , 0); // 0 번에서 n+1 칸을 0으로 채운다

    for (int i = 0; i < m; i++){
        int a, b;
        cin >> a >> b;

        // 양방향 리스트 
        graph[a].push_back(b); // 배열 a행에 b를 추가
        graph[b].push_back(a); // 배열 b행에 a를 추가

    }

    // 한 노드와 연결된 다른 노드들을 오름 차순으로 만들어줌
    // 각 노드(= 정점을 순서대로 방문하기 위함) 
    // 3번이 4,1이랑 연결되어 있으면 1먼저 방문 후 4방문
    for (int i = 1 ; i<= n; i++){
        sort(graph[i].begin(), graph[i].end());
    }

    bfs(v);


}




```


### 결과 화면

<img width="441" alt="image" src="https://github.com/gnbhub/20232_C_Algorithm/assets/108808701/5153e1f8-aa5f-44de-9a79-2d3c849a1fe6">

