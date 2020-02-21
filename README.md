# Min Satck
## https://leetcode.com/problems/min-stack

# Implementation :

```java
class MinStack {
    Stack<Integer> s1, s2;
    /** initialize your data structure here. */
    public MinStack() {
        s1 = new Stack<Integer>();
        s2 = new Stack<Integer>();
    }
    
    public void push(int x) {
        s1.push(x);
        if(s2.isEmpty() || x <= s2.peek())
            s2.push(x);
    }
    
    public void pop() {
        int x = s1.pop();
        if(x == s2.peek())
            s2.pop();
    }
    
    public int top() {
        return s1.peek();
    }
    
    public int getMin() {
        return s2.peek();
    }
}
```

# References :
1. https://www.youtube.com/watch?v=nGwn8_-6e7w
2. https://www.youtube.com/watch?v=WxCuL3jleUA
3. https://leetcode.com/problems/min-stack/solution/
