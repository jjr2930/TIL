### 알고리즘

array의 각 element 중 divisor로 나누어 떨어지는 값을 오름차순으로 정렬한 배열을 반환하는 함수, solution을 작성해주세요.  
divisor로 나누어 떨어지는 element가 하나도 없다면 배열에 -1을 담아 반환하세요.

나의 해답
```
#include <string>
#include <vector>

using namespace std;

vector<int> solution(vector<int> arr, int divisor) {
    vector<int> answer;
    
    int size = arr.size();
    for(int i = 0; i < size; ++i)
    {
        if(arr[i] % divisor == 0)
        {
            answer.push_back(arr[i]);
        }
    }
    
    if(answer.size() == 0)
    {
        answer.push_back(-1);
    }
    else
    {
        int count = answer.size();
        for(int i = 0; i<count; ++i)
        {
            for(int j = i + 1; j<count; ++j)
            {
                if(answer[i] > answer[j])
                {
                    int temp = answer[i];
                    answer[i] = answer[j];
                    answer[j] = temp;
                }
            }
        }
    }
    return answer;
}
```



### 언리얼 블루프린트로 FPS만들기 5회차

괴물 개미와의 보스전을 치르는 느낌을 만들고 만들고 싶었다.
개미의 크기를 크게 키우고, 체력도 늘리고, 몇가지 공격 패턴을 추가해보았다.
개미의 공격은 다음과 같다.
몸통 박치기
미사일 발사

또한 플레이어에게 아이템을 습득하도록 하고 싶었다. 아이템은 10초마다 스폰지역에서 생성된다. 

아이템은 다음과 같다.
총알
체력 늘리기
이동속도 올리기

공통적인 동작을 구현하기 위해 BP_ItemBase를 만들어서 공통적인 부분을 구현하고, 특수한 부분만 확장할 수 있게 DoSomething이라는 함수를 만들어서 자식 블루프린트에서 구현할 수 있게 하였다. 구현한 것은 사용자가 overlap되었을 때 DoSomething을 하도록 구현하였다.



