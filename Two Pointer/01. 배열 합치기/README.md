https://www.acmicpc.net/problem/11728

<br>   

![image](https://github.com/last-child/CODING_TEST/assets/98595054/28efd198-7ad2-472a-8269-e5a39446f068)

<br>   

![image](https://github.com/last-child/CODING_TEST/assets/98595054/31165c88-9989-4efc-b912-1765ec64ae4f)

<br>   
<br>   

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        int N = Integer.parseInt(st.nextToken());
        int M = Integer.parseInt(st.nextToken());

        int[] firstArray = new int[N];
        int[] secondArray = new int[M];
        int[] thirdArray = new int[N+M];

        int firstIndex = 0;
        int secondIndex = 0;
        int thirdIndex = 0;

        st = new StringTokenizer(br.readLine());

        for(int i=0; i<N; i++) {
            firstArray[i] = Integer.parseInt(st.nextToken());
        }

        st = new StringTokenizer(br.readLine());

        for(int i=0; i<M; i++) {
            secondArray[i] = Integer.parseInt(st.nextToken());
        }

        while(thirdIndex < N+M) {
            if(firstIndex == N && secondIndex < M) {
                thirdArray[thirdIndex++] = secondArray[secondIndex++];
            } else if(firstIndex < N && secondIndex == M) {
                thirdArray[thirdIndex++] = firstArray[firstIndex++];
            } else {
                if(firstArray[firstIndex] >= secondArray[secondIndex]) {
                    thirdArray[thirdIndex++] = secondArray[secondIndex++];
                } else {
                    thirdArray[thirdIndex++] = firstArray[firstIndex++];
                }
            }
        }

        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        for(int i=0; i<thirdArray.length; i++) {
            bw.write(thirdArray[i] + " ");
        }

        br.close();
        bw.flush();
        bw.close();
    }	
	
}
```

<br>   

#### 두 배열의 인덱스를 투 포인터로 지정하였다. 두 배열의 원소를 비교하면서 작은 원소를 세번째 배열에 저장한다.
#### 작은 원소에 속한 배열의 포인터를 이동시키고, 다음 반복을 진행한다.
#### 반복문을 진행하다 보면 한 포인터의 이동이 끝나게 되어 있다. 
#### 이때 다른 배열의 나머지 원소들을 순서대로 세번째 배열에 저장한다.
#### 두 포인터가 모두 순회를 마칠 때, 즉 세번째 배열이 꽉 차 있으면 반복문을 종료시킨다.

<br>   

##  

<br>

#### Arrays.sort()를 이용하는 경우도 있었다. 다만 시간복잡도가 O(nlogn)임을 명심하자.
#### 세번째 배열에 저장하지 않고 ArrayList나 StringBuilder에 덧붙이는 풀이도 있었다.

<br>   
