![image](https://github.com/last-child/CODING_TEST/assets/98595054/d14493c0-2564-40ff-a5d1-cc11c1dcabe2)
![image](https://github.com/last-child/CODING_TEST/assets/98595054/c3d73139-89fd-47a5-bc20-0d76af47d02b)

##

<br>   

```java
public class Main {

    public static void main(String[] args) throws IOException {

        // 정수 N을 입력받는다.
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        br.close();

        // 크기가 N+1인 배열에 0부터 N까지 저장한다.
        int[] number = new int[N+1];
        for(int i=2; i<=N; i++) {
            number[i] = i;
        }

        // 에라토스테네스의 체
        for(int i=2; i<=Math.sqrt(N); i++) {
            // 현재 원소가 0이면 이미 소수가 아닌 수로 판정되었으므로, 다음 원소로 넘어간다.
            if(number[i] == 0) continue;
            // i의 배수를 모두 0으로 변경한다.
            for(int j=2*i; j<=N; j+=i) {
                if(j % i == 0) number[j] = 0;
            }
        }

        // ArrayList에 N 이하의 소수들을 차례대로 저장한다.
        ArrayList<Integer> primeNumber = new ArrayList<>();
        for(int i=2; i<=N; i++) {
            if(number[i] != 0) primeNumber.add(number[i]);
        }

        int start = 0;
        int end = 0;
        int sum = 0;
        int count = 0;
        int size = 0;
        
        if(N > 1) {
            sum = primeNumber.get(0);
            size = primeNumber.size();
        }
        else sum = 1;

        // 두 포인터가 순회하면서 구간 합이 N과 같은지 비교한다. 
        while(start < size  && end < size) {
            if(sum < N) {
            	if(end < size-1) sum += primeNumber.get(++end);
            	else sum -= primeNumber.get(start++);
            } else if(sum > N) {
            	sum -= primeNumber.get(start++);
            } else {
                count++;
                sum -= primeNumber.get(start++);
            }
        }
        
        System.out.print(count);
        
    }
 
}
```

<br>   

#### 시간복잡도가 O(Nlog(logN))인 에라스토테네스의 체 알고리즘을 이용하여 N 이하의 소수들을 ArrayList에 저장한다.
#### 두 포인터 i, j를 모두 ArrayList의 0번째 원소에 위치시킨다.
#### 만일 구간 [i, j]의 합이 N보다 작고, j가 마지막 원소가 아니라면 j를 이동시키고 구간 합을 갱신한다.
#### 나머지 경우에는 i를 이동시키고 구간 합을 갱신한다. 단, 구간 합이 N과 같은 경우 count를 추가한다.

<br>   

##  

<br>   

#### 입력 값은 400만 이하이므로, 시간 복잡도가 O(N^2)인 이중 반복문을 사용하기 어렵다.

#### 
