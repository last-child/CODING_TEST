![image](https://github.com/last-child/CODING_TEST/assets/98595054/edd4f409-fb6b-4421-b2d9-5ae7fe8178ad)

![image](https://github.com/last-child/CODING_TEST/assets/98595054/b0868c32-2208-47ff-bfaa-fe5e8745031a)

![image](https://github.com/last-child/CODING_TEST/assets/98595054/6b1e47ac-b65c-4c46-9d20-ae457f993154)

<br>   

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
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int T = Integer.parseInt(br.readLine());
        int[] countArray = new int[T];
        
        StringTokenizer st;
        int N, M, K, sum, count;
        int[] houseArray;
        
        for(int s=0; s<T; s++) {
            // 세 정수 N, M, K를 입력받는다. 
            st = new StringTokenizer(br.readLine());
            N = Integer.parseInt(st.nextToken());
            M = Integer.parseInt(st.nextToken());
            K = Integer.parseInt(st.nextToken());

            // 크기가 N+M-1인 배열을 선언하고, sum과 count를 초기화한다.
            houseArray = new int[N+M-1];
            sum = 0;
            count = 0;

            // 배열에 원소들을 저장한다.
            st = new StringTokenizer(br.readLine());
            for(int i=0; i<N; i++) {
            	houseArray[i] = Integer.parseInt(st.nextToken());
            }
            
            for(int i=0; i<M-1; i++) {
            	houseArray[i+N] = houseArray[i]; 
            }

            // 연속적으로 훔칠 횟수만큼 가격을 더한다.
            for(int i=0; i<M; i++) {
            	sum += houseArray[i];
            }

            // 최초의 sum이 K보다 작으면 count를 추가한다.
            if(sum < K) count++;

            // 두 포인터를 한 칸씩 뒤로 이동시키며 sum을 갱신하고, K와 비교한다.
            for(int i=0; i<N-1; i++) {
            	if(N==M) break;
            	sum -= houseArray[i];
            	sum += houseArray[i+M];
            	if(sum < K) count++;
            }
            
            countArray[s] = count;
        }
        
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        for(int t=0; t<T; t++) {
            bw.write(String.valueOf(countArray[t]));
            bw.newLine();
        }
        
        br.close();
        bw.flush();
        bw.close();

    }

}
```

<br>   

##   

<br>   

#### N번째 집과 1번째 집은 서로 연결되었으므로, 원형으로 구성되었다고 할 수 있다.
#### 도둑은 M번 연속으로 훔치기 때문에, N번째 집을 훔치기 시작할 때 N+M-1번째 집까지 훔친다.
#### 따라서 크기가 N+M-1인 배열에 N개의 원소들을 저장하고, 1번부터 M-1번 원소를 또 저장한다.

<br>   

#### start 포인터를 0번째 원소, end 포인터를 M-1번째 원소에 위치시키고 구간 합을 계산한다.
#### 구간 합이 기준치(K)보다 작으면 count를 추가한다.
#### 두 포인터를 한 칸씩 뒤로 이동시키며 구간 합을 갱신하고, 구간 합이 K보다 작은지 확인한다.
#### end 포인터가 배열의 마지막 원소에 위치할 때까지 반복문을 진행한다.

<br>   

##   

<br>   

#### N과 M이 같은 경우, 즉 도둑이 마을의 모든 집을 훔칠 경우 반복문을 진행하면 안 된다.

<br>   

##  

<br>   

#### 크기가 N인 배열을 활용할 경우, 반복문에서 구간 합을 갱신할 때 % 연산을 이용해야 한다.
