https://www.acmicpc.net/problem/2559

<br>   

![image](https://github.com/last-child/CODING_TEST/assets/98595054/c0078aa7-bd38-43ed-b956-422523cfd56d)

<br>   

![image](https://github.com/last-child/CODING_TEST/assets/98595054/d8c7b64d-26df-46d7-8f7a-a25a2aec7e1b)

##

<br>   

```java
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        
        // 첫번째 줄의 N, K을 입력받고, 크기가 N인 배열을 초기화한다.
        StringTokenizer st = new StringTokenizer(br.readLine());
        int N = Integer.parseInt(st.nextToken());
        int K = Integer.parseInt(st.nextToken());
        int[] intArray = new int[N];

        // sum, startIndex, endIndex 초기화한다. 
        int sum = 0;
        int startIndex = 0;
        int endIndex = K-1;

        // 배열에 N개의 원소들을 저장한다.
        st = new StringTokenizer(br.readLine());
        for(int i=0; i<N; i++) {
            intArray[i] = Integer.parseInt(st.nextToken());
        }

        // 1일차부터 k일차까지 온도들의 합을 구한다.
        for(int i=0; i<K; i++) {
            sum += intArray[i];
        }
        int ans = sum;

        // 두 포인터를 순회시키며 최대합을 갱신한다.
        while(endIndex < N-1) {
            sum -= intArray[startIndex++];
            sum += intArray[++endIndex];
            if(sum > ans) ans = sum;
        }

        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        bw.write(String.valueOf(ans));
        bw.flush();
        bw.close();
        br.close();
    
    }

}
```

<br>   

#### sum에서 startIndex가 가리키는 값을 빼고, 두 포인터를 한칸씩 뒤로 이동시킨다.
#### sum에 endIndex가 새로 가리키는 값을 더한다. 
#### 최대합 ans 값과 현재합 sum 값을 비교한다. 만일 sum 값이 크다면 ans 값을 sum 값으로 변경한다.
#### endIndex가 마지막 원소에 다다르면 반복문을 종료하고, ans 값을 출력한다.

<br>   

## 

<br>   

#### 처음에 최대합을 0이 아닌 가장 낮은 경우인 -100*K로 설정하였다.
#### 모든 날의 온도가 음수이면 최대합도 음수여야 하는데, 0이 되버리니까.
#### 하지만 이것도 틀렸다. 만일 N=K일 경우 반복문이 진행되지 않으므로 최종 결과가 -100*K가 되버린다.
#### 결국 처음에는 최대합을 1일차부터 K일차까지 온도합으로 초기화하여야 한다.

<br>   

## 

<br>   

#### Math.max( ) 메소드를 사용하는 건 어떨까?
