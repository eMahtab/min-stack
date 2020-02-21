# Min Satck
## https://leetcode.com/problems/min-stack

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

1. push(x) -- Push element x onto stack.
2. pop() -- Removes the element on top of the stack.
3. top() -- Get the top element.
4. getMin() -- Retrieve the minimum element in the stack.
 
```
Example:

MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```
## Approach
The question asks us to implement 4 functions and all of them should have constant runtime, which means no matter how large the input is, those 4 functions should always run in constant time.

Now we already know that, a Stack gives us `push(x)` , `pop()` and `peek()` functions, all of these 3 functions run in constant time.
So If we use Stack, the only additional thing we would have to implement is the `getMin()` function.

We will use one additional stack called the `min_stack` to keep track of the minimum element in the stack at any point of time, this will allow us to get the minimum element from the stack in constant time.

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
