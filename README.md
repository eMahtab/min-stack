# Min Satck
## https://leetcode.com/problems/min-stack

# Implementation :

```java
class MinStack {
   private Stack<Integer> stack = new Stack<>();
   private Stack<Integer> minStack = new Stack<>();
  
   public void push(int x) {
        stack.push(x);
        if (minStack.isEmpty() || x <= minStack.peek()) {
            minStack.push(x);
        }
    }
     
   public void pop() {
        if (stack.peek().equals(minStack.peek())) {
            minStack.pop();
        }
       stack.pop();
   }
   
   public int top() {
        return stack.peek();
   }
 
   public int getMin() {
        return minStack.peek();
   }
}

```

# References :
1. https://www.youtube.com/watch?v=nGwn8_-6e7w
2. https://www.youtube.com/watch?v=WxCuL3jleUA
3. https://leetcode.com/problems/min-stack/solution/
