![image](https://github.com/last-child/CODING_TEST/assets/98595054/8b6e1f8e-add6-4ab2-9755-8c76c8ff68f3)

<br>   

![image](https://github.com/last-child/CODING_TEST/assets/98595054/cc90d34b-cc67-45e3-ac3a-9115d8ea5b88)

##

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
        // 정수 N을 입력받고, 크기가 N인 배열을 선언한다.
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int[] number = new int[N];

        // 배열에 N개의 원소를 저장한다. 
        StringTokenizer st = new StringTokenizer(br.readLine());
        for(int i=0; i<N; i++) {
            number[i] = Integer.parseInt(st.nextToken());
        }

        // 두 포인터를 배열의 처음에 위치시킨다.
        int K = Integer.parseInt(br.readLine());
        int start = 0;
        int end = 0;
        long sum = number[0];
        long count = 0;

        // 두 포인터 구간의 합과 기준치(K)를 비교하며 반복문을 진행한다.
        while(start < N && end < N) {
            if(sum <= K) {
                if(end != N-1) sum += number[++end];
                else sum -= number[start++];
            } else {
            	count += (N-end);
            	sum -= number[start++];
            }  
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

##   

<br>   

#### 구간 [i, j]의 합이 k보다 크면 구간 [i, j+1], [i, j+2], ···, [i, N-1]의 합도 K보다 크다.
#### 이때 count에 (N-j)를 더하고, i를 한 칸 뒤로 이동시켜 다음 반복을 진행한다.

<br>   

#### 구간 [i, j]의 합이 k보다 크지 않을 때, j가 마지막 원소가 아니라면 j를 한 칸 뒤로 이동시키고 구간 합을 갱신한다.
#### j가 마지막 원소이면 i를 한 칸 뒤로 이동시키고 구간 합을 갱신한다.

<br>   

## 

<br>   

#### 만일 배열에 10만 개의 자연수가 있고, K가 1이라면 count는 100000!만큼 클 수 있다.
#### 따라서 count는 int가 아니라 long으로 선언했어야 한다.
