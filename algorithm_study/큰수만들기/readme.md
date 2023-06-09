for문으로 앞의 숫자와 뒤의 숫자를 비교하여 앞의 숫자가 더 작을 경우 number에서 제거하고 count를 1 증가시켰다.    
k개의 수를 제거해야하므로 이를 k번 반복해야한다.

앞의 숫자가 뒤의 숫자보다 작은게 없는 경우(ex: "4321")를 고려하지 않아서 테스트케이스 12번에서 오류가 발생하였다.    
count가 k와 다른 경우(숫자를 덜 삭제한 경우)에는 남은 개수만큼 삭제한다.

count는 숫자가 제거된 횟수이다. k는 제거해야하는 총 갯수이다.    
즉, 제거해야하는 개수에서 이미 제거한 count번을 제외한다.

```C++
#include <string>
#include <vector>

using namespace std;

string solution(string number, int k) 
{
    int count = 0;
    for(int i = 1; i <= k; i++) {   
        for(int j = 0; j < number.size() - 1; j++) {
           if(number[j] < number[j + 1]) {
                number.erase(j, 1);
                count++;
                break;
           }
        }
        if(count == k) break;
    }
    
    // 숫자가 덜 제거된 경우 추가로 제거
    if(count != k) {
        number.erase(number.size() - (k - count), k - count);
    }
    return number;
}
```
