| 작성자  |   날짜   | 언어    |
| ------- | --------- | ------- |
| 이다민    | 23.11.15  | C  |

# Problem_Title

 - [문제 링크](https://www.acmicpc.net/problem/1260)
  

### 풀이 과정  



### 소스 코드

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

int sheet[1000][1000];
int visit[1000];
int stack[1000];
int top;

//첫째 줄에 정점의 개수 N(1 ≤ N ≤ 1,000), 간선의 개수 M(1 ≤ M ≤ 10,000), 탐색을 시작할 정점의 번호 V

void push(int v) {
    stack[top++] = v;
}

int pop() {
    return stack[--top];
}

void dfs(int n, int v) {
    printf("%d ", v);
    visit[v] = 1;
    push(v);

    while (top > 0) {
        int current = pop();
        for (int i = 1; i <= n; i++) {
            if ((sheet[current][i] == 1) && (visit[i] == 0)) {
                printf("%d ", i);
                push(i);
                visit[i] = 1;
            }
        }
    }
}

int main() {
    int n, m, v, x, y;
    scanf("%d %d %d", &n, &m, &v);

    for (int i = 0; i < m; i++) {
        scanf("%d %d", &x, &y);
        sheet[x][y] = 1;
        sheet[y][x] = 1;
    }
    dfs(n, v);

    return 0;
}

```

### 결과 화면
