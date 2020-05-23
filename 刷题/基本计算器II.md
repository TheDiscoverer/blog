## 基本计算器II
- 题目链接：https://leetcode-cn.com/problems/basic-calculator-ii/
- Tag：无

## 题目详情
实现一个基本的计算器来计算一个简单的字符串表达式的值。字符串表达式仅包含非负整数，+， - ，*，/ 四种运算符和空格  。 整数除法仅保留整数。  
    
## 解法

使用两个栈s1和s2来分别记录数字和运算符。当遍历到运算符ch时如果优先级比s2的栈顶运算符优先级高，则取出s1中的两个运算符进行计算，否则ch入栈。其中需要注意的细节就是运算符的顺序、全部入栈后，要依次出栈运算。
```
class Solution {
    Map<Character, Integer> map = new HashMap<>();
    {
        map.put('+', 1);
        map.put('-', 1);
        map.put('*', 2);
        map.put('/', 2);
    }
    public int calculate(String s) {
        Stack<Integer> stackNum = new Stack<>();
        Stack<Character> stackChar = new Stack<>();
        s = s.replaceAll(" ","");
        int num = 0;
        int a, b, res = 0;
        for(int i = 0; i < s.length(); i++){
            char ch = s.charAt(i);
            if(ch <= '9' && ch >= '0'){
                num = num * 10 + ch - '0';
            }else {
                stackNum.push(num);
                num = 0;
                while(!stackChar.isEmpty() && map.get(stackChar.peek()) >= map.get(ch)) {
                    a = stackNum.pop();
                    b = stackNum.pop();
                    res = twoItemCalculate(b, a, stackChar.pop());
                    stackNum.push(res);
                }
                stackChar.push(ch);
            }
        }
        stackNum.push(num);
        while(!stackChar.isEmpty()) {
            a = stackNum.pop();
            b = stackNum.pop();
            res = twoItemCalculate(b, a, stackChar.pop());
            stackNum.push(res);
        }
        return stackNum.peek();
    } 
    public int twoItemCalculate(int a, int b, char ch) {
        //System.out.println(a+" "+b+" "+ch);
        if(ch == '+') {
            return a + b;
        }else if(ch == '-') {
            return a - b;
        }else if(ch == '*') {
            return a * b;
        }else {
            return a / b;
        }
    }
}
```