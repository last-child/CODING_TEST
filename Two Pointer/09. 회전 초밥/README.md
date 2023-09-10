![image](https://github.com/last-child/CODING_TEST/assets/98595054/e87dd9ef-1945-4988-a362-b05e37a706a4)
![image](https://github.com/last-child/CODING_TEST/assets/98595054/d8551135-dc95-431c-9cdb-9560ab0a00c5)
![image](https://github.com/last-child/CODING_TEST/assets/98595054/e99a8042-a540-4cb4-ade8-af19c7e79466)

##

<br>   

```java
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());
        
        int N = Integer.parseInt(st.nextToken()); // 전체 초밥
        int d = Integer.parseInt(st.nextToken());
        int K = Integer.parseInt(st.nextToken()); // 고객 접시
        int c = Integer.parseInt(st.nextToken()); // 쿠폰 번호
        
        int[] sushi = new int[N];
        Map<Integer, Integer> dish = new HashMap<>();
        
        for(int i=0; i<N; i++) {
            sushi[i] = Integer.parseInt(br.readLine());
        }

        // 구간 [0, K-1]일 때 초밥을 종류별로 몇 개씩 먹었는지 HashMap에 저장한다.
        for(int i=0; i<K; i++) {
            if(dish.containsKey(sushi[i])) dish.replace(sushi[i], dish.get(sushi[i])+1);
            else dish.put(sushi[i], 1);
        }

        // 무료 초밥(C)은 1개 이상 제공되므로 HahsMap의 C 값을 하나 추가한다. 
        if(!dish.containsKey(c)) dish.put(c, 1);
        else dish.replace(c, dish.get(c)+1);
        
        int answer = dish.size();

        // 두 포인터를 한 칸씩 이동시키며 HashMap을 갱신한다.
        for(int i=0; i<N-1; i++) {
            if(dish.get(sushi[i]) == 1) dish.remove(sushi[i]);
            else dish.replace(sushi[i], dish.get(sushi[i])-1);
            
            if(dish.containsKey(sushi[(i+K)%N])) {
                dish.replace(sushi[(i+K)%N], dish.get(sushi[(i+K)%N])+1);
            }
            else dish.put(sushi[(i+K)%N], 1);
            answer = Math.max(answer, dish.size());
        }
        
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        bw.write(String.valueOf(answer));
        bw.flush();
        bw.close();
        br.close();
        
    }
 
}
```

<br>   

#### 손님이 초밥을 종류별로 몇개씩 먹었는지 확인하기 위해 <key, value> 형태의 HashMap을 이용한다.
#### 손님이 특정 초밥을 처음 먹는다면 HashMap의 put( ) 메소드를 이용하고, 또 먹는다면 replace( ) 메소드를 이용한다.
#### replace( ) 메소드로 초밥의 수를 갱신하려면 get( ) 메소드를 통해 기존 수를 확인할 필요가 있다.
#### 무료 초밥 C에 한해 value를 하나 추가한다.

<br>   

#### 두 포인터를 각각 0번째 원소와 K-1번째 원소에 위치시키고, 두 포인터를 한 칸씩 뒤로 이동시켜 구간을 갱신한다. 
#### x번째 원소가 구간에서 추출되면 HashMap의 x 값이 2 이상이면 replace( ) 메소드를 통해 하나 감소시키고, 
#### HashMap의 x 값이 1이면 remove( ) 메소드를 통해 HashMap에서 x를 제거한다.
#### x번째 원소가 구간에 추가되면 put( ) 메소드나 replace( ) 메소드를 통해 x 값을 갱신한다.
#### size( ) 메소드를 통해 초밥을 몇 종류나 먹었는지 확인한다.
#### 무료 초밥 C는 value가 하나 추가된 상태이므로, HashMap에서 제거되지 않는다.

<br>   

##  

<br>   

#### 크기가 d+1인 배열을 사용했더라면 HashMap을 이용하지 않아도 될 것 같다. 
