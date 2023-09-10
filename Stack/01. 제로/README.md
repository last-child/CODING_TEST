![image](https://github.com/last-child/CODING_TEST/assets/98595054/21475390-f3c5-4a9a-92b2-2d173f848bd7)
<br>   
![image](https://github.com/last-child/CODING_TEST/assets/98595054/ac76c5a9-f13e-43df-ab25-c7caf3487607)

##  

<br>   

```java
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.util.Stack;

public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int K = Integer.parseInt(br.readLine());
        
        Stack<Integer> money = new Stack<>();
        int m;
        long sum = 0;
        
        for(int i=0; i<K; i++) {
            m = Integer.parseInt(br.readLine());
            if(m != 0) {
                money.push(m);
            } else {
                money.pop();
            }
        }
        
        while(!money.isEmpty()) {
            sum += money.pop();
        }
        
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        bw.write(String.valueOf(sum));
        bw.flush();
        bw.close();
        br.close();
        
    }
 
}
```

<br>   

##   

<br>   

#### i번째 원소가 0이 아니면 해당 원소를 stack에 넣는다.
#### i번째 원소가 0이면 stack의 top 원소를 추출한다.
#### 반복문을 마치면 stack에 남아있는 원소들을 모두 더한 sum을 구한다.
