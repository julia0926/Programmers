## K번째 수
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.</br>
예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면
1. array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.
2. 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
3. 2에서 나온 배열의 3번째 숫자는 5입니다.

[ 해결 순서 ] </br>
1. 각 commands 배열의 순서대로 시작점 끝점 몇번째 꺼낼 값을 변수에 지정해 줌
2. 시작과 끝부분의 길이 -1 만큼 뽑아서 저장할 배열을 생성해 줌
3. 처음엔 for문을 통해 start~end까지 뽑아서 저장하고 count 값을 1씩 더하는 식으로 배열을 저장했으나,</br>
Arrays.copyOfRange() 메소드를 통해 배열의 시작과 끝을 정해 그대로 카피 할 수 있음.
4. 배열을 정렬하고 정렬된 배열에서 몇번째 꺼낼 건지 값을 리턴해줄 answer배열의 i번째에 저장


```java
import java.util.Arrays;
class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];
        for(int i=0;i<commands.length;i++){
            int start=commands[i][0];
            int end=commands[i][1];
            int pick=commands[i][2];
            int rearr[]=new int[end-(start-1)];//자른 배열의 길이
            int count=0;//자른 배열에 반복문하면서 돌릴때 인덱스
            
            rearr=Arrays.copyOfRange(array, start-1, end);
            //배열 자르고 복붙하기..
            Arrays.sort(rearr);
            answer[i]=rearr[pick-1];
        }
        return answer;
    }
}
```
