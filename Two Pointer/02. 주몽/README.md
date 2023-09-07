https://www.acmicpc.net/problem/1940

<br>   

![image](https://github.com/last-child/CODING_TEST/assets/98595054/08079dd2-f464-4a95-b3bc-836c68dcd9c1)

![image](https://github.com/last-child/CODING_TEST/assets/98595054/893111ab-06e6-4b01-83ff-7d1c164d1b9b)

## 

<br>   

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.Arrays;
import java.util.StringTokenizer;

public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        // 두 정수 N, M을 입력받고, 크기 N인 배열을 선언한다.
        int N = Integer.parseInt(br.readLine());
        int M = Integer.parseInt(br.readLine());
        int[] intArray = new int[N];

        // 두 개의 포인터를 양끝으로 이동시킨다.
        int startIndex = 0;
        int endIndex = N-1;

        // 배열에 원소 N개를 저장한다.
        StringTokenizer st= new StringTokenizer(br.readLine());     
        for(int i=0; i<N; i++) {
            intArray[i] = Integer.parseInt(st.nextToken());
        }

        // 배열을 정렬하고, sum, count를 초기화한다.
        Arrays.sort(intArray);
        int sum = intArray[startIndex] + intArray[endIndex];
        int count = 0;

        // 두 개의 포인터를 이동시키며 배열을 탐색한다.
        while(startIndex < endIndex) {
            if(sum > M) {
                endIndex--;
            } else if(sum < M) {
                startIndex++;
            } else {
                count++;
                startIndex++;
                endIndex--;
            }
            sum = intArray[startIndex] + intArray[endIndex];
        }
        

        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        bw.write(String.valueOf(count));
        
        bw.flush();
        bw.close();
        br.close();
    
    }

}
```

<br>   

#### 두 포인터는 양 끝에서 시작하고, 서로 만날 때까지 탐색을 진행한다.
#### start 원소와 end 원소의 합이 목표치(M)보다 크다면 end 포인터를 앞으로 이동시킨다.
#### 두 원소의 합이 목표치(M)보다 작다면 start 포인터를 뒤로 이동시킨다.
#### 두 원소의 합이 목표치(M)와 같다면 count를 증가시키며, 두 포인터를 이동시킨다.

<br>   

## 

<br>   

#### 이번 문제에서 두 포인터를 바로 사용하면 이중 반복문을 사용해야 한다.
#### 하지만 정렬 알고리즘을 사용하면 시간 복잡도를 더욱 줄일 수 있다.

<br>   

#### 한 줄에 여러 개의 데이터를 입력받을 때 StringTokenizer의 nextToken()을 활용하고,
#### 한 줄에 하나의 데이터를 입력받을 때 BufferedReader의 readLine()만 활용해도 된다.

<br>   
   
