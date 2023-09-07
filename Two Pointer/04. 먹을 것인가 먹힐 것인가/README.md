https://www.acmicpc.net/problem/7795

<br>   

![image](https://github.com/last-child/CODING_TEST/assets/98595054/a4714528-7b48-4a6e-af64-a563aa8be945)

<br>   

![image](https://github.com/last-child/CODING_TEST/assets/98595054/30668847-810f-450e-adca-dfbbe8d709ba)

<br>   

```java
public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int T = Integer.parseInt(br.readLine());
        int[] solution = new int[T];
        
        StringTokenizer st;
        int N, M, firstIndex, secondIndex, count;
        long[] A, B;
        
        for(int t=0; t<T; t++) {
            st = new StringTokenizer(br.readLine());
            N = Integer.parseInt(st.nextToken());
            M = Integer.parseInt(st.nextToken());
            A = new long[N];
            B = new long[M];
            firstIndex = N-1;
            secondIndex = M-1;
            count = 0;

            // A 배열에 N개의 원소를 저장한다.
            st = new StringTokenizer(br.readLine());
            for(int i=0; i<N; i++) {
                A[i] = Long.parseLong(st.nextToken());
            }

            // B 배열에 M개의 원소를 저장한다.
            st = new StringTokenizer(br.readLine());
            for(int i=0; i<M; i++) {
                B[i] = Long.parseLong(st.nextToken());
            }

            // 두 배열을 정렬한다.
            Arrays.sort(A);
            Arrays.sort(B);
            
            while(firstIndex >= 0 && secondIndex >= 0) {
                if(A[firstIndex] > B[secondIndex]) {
                    count += (secondIndex + 1);
                    firstIndex--;
                } else {
                    secondIndex--;
                }
            }
            
            solution[t] = count;
        }
        
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        for(int t=0; t<T; t++) {
            bw.write(String.valueOf(solution[t]));
            if(t<T-1) bw.newLine();
        }
        
        bw.flush();
        bw.close();
        br.close();
    
    }

}
```

<br>   

#### A 배열과 B 배열을 정렬하고, 각 배열의 마지막 원소에 포인터 i, j를 위치시킨다.
#### i번째 생물이 j번째 생물보다 크면, i번째 생물이 j번째보다 작은 생물들도 먹을 수 있다.
#### count에 j+1을 추가하고, A 배열의 i 포인터를 한 칸 전진시킨다.
#### i번째 생물이 j번째 생물보다 크지 않으면, i번째보다 작은 생물들도 j번째 생물을 먹을 수 없다.
#### j번째는 더 이상 비교하지 않아도 되므로, B 배열의 j 포인터를 한 칸 전진시킨다.
#### 한 포인터가 탐색을 마치면 반복문을 종료한다.
