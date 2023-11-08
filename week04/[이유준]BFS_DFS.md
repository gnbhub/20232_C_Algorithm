| 작성자  |   날짜   | 언어    |
| ------- | --------- | ------- |
| 이유준  | 23.11.08  | c    |

# BFS_DFS


 - https://www.acmicpc.net/problem/1260
  
### 소스 코드

```c
#include <stdio.h>

int sheet[1000][1000];
int visit[1000];
int queue[1000];
int front, rear;

void fqueue(int c){
    queue[front++] = c;
}

int rqueue(){
    return queue[rear++];
}

void bfs(int a, int c){
    printf("%d ", c);
    visit[c] = 1;
    fqueue(c);

    while(front != rear){
        int current = rqueue();
        for(int i = 1; i <= a; i++){
            if((sheet[current][i] == 1) && (visit[i] == 0)){
                printf("%d ", i);
                fqueue(i);
                visit[i] = 1;
            }
        }
    }
}

int main(){
    int a, b, c, x, y;
    scanf("%d %d %d", &a , &b, &c);

    for(int i = 0; i < b; i++){
        scanf("%d %d", &x, &y);
        sheet[x][y] = 1;
        sheet[y][x] = 1;
    }
    bfs(a, c);

    return 0;
}
```


### 결과 화면
![image](https://github.com/gnbhub/20232_C_Algorithm/assets/77258639/ab91a523-73c1-40fa-b766-ef082e1ee6d0)
