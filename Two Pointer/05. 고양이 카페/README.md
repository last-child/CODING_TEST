![image](https://github.com/last-child/CODING_TEST/assets/98595054/0bf075d9-f01e-4a53-b901-d693bfaa790b)
![image](https://github.com/last-child/CODING_TEST/assets/98595054/5b1738de-c869-4491-9416-06afea118ae3)

##   

<br>   

```java
public class Main {

    public static void main(String[] args) throws IOException {
    	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    	StringTokenizer st = new StringTokenizer(br.readLine());

        // 두 정수 N, M을 입력받는다. 
    	int N = Integer.parseInt(st.nextToken());
    	int K = Integer.parseInt(st.nextToken());
    	
    	int[] catArray = new int[N];
    	int start = 0;
    	int end = N-1;
    	int count = 0;

        // 배열에 원소를 저장한 다음 정렬한다.
    	st = new StringTokenizer(br.readLine());
    	for(int i=0; i<N; i++) {
    	    catArray[i] = Integer.parseInt(st.nextToken());      
    	}
    	Arrays.sort(catArray);

        // 양끝의 두 포인터가 만날 때까지 count를 갱신한다. 
    	while(start < end) {
    	    if(catArray[start] + catArray[end] > K) {
    	        end--;
    	    } else {
    	    	start++;
    	    	end--;
    	    	count++;
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

#### 배열을 정렬하고, 가장 가벼운 고양이와 가장 무거운 고양이에 두 포인터 start, end를 위치시킨다.
#### 두 무게의 합이 기준치(K)보다 크면 무게를 줄이기 위해 end를 한 칸 전진시킨다.
#### 두 무게의 합이 기준치(K)보다 크지 않다면 두 포인터를 한 칸씩 이동시키고, count를 하나 추가한다.
#### 두 포인터가 서로 만나면 탐색을 종료한다.
