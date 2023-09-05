https://www.acmicpc.net/problem/11728

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
