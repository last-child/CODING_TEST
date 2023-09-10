![image](https://github.com/last-child/CODING_TEST/assets/98595054/34aec850-8d6c-48e8-92c6-420b9a703538)

<BR>   

![image](https://github.com/last-child/CODING_TEST/assets/98595054/58d5a76f-b196-45e3-98ab-112a77bf9f96)

##

<br>   

```java
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        String S = br.readLine();
        double[] number = new double[N];
        
        for(int i=0; i<N; i++) {
            number[i] = Double.parseDouble(br.readLine());
        }
        
        Stack<Double> myStack = new Stack<>();
        char ch;
        double first, second;
        
        for(int i=0; i<S.length(); i++) {
        	ch = S.charAt(i);
            if(ch >= 65 && ch <= 90) {
                myStack.push(number[ch-65]);
            } else {
            	first = myStack.pop();
            	second = myStack.pop();
                switch(ch) {
                    case '+': myStack.push(second + first); break;
                    case '-': myStack.push(second - first); break;
                    case '*': myStack.push(second * first); break;
                    case '/': myStack.push(second / first);
                }
            }
        }
        
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        bw.write(String.valueOf(String.format("%.2f", myStack.peek())));
        bw.flush();
        bw.close();
        br.close();
    }
 
}
```

<br>   

##   

<BR>   

#### int형 간의 나눗셈은 몫에 해당하는 값을 반환하므로, 피연산자를 double형으로 입력받아야 한다.
#### 후위 표기식의 i번째 문자가 알파벳이면 상응하는 피연산자를 Stack에 push한다.
#### 연산자이면 stack에서 2개의 숫자를 꺼낸 후 그 숫자들 간의 연산 결과를 stack에 push한다.
#### 계산이 모두 끝나면 stack에 한 숫자만이 남아있는데, String.format( ) 메소드를 통해 소수점 둘째 자리까지 출력한다.
#### Math.round( ) 메소드를 이용하면 소수점을 shift해야 하며, 소수점 아래의 0이 생략될 수 있다.

<br>   

##

<br>   

#### 'A'의 유니코드가 65, 'Z'의 유니코드가 90임을 이용했지만, 유니코드로 변환하지 않아도 풀 수 있다.
