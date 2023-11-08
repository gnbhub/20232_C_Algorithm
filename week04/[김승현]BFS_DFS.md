| 작성자  |   날짜   | 언어    |
| ------- | --------- | ------- |
| 김승현    | 23.11.08  | C  |

# Problem_Title

 - [문제 링크](https://www.acmicpc.net/problem/1260)
  

### 풀이 과정  



### 소스 코드

``` C
#include <stdio.h>

int arr[1001][1001] = {0,};
int visited[1001] = {0,};
int n,m,v; // n== 노드, m == 간선, v == 시작 노드

void dfs(int start_node);


int main()
{
    scanf("%d %d %d",&n,&m,&v);

    int s_n,f_n;
    
    /////////////////////////////노드 세팅/////////////////////////////////////
    
    for(int i=0; i<m; i++) {
        scanf("%d %d",&s_n,&f_n);
        arr[s_n][f_n] = 1;
        arr[f_n][s_n] = 1;
    }
    
    
    /////////////////////////////dfs///////////////////////////////////
    
    dfs(v);
    printf("\n");
    
    //////////////////////////큐 세팅////////////////////////////
    for(int i=0; i<=n; i++) visited[i] = 0;
    int queue[1001] = {0,};//노드 갯수만큼
    int front = 0;
    int back = 0; // front == back is empty
    
    //추가할 때는 back위치에 추가 후 back++
    queue[back++] = v;
    visited[v] = 1; // 이노드를 저장했다고 기록
    
    /////////////////////////bfs////////////////////////////////////
    
    int search_node;
    
    while(1) {
        
        printf("%d ",queue[front]); // 이 노드를 방문했다고 출력
        
        search_node = queue[front++]; // queue pop
       
        for(int i=1; i<=n; i++) { // 1부터 방문할 수 있는 node queue에 저장
            if(arr[search_node][i] == 1 && visited[i] == 0) {// 방문할 수 있는 노드여야하고, 그 노드가 저장이 안되어있어야한다
                queue[back++] = i;
                visited[i] = 1;
            }
        }    
        
        if(front==back) break; //queue가 empty면 break
     
    }
    
/////////////////////////////////dfs/////////////////////////////////////////////////////////





////////////////////////////////////////////////////////////////////////////////////////



    return 0;
}


void dfs(int start_node) {
    visited[start_node] = 1;
    printf("%d ",start_node);
    
    for(int i=1; i<=n; i++) {
        if(arr[start_node][i] == 1 && visited[i] == 0) dfs(i);
    }
    
}








```

### 결과 화면
