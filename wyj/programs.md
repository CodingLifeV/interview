<!-- TOC -->

- [算法题](#算法题)
    - [**链表**](#链表)
        - [从尾到头打印链表](#从尾到头打印链表)
        - [在O(1)时间内删除链表节点](#在o1时间内删除链表节点)
        - [删除链表中重复的结点](#删除链表中重复的结点)
        - [**链表中倒数第k个结点**](#链表中倒数第k个结点)
        - [**链表中环的入口结点**](#链表中环的入口结点)
        - [合并二个排序的链表](#合并二个排序的链表)
        - [反转链表](#反转链表)
        - [**两个链表的第一个公共结点**](#两个链表的第一个公共结点)
    - [**树**](#树)
        - [**根据前序中序遍历结果重建二叉树**](#根据前序中序遍历结果重建二叉树)
        - [**给定二叉树其中的一个节点，返回中序遍历顺序的下一个结点**](#给定二叉树其中的一个节点返回中序遍历顺序的下一个结点)
        - [**树的子结构**](#树的子结构)
        - [**二叉树的镜像**](#二叉树的镜像)
        - [**对称二叉树**](#对称二叉树)
        - [**从上往下打印二叉树**](#从上往下打印二叉树)
        - [把二叉树打印成多行](#把二叉树打印成多行)
        - [按之字形顺序打印二叉树](#按之字形顺序打印二叉树)
        - [**二叉查找树的第K个节点**](#二叉查找树的第k个节点)
        - [**二叉树的深度**](#二叉树的深度)
        - [**平衡二叉树**](#平衡二叉树)
    - [**排序**](#排序)
        - [**归并排序**](#归并排序)
        - [**快速排序**](#快速排序)
        - [**堆排序**](#堆排序)
    - [**栈**](#栈)
        - [用二个栈实现队列](#用二个栈实现队列)
        - [**包含min函数的栈**](#包含min函数的栈)
        - [**输入二个序列，第一个序列是栈的压入序列，判断第二个序列是否为栈的弹出序列**](#输入二个序列第一个序列是栈的压入序列判断第二个序列是否为栈的弹出序列)
    - [数组](#数组)
        - [数组中重复的数字](#数组中重复的数字)
        - [二维数组中的查找，数组从左到右从上到下递增](#二维数组中的查找数组从左到右从上到下递增)
        - [旋转数组的最小数字](#旋转数组的最小数字)
        - [数组中出现次数超过一半的数字](#数组中出现次数超过一半的数字)
        - [调整数组顺序使奇数位于偶数前面](#调整数组顺序使奇数位于偶数前面)
    - [动态规划](#动态规划)
        - [连续子数组的最大和](#连续子数组的最大和)
        - [跳台阶](#跳台阶)
        - [变态跳台阶](#变态跳台阶)

<!-- /TOC -->

# 算法题
## **链表**
### 从尾到头打印链表

1. 改变链表结构（头插法）：

```java
public class Test {
    public ArrayList<Integer> print(ListNode listNode) {
        ListNode head = new ListNode(-1);
        while(listNode != null) {
            ListNode next = listNode.next;
            listNode.next = head.next;
            head.next = listNode;
            listNode  = next; 
        }
        
        head = head.next;
        ArrayList<Integer> ret = new ArrayList<>();
        while(head != null) {
            ret.add(head.value);
            head = head.next;
        }
        
        return ret;
    }
}
```

2. 不改变链表结构，栈
```java
public class Test {
    public ArrayList<Integer> print(ListNode listNode) {
        Stack<Integer> stack = new Stack<>()
        while(listNode != null) {
            stack.add(listNode.value);
            listNode = listNode.next;
        }
        
        ArrayList<Integer> ret = new ArrayList<>();
        //while(stack != null) {
        while(!stack.isEmpty()) {  
            //ret.add(head.value);
            //pop()方法
            ret.add(stack.pop())
        }
        
        return ret;
    }
}
```
3. 递归

### 在O(1)时间内删除链表节点

```java
public class Test {
    public ListNode deleteNode(ListNode head, ListNode deleteNode) {
        
        //加入特殊判断条件
        if(head == null || deleteNode ==null) {
            return null;
        }
        
        if (deleteNode.next != null) {
            deleteNode.val = deleteNode.next.val;
            deleteNode.next = deleteNode.next.next;
        } else {
            ListNode cur = head;
            while (cur.next != deleteNode) {
                cur = cur.next;
            }
            cur.next = null;
        }
        
        return head;
    }
}
```

### 删除链表中重复的结点
```java
public class Test {
    public ListNode deleteDuplication(ListNode head) {
        if(head == null || head.next == null) {
            return head;
        }
        ListNode cur = head;
        while(cur.next != null) {
            if(cur.val == cur.next.val) {
                cur.next = cur.next.next;
            } else {
                cur = cur.next
            }
        }
        
        return head;
    }
}
```
### **链表中倒数第k个结点**
```java
public class Test {
    public ListNode KthNode(ListNode listNode, int k) {
       //特殊条件
       if(listNode == null) {
           return null;
       }
       
       ListNode node1 = listNode, node2 = listNode;
       //int i = 1;
       //while(i++ < k && node2 != null) {
       //    node2 = node2.next;
       //}
       //if(node2 == null) {
       //    return null;
       //}
       
       while(node2 != null && k-- > 0) {
           node2 = node2.next;
       }
       // k > 0表示链表长度小于 k
       if(k > 0) {
           return null;
       }
       
       while(node2.next != null) {
           node1 = node1.next;
           node2 = node2.next;
       }
       
       return node1;
    }
}
```

### **链表中环的入口结点**

```java
public class Test {
    public ListNode getEntryNode(ListNode head) {
        if(head == null || head.next == null) {
            return null;
        }
        ListNode fast = head, slow = head;
        //while(fast.next.next != slow.next) {
        //    fast = fast.next.next;
        //    slow = slow.next;
        //}
        //使用do/while，fast和slow相遇
        do {
            fast = fast.next.next;
            slow = slow.next;
        } while(slow != fast)
        
        fast = head;
        while(fast != slow) {
            fast = fast.next;
            slow = slow.next;
        }
        
        return slow;
    }
}
```

### 合并二个排序的链表

1. 递归，不需要额外的辅助空间
```java
public class Test {
    public ListNode mergeSortedList(ListNode list1, ListNode list2) {
       //特殊条件分开了
       if(list1 == null) {
           return list2;
       }
       if(list2 == null) {
           return list1;
       }
       
       //不需要while循环判断list1和list2是否为空了
       if(list1.val < list2.val) {
            list1.next = mergeSortedList(list1.next, list2);
           return list1;
       } else {
           list2.next = mergeSortedList(list1, list2.next);
           return list2;
       }
       
    }
}
```
2. 迭代，需要额外的辅助空间
```java
public class Test {
    public ListNode mergeSortedList(ListNode list1, ListNode list2) {
       
       ListNode head = new ListNode(-1);
       //需要定义一个cur添加节点
       ListNode cur = head;
       while(list1 != null && list2 != null) {
           if(list1.val < list2.val) {
               cur.next = list1;
               list1 = list1.next;
           } else {
               cur.next = list2;
               list2 = list2.next;
           }
           cur = cur.next;
       }
       
       if(list1 != null) {
           cur.next = list1;
       }
       
       if(list2 != null) {
           cur.next = list2;
       }
       
       return head;
    }
}
```

### 反转链表
1. 头插法,迭代
```java
public class Test {
    public ListNode reverseList(ListNode list) {
        //不需要
        //if(list == null) {
        //    return null;
        //}

        ListNode head = new ListNode(-1);
        while(list != null) {
            ListNode next = list.next;
            list.next = head.next;
            head.next = list;
            list = next;
        }

        return head.next;

    }
}
```
2. 递归

### **两个链表的第一个公共结点**

```java
public class Test {
    public ListNode findFirstCommonNode(ListNode pHead1, ListNode pHead2){
        //if(pHead1 == null || pHead2 == null) {
        //    return null;
        //}

        ListNode p1 = pHead1, p2 = pHead2;
        while(p1 != p2) {
            p1 = (p1 == null) ? pHead2 : p1.next;
            p2 = (p2 == null) ? pHead1 : p2.next;
        }

        return p1;

    }
}
```

## **树**

### **根据前序中序遍历结果重建二叉树**
```java
public class Test {
    //map key-中序值 value-中序值的在数组的索引位置
    private Map<Integer,Integer> indexForInOrders = new HashMap<>();
    public TreeNode rebuildBinaryTree(int[] pre, int[] in){
        for(int i = 0; i < in.length - 1; i++) {
            indexForInOrders.put(in[i], i);
        }
        return rebuildBinaryTree(pre, 0, pre.length - 1, 0);
    }
    private TreeNode rebuildBinaryTree(
        int[] pre, int preL, int preR, int inL) {
            if(preL > preR) {
                return null;
            }

            TreeNode root = new TreeNode(pre[preL]);
            int index = indexForInOrders.get(root.val);
            int leftTreeSize = index - inL;

            root.left = rebuildBinaryTree(
                pre, preL+1, preL+leftTreeSize, inL
            );
            root.right = rebuildBinaryTree(
                pre, preL+leftTreeSize+1, preR, inL+leftTreeSize+1
            );

            return root;
    }
}
```
### **给定二叉树其中的一个节点，返回中序遍历顺序的下一个结点**
```java
public class Test {
   public TreeNode getNextNode(TreeNode pNode) {
       //右子树不为空，该节点的下一个节点是右子树的最左节点
       if(pNode.right != null) {
            TreeNode node = pNode.right;
            while(node.left != null) {
                node = node.left;
            }
            return node;
       } else {//否则，向上找第一个左链接指向的树，若该树包含该节点，返回该树的祖先节点
            while(pNode.next != null) {
                TreeNode parent = pNode.next;
                if(parent.left == pNode) {
                    return parent;
                }
                pNode = pNode.next;
            }
          
       }
       return null;
   }
}
```
### **树的子结构**
```java
public class Test {
   public boolean hasSubTree(TreeNode root1, TreeNode root2) {
       //特殊情况判断
       //if(root1 == null || root2 == null) {
       //    return null;
       //}
       return isSubTree(root1, root2) 
       || hasSubTree(root1.left, root2) 
       || hasSubTree(root1.right, root2);
   }
   private boolean isSubTree(TreeNode root1, TreeNode root2) {
       if(root1 == null) {
           return false;
       }
       if(root2 == null) {
           return true;
       }
       if(root1.val != root2.val) {
           return false;
       }

       return isSubTree(root1.left, root2.left) 
       && isSubTree(root1.right, root2.right);

   }
}
```

### **二叉树的镜像**

```java
public class Test {
    //判断是否为镜像
    public boolean isMirror(TreeNode root1, TreeNode root2) {
       if(root1 == null && root2 == null) {
           return true;
       }
       if(root1 == null || root2 == null) {
           return false;
       }
       if(root1.val != root2.val) {
           return false;
       }

       return isMirror(root1.left, root2.right) &&
       isMirror(root1.right, root2.left);   
    }

    //创建镜像
    public void createMirror(TreeNode root) {
        if(root == null) 
            return;
        
        swap(root);
        createMirror(root.left);
        createMirror(root.right);
    } 
    
    private void swap(TreeNode root) {
        TreeNode temp = root.right;
        root.right = root.left;
        root.left = temp;
    }
    
}
```

### **对称二叉树**
```java
public class Test {
   public boolean hasSymmetric(TreeNode root) {
       if(root == null) {
           return true;
       }
        return isSymmetric(root.left, root.right);
    }
    private boolean isSymmetric(TreeNode root1, TreeNode, root2) {
        if(root1 == null && root2 == null) {
            return true;
        }
        if(root1 == null || root2 == null) {
            return false;
        }
        if(root1.val != root2.val) {
            return false;
        }   
        return isSymmetric(root1.left, root2.right) &&
            isSymmetric(root1.right, root2.left);
    } 
}
```

### **从上往下打印二叉树**
```java
public class Test {
    public ArrayList<Integer> printBinaryTree(TreeNode pRoot) {
        if(pRoot == null) {
            return null;
        }
        
        Queue<TreeNode> queue = new LinkedList<>();
        ArrayList<Integer> ret = new ArrayList<>();
        queue.add(pRoot);
        while(!queue.isEmpty()) {
            int size = queue.size();
            while(size-- > 0) {
                //队列的poll()方法,返回并删除
                TreeNode t = queue.poll();
                if(t == null) {
                    continue;
                }
                ret.add(t);
                queue.add(t.left);
                queue.add(t.right);
            }
        }
        return ret;
    }
}
```

### 把二叉树打印成多行
```java
public class Test {
    public ArrayList<ArrayList<Integer>> printBinaryTree(TreeNode pRoot) {
        if(pRoot == null) {
            return null;
        }

        Queue<TreeNode> queue = new LinkedList<>();
        ArrayList<ArrayList<Integer>> ret = new ArrayList<>();
        queue.add(pRoot);
        while(!queue.isEmpty()) {
            ArrayList<Integer> line = new ArrayList<>();
            int size = queue.size();
            while(size-- > 0) {
                TreeNode t = queue.poll();
                if(t == null) {
                    continue;
                }
                line.add(t);
                queue.add(t.left);
                queue.add(t.right);
            }
            //加入对line的判空条件
            if(line.size() != 0) {
                ret.add(line);
            }     
        }
        return ret;
    }
}
```

### 按之字形顺序打印二叉树

```java
public class Test {
    public ArrayList<ArrayList<Integer>> printBinaryTree(TreeNode pRoot) {
        if(pRoot == null) {
            return null;
        }

        ArrayList<ArrayList<Integer>>() ret = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();
        booleam reverse = false;
        queue.add(pRoot);
        while(!queue.isEmpty()) {
            ArrayList<Integer>() line = new ArrayList<>();
            TreeNode t = queue.poll();
            int size = queue.size();
            while(size-- > 0) {
                if(t == null) {
                    continue;
                }
                line.add(t);
                queue.add(t.left);
                queue.add(t.right);
                //不能这样做，在按照多行打印的基础进行修改
                //if(odd % 2 == 0) {
                //    queue.add(t.right);
                //    queue.add(t.left);
                //} else {
                //    queue.add(t.left);
                //    queue.add(t.right);
                //}
            }
            if(reverse) {
                //集合工具类Collections.reverse()方法
                Collections.reverse(line);
            }
            reverse = !reverse;
            if(line != null) {
                ret.add(line);
            }
        }
        return ret;
    }
}
```

### **二叉查找树的第K个节点**

```java
public class Test{
    private TreeNode ret;
    private int cnt;
    //中序遍历的形式
    public TreeNode getKthNode(TreeNode pRoot, int k) {
        inOrder(pRoot, k);
        return ret;
    }
    private void inOrder(TreeNode pRoot, int k) {
        if(pRoot == null || cnt >= k) {
            return;
        }
        inOrder(pRoot.left, k);
        cnt++;
        if(k == cnt) {
            ret = pRoot;
            //return;
        }
        inOrder(pRoot.right);
    }
}
```

### **二叉树的深度**
```java
public class Test{
    public int getTreeDepth(TreeNode pRoot) {
        return pRoot == null ? 0 : 1 + Math.max(getTreeDepth(pRoot.left), getTreeDepth(pRoot.right));  
    }
}
```

### **平衡二叉树**
```java
public class Test{
    private boolean isBalance = true;
    public boolean isBalance(TreeNode pRoot) {
        getMaxDepth(pRoot);
        return isBalance;
    }
    private int getMaxDepth(TreeNode pRoot) {
        if(pRoot == null || !isBalance) {
            return 0;
        }
        int l = getMaxDepth(pRoot.left);
        int r = getMaxDepth(pRoot.right);
        if(Math.abs(l, r) > 1) {
            isBalance = false;
        } 
        return 1 + Math.max(l, r);
    }
}
```
## **排序**

### **归并排序**

**思想：**

归并排序是利用归并的思想实现的排序方法，采用经典的分治算法实现，这里的分就是把问题无序的数分解成一些小的组并使其有序，而治就是将这些有序的组进行有序的组合实现整个数列有序，其是通过归并实现的。

**代码实现：**

```java
public class Test {
    private int[] copyOfArr;
    public void sort(int[] arr) {
        copyOfArr = new int[arr.length];
        sort(arr, 0, arr.length - 1);
    }
    //sort()方法的作用其实在于安排多次merge()方法调用的正确顺序
    private void sort(int[] arr, int low, int high) {
        if(low >= high) {
            return;
        }
        int mid = low + (high - low) / 2;
        //分治思想，第一步：分
        sort(arr, low, mid);
        sort(arr, mid + 1, high);
        //第二步：治
        merge(arr, low, mid, high);
    
    }
    private void merge(int[] arr, int low, int mid, int high) {
        int i = low, j = mid + 1;
      
        for(int k = low; k <= high; k++) {
            copyOfArr[k] = arr[k];
        }

        for(int k = low; k <= high; k++) {
            if(i > mid)       arr[k] = copyOfArr[j++];
            else if(j > high) arr[k] = copyOfArr[i++];
            else if(copyOfArr[i] > copyOfArr[j]) {
                arr[k] = copyOfArr[j++]
            } 
            else {
                arr[k] = copyOfArr[i++];
            }
        }
    }
}
```
**时间复杂度：**

平均最好最坏都为O(N$\log$N)，证明如下：

>对于长度为 N 的数组，$2^n$ = N，k $\in$[0, n-1]，
第 k 层有 $2^k$ 个子数组，每个子数组的长度为$2^{n-k}$，归并最多需要 $2^{n-k}$ 次比较。因此每层的比较次数为 $2^k$ * $2^{n-k}$ = $2^n$，n 层总共为 n$2^n$ = N$\log$N


### **快速排序**

**思想：**

通过选取一个基准（理论上是可以任意取序列中的一个元素），通过基准将一个序列分割成独立的两部分，将小于基准的所有数据都和大于基准的另外一部分的所有数据分开，然后再按此方法对这两部分数据分别进行类似的排序，最终整个序列就可以实现有序，整个排序过程可以递归进行。

**代码实现：**
```java
public class Test {
    public void sort(int[] arr) {
        sort(arr, 0, arr.length - 1);
    }
    private void sort(int[] arr, int lo, int hi) {
        if(lo >= hi) {
            return;
        }
        int j = partition(arr, lo, hi);
        merge(arr, lo, j - 1);
        merge(arr, j + 1, hi);
    }
    private int partition(int[] arr, int lo, int hi) {
        int i = lo, j = hi + 1;
        int temp = arr[lo];
        while(true) {
            while(arr[++i] < temp);
            while(arr[--j] > temp);
            if(i >= j) break;
            swap(arr, i, j);
        }
        swap(arr, lo, j);
        return j;
    }
    private void swap(int[] arr, int i, int j) {
        int temp = arr[j];
        arr[j]   = arr[i];
        arr[i]   = temp;
    }
}
```
**时间复杂度：**

最好情况下每次都将数组对半分，最好平均为 O(N$\log$N)

最坏情况数组本身有序，最坏 O($N^2$)

### **堆排序**

**思想：**

分两个阶段：

* 堆的构造阶段：从右至左用sink()函数构造大顶堆
* 下层排序阶段：将堆中的最大元素删除，然后放入堆缩小后数组中空出的位置

**代码实现：**
```java
public class Test{
    public void sort(int[] arr) {
        int arrLength = arr.length - 1;
        //构造大顶堆
        for(int i = arrLength / 2 ; i >= 0; i--) {
            sink(arr, i, arrLength);
        }

        //下层排序阶段
        while(arrLength > 0) {
            swap(arr, 0, arrLength--);
            sink(arr, 0, arrLength);
        }
    }
    //下沉元素
    private void sink(int[] arr, int index, int arrLength) {
        while((2 * index + 1) <= arrLength) {
            int j = 2 * index + 1;
            if(j < arrLength && arr[j] < arr[j+1]) j++;
            if(arr[index] >= arr[j]) break;
            swap(arr, index, j);
        }
    }
    private void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i]   = arr[j];
        arr[j]   = temp;
    }
}
```

**时间复杂度：**

最好最坏平均情况下都为O(N$\log$N)

## **栈**

栈的常用方法：
* peek()：返回首元素不删除
* pop()：返回首元素且删除
* push()：压入元素
* isEmpty()：判空

### 用二个栈实现队列

```java
public class Test {
    private Stack<Integer> in;
    private Stack<Integer> out;
    public void push(int node) {
        in.push(node);
    }
    public void pop() {
        if(out.isEmpty()) {
            //if(in.isEmpty()) 
            //    throw new Exception("queue is Empty");
            while(!in.isEmpty()) {
                out.push(in.pop());
            }
        }

        if(out.isEmpty()) 
            throw new Exception("queue is Empty");

        return out.pop();
    }
}
```
### **包含min函数的栈**

```java
public class Test{
    private Stack<Integer> dataStack;
    private Stack<Integer> minStack;

    public void push(int node) {
        dataStack.push(node);
        minStack.push(minStack.isEmpty() ? node : Math.min(minStack.peek(), node))
    }
    public void pop() {
        dataStack.pop();
        minStack.pop();
    }
    public int min() {
        return minStack.peek();
    }
    public int pop() {
        return dataStack.peek();
    }

}
```

### **输入二个序列，第一个序列是栈的压入序列，判断第二个序列是否为栈的弹出序列**

```java
public class Test {
    private Stack<Integer> = new Stack<>();
    public boolean isPopSequence(int[] pushSequence, int[] popSequence) {
        int n = pushSequence.length;
        for(int pushIndex = 0, popIndex = 0; pushIndex < n; pushIndex++) {
            stack.push(pushSequence[pushIndex]);
            while(popIndex < n && !stack.isEmpty() && stack.peek() == popSequence[popIndex]) {
                stack.pop();
                popIndex++;
            }
        }
    }

    return stack.isEmpty();
}
```
## 数组

### 数组中重复的数字

```java
public class Test {
    //将值为 i 的元素调整到第 i 个位置上
    public boolean dulicate(int[] nums, int[] duplication) {
        //特殊条件：二个
        if(nums.length == 0 || nums == null) {
            return false;
        }

        for(int i = 0; i < nums.length; i++) {
            while(nums[i] != i) {
                if(nums[i] == nums[nums[i]]) {
                    duplication[0] = nums[i];
                    return true;
                }
                swap(nums, nums[i], i);
            }
        }
        return false;
    }

    private void swap(int[] nums, int i, int j) {
            int temp = nums[i]; 
            nums[i]  = nums[j];
            nums[j]  = temp; 
        }
}
```

### 二维数组中的查找，数组从左到右从上到下递增

**思想：**

类似二分查找

```java
public class Test {
    public boolean findTarget(int[][] matrix, int target) {
        if(matrix == null || matrix.length == 0 || matrix[0] == 0) {
            return false;
        }

        int row = matrix.length, col = matrix[0].length;
        int r = 0, c = col - 1;

        while(r <= row-1 && c >= 0) {
            if(target == matrix[r][c]) {
                return true;
            } else if(target > matrix[r][c]) {
                r++;
            } else {
                c--;
            }
        }
    }  
}
```

### 旋转数组的最小数字

**思想：**

二分查找

```java
public class Test {
    public int getMinNumber(int[] rotate) {
        if(rotate == null || rotate.length == 0) {
            return Integer.MIN_VALUE;
        }

        int l = 0, h = rotate.length - 1;
        while(l < h) {
            int m = l + (h - l) / 2;
            if(rotate[m] <= nums[h]) {
                h = m;
            } else {
                l = m + 1;
            }
        }

        return ratate[l];
    }
} 
```
### 数组中出现次数超过一半的数字

**思想：**

基于快排，数组中中位数肯定是出现超过一半的那一个数字

```java
public class Test {
    public int getMoreThanHalfNumber(int[] nums) {
        if(nums.length == 0 || nums == null) {
            return Integer.MAX_VALUE;
        }
        int mid = nums.length / 2;
        int index = patition(nums, 0, nums.length - 1);
        while(mid != index) {
            if(index > mid) {
                index = partition(nums, 0, index-1);
            } else {
                index = partition(nums, index+1, nums.length - 1);
            }
        }
    }

    private int partition(int[] nums, int lo, int hi) {
        int i = lo, j = hi + 1;
        int temp = nums[lo];
        while(true) {
            while(nums[++i] < lo);
            while(nums[--j] > lo);
            //快排 if 
            if(i >= j) break;
            swap(nums, i, j);
        }
        swap(nums, i, lo);
        return j;
    }

    private void swap(int nums, int i, int j) {
        int temp = nums[i];
        nums[i]  = nums[j];
        nums[j]  = temp;  
    }
}
```

### 调整数组顺序使奇数位于偶数前面

**思想：双指针**

```java
public class Test {
    pubic int[] reAdjustArr(int[] nums) {
        if(nums.length == null || nums.length == 0) {
            return null;
        }

        int i = 0, j = nums.length - 1;
        while(i < j) {
            if(nums[i] % 2 != 0) i++;
            if(nums[j] % 2 == 0) j++;
            swap(nums, i, j);
        }

        return nums;
    }
}
```





## 动态规划

### 连续子数组的最大和

**思想：**

DP[i] = max(dp[i-1]+num[i] , num[i])

```java
public class Test {
    public int getMaxSumOFSubArray(int[] nums) {
        if(nums == null && nums.length == 0) {
            return 0;
        }

        int max = nums[0], sum = nums[0];

        for(int i = 1; i < nums.length; i++) {
            sum = Math.max(nums[i], sum + nums[i]);
            if(sum > max) {
                max = sum;
            }
        }

        return max;
    }
}
```

### 跳台阶


### 变态跳台阶







