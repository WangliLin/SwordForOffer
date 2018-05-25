#### 最小的K个数

#### 题目
>  输入n个整数，找出其中最小的K个数。例如输入4,5,1,6,2,7,3,8这8个数字，则最小的4个数字是1,2,3,4,。

#### 思路 
-  全排序的话时间复杂度为：`O(nlogn)`
-  利用优先队列（大顶堆）的话时间复杂度为：`O(nlogk)`
-  有时间的话，Java的`PriorityQueue`的源码还是值得读一读的

#### 代码

```java
import java.util.*;
public class Solution {
    public ArrayList<Integer> GetLeastNumbers_Solution(int [] input, int k) {
        ArrayList<Integer> result = new ArrayList<Integer>();
        
        int len = input.length;
        if (k > len || k == 0) {
            return result;
        }
        
        PriorityQueue<Integer> maxHeap = new PriorityQueue<Integer>(k, new Comparator<Integer>(){
            
            @Override
            public int compare(Integer o1, Integer o2) {
                return o2.compareTo(o1);
            }
            
        });
        
        for (int i = 0; i < len; i++) {
            if (maxHeap.size() < k) {
                maxHeap.offer(input[i]);
            } else {
                if (maxHeap.peek() > input[i]) {
                    maxHeap.remove();
                    maxHeap.offer(input[i]);
                }
            }
        }
        
        for (Integer num: maxHeap) {
            result.add(num);
        }
        
        return result;
    }
}
```
