![image](https://github.com/last-child/CODING_TEST/assets/98595054/2cb70501-caf8-4dda-a183-1f43a1d7d130)
![image](https://github.com/last-child/CODING_TEST/assets/98595054/46d3880d-f3d1-47d8-a317-2fd00e2ee3c3)

##   

<br>    

```java
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String word = br.readLine();
        
        Stack<Integer> mole = new Stack<>();
        
        for(int i=0; i<word.length(); i++) {
            switch(word.charAt(i)) {
                case 'H': mole.push(1); break;
                case 'C': mole.push(12); break;
                case 'O': mole.push(16); break;
                case '(': mole.push(0); break;
                case ')': 
                    int temp = 0;
                    while(!mole.peek().equals(0)) {
                        temp += mole.pop();
                    }
                    mole.pop(); // 0
                    mole.push(temp);
                    break;
                default: mole.push(mole.pop() * (word.charAt(i)-48));
            }
        }
        
        int sum = 0;
        
        while(!mole.isEmpty()) {
            sum += mole.pop();
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

#### 알파벳이면 상응하는 화학식량을 stack에 push하고, '('라면 0을 stack에 push한다.
#### 숫자라면 stack의 탑 원소를 꺼낸 다음 두 숫자의 곱을 stack에 push한다.
#### ')'라면 stack에서 0이 나올 때까지 원소들을 꺼내어 계속 더하고, 0이 나오면 그 합을 push한다.
#### 최종적으로 stack에 남아있는 화학식량을 모두 꺼내어 더한 값을 구한다.

<br>   

##
<br>   

#### 화학식의 i번째 문자가 숫자일 때 0의 유니코드를 이용했다. 유니코드가 아닌 '0'을 사용했어야 하는데.
