# Min Stack
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
## Approach :
The question asks us to implement 4 functions and all of them should have constant runtime, which means no matter how large the input is, those 4 functions should always run in constant time.

Now we already know that, a Stack gives us `push(x)` , `pop()` and `peek()` functions, all of these 3 functions run in constant time.
So If we use Stack, the only additional thing we would have to implement is the `getMin()` function.

We will use one additional stack called the `minStack` to keep track of the minimum element in the stack at any point of time, this will allow us to get the minimum element from the stack in constant time.

# Implementation 1 : getMin() => O(n) (Note, getMin() doesn't run in constant time) 😉

```java
class MinStack {
    Stack<Integer> stack = new Stack<>();
    
    public void push(int x) {
        stack.push(x);
    }
    
    public void pop() {
        stack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
        Stack<Integer> s = new Stack<>();
        int min = Integer.MAX_VALUE;
        while(!stack.isEmpty()) {
            int x = stack.pop();
            min = Math.min(min, x);
            s.push(x);
        }
        while(!s.isEmpty()) {
            stack.push(s.pop());
        }
        return min;
    }
}
```

# Implementation 2 : getMin() => O(1)

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

### Key Points :
1. Don't forget to update the minStack on both push and pop operations on the main stack
2. Pitfall : We push an element to minStack, if the element is less than **or equal to** `min_stack.peek()` 

As a side note, in Java calling `push()`, `pop()` and `peek()` returns the element, but in this question for `push()` and `pop()` the return type is void. And also calling  `pop()` and `peek()` on an empty stack results in `EmptyStackException`

# References :
1. https://www.youtube.com/watch?v=nGwn8_-6e7w
2. https://www.youtube.com/watch?v=WxCuL3jleUA
3. https://leetcode.com/problems/min-stack/solution/
