| 작성자  |   날짜   | 언어    |
| ------- | --------- | ------- |
| 이유준   | 23.11.22 | c  |

# RGB 거리

 - https://www.acmicpc.net/problem/1149
  

## 소스 코드

```c
#include <stdio.h>

int main(){
    int count, ans;
    scanf("%d", &count);
    int house[count][3];
    int list [count][3];

    for(int i=0; i<count; i++){
        scanf("%d %d %d", &house[i][0], &house[i][1], &house[i][2]);
    }
    list[0][0] = house[0][0];
    list[0][1] = house[0][1];
    list[0][2] = house[0][2];

    for(int i=1; i<count; i++){
        for(int s=0; s<3; s++){
            if(s == 0){
                if(list[i-1][1] > list[i-1][2]){
                    list[i][0] = house[i][0] + list[i-1][2];
                }
                else{
                    list[i][0] = house[i][0] + list[i-1][1];
                }
            }
            else if(s == 1){
                if(list[i-1][0] > list[i-1][2]){
                    list[i][1] = house[i][1] + list[i-1][2];
                }
                else{
                    list[i][1] = house[i][1] + list[i-1][0];
                }
            }            
            else{
                if(list[i-1][1] > list[i-1][0]){
                    list[i][2] = house[i][2] + list[i-1][0];
                }
                else{
                    list[i][2] = house[i][2] + list[i-1][1];
                }
            }            
        }
    }
    ans = list[count-1][0];

    if(ans > list[count-1][1]){
        ans = list[count-1][1];
    }

    if(ans > list[count-1][2]){
        ans = list[count-1][2];
    }

    printf("%d", ans);

    return 0;
}
```

### 결과 화면

![image](https://github.com/gnbhub/20232_C_Algorithm/assets/77258639/7e7598ae-4843-4d62-949b-b0b04150836f)
![image](https://github.com/gnbhub/20232_C_Algorithm/assets/77258639/2060d774-9ee7-4b93-8d68-8bf96eb0f921)

