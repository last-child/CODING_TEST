![image](https://github.com/last-child/CODING_TEST/assets/98595054/6f5df967-0fd5-4180-a3c1-b3c00a0ce276)
![image](https://github.com/last-child/CODING_TEST/assets/98595054/fe238c03-93d6-4286-88e7-5de654f47461)

##
<br>   

```java
public class Main {

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int N = Integer.parseInt(br.readLine());
        int[] towerArray = new int[N+1];
        
        Stack<Tower> towerStack = new Stack<>();
        towerStack.push(new Tower(100000001,0));
        StringTokenizer st = new StringTokenizer(br.readLine());
        
        for(int i=1; i<=N; i++) {
            int h = Integer.parseInt(st.nextToken());
            if(towerStack.peek().height < h) {
                while(towerStack.peek().height < h) {
                    towerStack.pop();
                }
            }
            towerArray[i] = towerStack.peek().index;
            towerStack.push(new Tower(h, i));
        }
       
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
        for(int i=1; i<=N; i++) {
            bw.write(String.valueOf(towerArray[i]));
            if(i != N) bw.write(" ");
        }
        bw.flush();
        bw.close();
        br.close();
    }   
    
    static class Tower {
    	int height;
    	int index;
    	
    	Tower(int height, int index) {
    	    this.height = height;
    	    this.index = index;
    	}
    }
 
}
```

<br>   

##   

<br>   

#### 
