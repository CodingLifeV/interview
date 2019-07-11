<!-- TOC -->

- [算法题](#算法题)
  - [**一、链表**](#一链表)
    - [从尾到头打印链表](#从尾到头打印链表)
    - [在 O(1)时间内删除链表节点](#在-o1时间内删除链表节点)
    - [删除链表中重复的结点](#删除链表中重复的结点)
    - [**链表中倒数第 k 个结点**](#链表中倒数第-k-个结点)
    - [**链表中环的入口结点**](#链表中环的入口结点)
    - [合并二个排序的链表](#合并二个排序的链表)
    - [反转链表](#反转链表)
    - [**两个链表的第一个公共结点**](#两个链表的第一个公共结点)
  - [**二、树**](#二树)
    - [**根据前序中序遍历结果重建二叉树**](#根据前序中序遍历结果重建二叉树)
    - [**给定二叉树其中的一个节点，返回中序遍历顺序的下一个结点**](#给定二叉树其中的一个节点返回中序遍历顺序的下一个结点)
    - [**树的子结构**](#树的子结构)
    - [**二叉树的镜像**](#二叉树的镜像)
    - [**对称二叉树**](#对称二叉树)
    - [**从上往下打印二叉树**](#从上往下打印二叉树)
    - [把二叉树打印成多行](#把二叉树打印成多行)
    - [按之字形顺序打印二叉树](#按之字形顺序打印二叉树)
    - [**二叉查找树的第 K 个节点**](#二叉查找树的第-k-个节点)
    - [**二叉树的深度**](#二叉树的深度)
    - [**平衡二叉树**](#平衡二叉树)
  - [**三、排序**](#三排序)
    - [**归并排序**](#归并排序)
    - [**快速排序**](#快速排序)
    - [**堆排序**](#堆排序)
    - [数组中前一个数字大于后面一个数字构成逆序对，求数组中的逆序对个数](#数组中前一个数字大于后面一个数字构成逆序对求数组中的逆序对个数)
    - [数组中出现次数超过一半的数字](#数组中出现次数超过一半的数字)
    - [最小的 k 个数](#最小的-k-个数)
    - [数据流中的中位数](#数据流中的中位数)
  - [**四、栈**](#四栈)
    - [用二个栈实现队列](#用二个栈实现队列)
    - [**包含 min 函数的栈**](#包含-min-函数的栈)
    - [**输入二个序列，第一个序列是栈的压入序列，判断第二个序列是否为栈的弹出序列**](#输入二个序列第一个序列是栈的压入序列判断第二个序列是否为栈的弹出序列)
  - [五、数组](#五数组)
    - [数组中重复的数字](#数组中重复的数字)
    - [二维数组中的查找，数组从左到右从上到下递增](#二维数组中的查找数组从左到右从上到下递增)
    - [旋转数组的最小数字](#旋转数组的最小数字)
    - [数组中出现次数超过一半的数字](#数组中出现次数超过一半的数字-1)
    - [调整数组顺序使奇数位于偶数前面](#调整数组顺序使奇数位于偶数前面)
    - [把数组中的所有数字拼接起来，排成最小的数](#把数组中的所有数字拼接起来排成最小的数)
    - [数组中前一个数字大于后面一个数字构成逆序对，求数组中的逆序对个数](#数组中前一个数字大于后面一个数字构成逆序对求数组中的逆序对个数-1)
    - [数组中只出现一次的数字](#数组中只出现一次的数字)
    - [递增数组中找和为 S 的二个数，若有多个， 输出乘积最小者](#递增数组中找和为-s-的二个数若有多个-输出乘积最小者)
    - [和为 S 的连续正数序列](#和为-s-的连续正数序列)
    - [滑动窗口中的最大值](#滑动窗口中的最大值)
    - [5 张扑克牌能否组成顺子](#5-张扑克牌能否组成顺子)
  - [六、动态规划](#六动态规划)
    - [**连续子数组的最大和**](#连续子数组的最大和)
    - [最长不含重复字符的子字符串](#最长不含重复字符的子字符串)
    - [**m \* n 的棋盘上拿礼物，求礼物的最大价值**](#m--n-的棋盘上拿礼物求礼物的最大价值)
    - [剪绳子，使得每段的长度乘积最大](#剪绳子使得每段的长度乘积最大)
    - [变态跳台阶](#变态跳台阶)
    - [求按从小到大的顺序的第 N 个丑数，丑数只包含因子 2、3 和 5](#求按从小到大的顺序的第-n-个丑数丑数只包含因子-23-和-5)
  - [七、贪心](#七贪心)
    - [**股票的最大利润**](#股票的最大利润)
  - [八、递归](#八递归)
    - [**斐波那契数列**](#斐波那契数列)
    - [跳 n 级台阶总共的跳法](#跳-n-级台阶总共的跳法)
    - [用 2 _ 1 的小矩形不重叠的覆盖 2 _ n 的大矩形](#用-2-_-1-的小矩形不重叠的覆盖-2-_-n-的大矩形)
    - [变态跳台阶](#变态跳台阶-1)
    - [求 1+2+3+...+n，要求不能用 for、while、if、else 等关键字](#求-123n要求不能用-forwhileifelse-等关键字)
  - [九、字符串](#九字符串)
    - [最长不含重复字符的子字符串](#最长不含重复字符的子字符串-1)
    - [字符串中第一次只出现一次的字符位置](#字符串中第一次只出现一次的字符位置)
    - [把数字翻译成字符串](#把数字翻译成字符串)
    - [不用额外的空间，翻转单词顺序列](#不用额外的空间翻转单词顺序列)
    - [左旋转字符串](#左旋转字符串)
    - [把字符串转成整数](#把字符串转成整数)
    - [替换空格](#替换空格)
  - [十、数字](#十数字)
    - [二进制中 1 的个数](#二进制中-1-的个数)
    - [数值的整数次方](#数值的整数次方)
    - [最小的 k 个数](#最小的-k-个数-1)
    - [数据流中的中位数](#数据流中的中位数-1)
    - [字符流中第一个不重复的字符](#字符流中第一个不重复的字符)
    - [求按从小到大的顺序的第 N 个丑数，丑数只包含因子 2、3 和 5](#求按从小到大的顺序的第-n-个丑数丑数只包含因子-23-和-5-1)
    - [圆圈中最后剩下的数](#圆圈中最后剩下的数)
    - [求 1+2+3+...+n，要求不能用 for、while、if、else 等关键字](#求-123n要求不能用-forwhileifelse-等关键字-1)

<!-- /TOC -->

# 算法题

[剑指 Offer 学习心得](http://wiki.jikexueyuan.com/project/for-offer/)

[剑指 Offer 题集](https://github.com/wyjPro/JianZhiOffer/tree/master/src/com/offer)

## **一、链表**

### 从尾到头打印链表

1. 改变链表结构（头插法）：

```java
public class Main {
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
public class Main {
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

### 在 O(1)时间内删除链表节点

```java
public class Main {
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
public class Main {
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

### **链表中倒数第 k 个结点**

```java
public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
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

## **二、树**

### **根据前序中序遍历结果重建二叉树**

```java
public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
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
public class Main {
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

### **二叉查找树的第 K 个节点**

```java
public class Main{
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
public class Main{
    public int getTreeDepth(TreeNode pRoot) {
        return pRoot == null ? 0 : 1 + Math.max(getTreeDepth(pRoot.left), getTreeDepth(pRoot.right));
    }
}
```

### **平衡二叉树**

```java
public class Main{
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

## **三、排序**

### **归并排序**

**思想：**

归并排序是利用归并的思想实现的排序方法，采用经典的分治算法实现，这里的分就是把问题无序的数分解成一些小的组并使其有序，而治就是将这些有序的组进行有序的组合实现整个数列有序，其是通过归并实现的。

**代码实现：**

```java
public class Main {
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

平均最好最坏都为 O(N$\log$N)，证明如下：

> 对于长度为 N 的数组，$2^n$ = N，k $\in$[0, n-1]，
> 第 k 层有 $2^k$ 个子数组，每个子数组的长度为$2^{n-k}$，归并最多需要 $2^{n-k}$ 次比较。因此每层的比较次数为 $2^k$ \* $2^{n-k}$ = $2^n$，n 层总共为 n$2^n$ = N$\log$N

### **快速排序**

**思想：**

通过选取一个基准（理论上是可以任意取序列中的一个元素），通过基准将一个序列分割成独立的两部分，将小于基准的所有数据都和大于基准的另外一部分的所有数据分开，然后再按此方法对这两部分数据分别进行类似的排序，最终整个序列就可以实现有序，整个排序过程可以递归进行。

**代码实现：**

```java
public class Main {
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

- 堆的构造阶段：从右至左用 sink()函数构造大顶堆
- 下层排序阶段：将堆中的最大元素删除，然后放入堆缩小后数组中空出的位置

**代码实现：**

```java
public class Main{
    public void sort(int[] arr) {
        int arrIndex = arr.length - 1;
        //构造大顶堆
        for(int i = (arrIndex - 1) / 2 ; i >= 0; i--) {
            sink(arr, i, arrIndex);
        }

        //下层排序阶段
        while(arrLength > 0) {
            swap(arr, 0, arrLength--);
            sink(arr, 0, arrLength);
        }
    }
    //下沉元素
    private void sink(int[] arr, int index, int arrIndex) {
        while((2 * index + 1) <= arrIndex) {
            int j = 2 * index + 1;
            if(j < arrIndex && arr[j] < arr[j+1]) j++;
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

最好最坏平均情况下都为 O(N$\log$N)

### 数组中前一个数字大于后面一个数字构成逆序对，求数组中的逆序对个数

**思想：**

分治，采用归并排序。`逆序对的总数=左边数组中的逆序对的数量+右边数组中逆序对的数量+左右结合成新的顺序数组时中出现的逆序对的数量`

```java
public class Main{
    private int cnt = 0;
    private int[] copyOfNums;
    public int getInversePairs(int[] nums) {
        copyOfNums = new int[nums.length];
        sort(nums, 0, nums.length);
        return cnt;
    }
    private void sort(int[] nums, int lo, int hi) {
        if(lo >= hi) {
            return;
        }
        int mid = lo + (hi - lo) / 2;
        sort(nums, lo, mid);
        sort(nums, mid+1, hi);
        merge(nums, lo, mid, hi);

    }
    private void merge(int[] nums, int lo, int mid,int hi) {
        int i = lo, j = mid + 1;
        int k = lo;

        while(i <= mid || j <= hi) {
            if(i > mid) {
                copyOfNums[k] = nums[j++];
            } else if(j > hi) {
                copyOfNums[k] = nums[i++];
            } else if(nums[i] < nums[j]) {
                copyOfNums[k] = nums[i++];
            } else {
                copyOfNums[k] = nums[j++];
                //nums[i] > nums[j],说明nums[i...mid] > nums[j]
                //统计逆序对总数
                this.cnt += m - i + 1;
            }
            k++;
        }

        //由于已经统计了这两对子数组内部的逆序对， 因此需要把这两对子数组进行排序，避免在之后的统计过程中重复统计
        for(int k = lo, k <= hi; k++) {
            nums[k] = copyOfNums[k];
        }
    }
}
```

### 数组中出现次数超过一半的数字

**思想：**

基于快排，数组中中位数肯定是出现超过一半的那一个数字

```java
public class Main {
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
        return nums[index];
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
        swap(nums, j, lo);
        return j;
    }

    private void swap(int nums, int i, int j) {
        int temp = nums[i];
        nums[i]  = nums[j];
        nums[j]  = temp;
    }
}
```

### 最小的 k 个数

**思想：**

1. 快排，找到切分点 j 使得 j 等于 k

   ```java
   public class Main {
       public ArrayList<Integer> getMinK(int[] nums, int k) {
           ArrayList<Integer> ret = new ArrayList<>();
           if(k > nums.length || k <= 0) {
               return ret;
           }

           findKthSmallest(nums, k-1);

           for(int i = 0; i < k; i++) {
               ret.add(nums[i]);
           }
           return ret;
       }

       private void findKthSmallest(int nums, int k) {
           int lo = 0, hi = nums.length - 1;
           while(lo < hi) {
               int j = partition(nums, lo, hi);
               if(j == k) {
                   break;
               } else if(j > k) {
                   hi = j - 1;
               } else {
                   lo = j + 1;
               }
           }
       }

       private int partition(int nums, int lo, int hi) {
           int i = lo, j = hi + 1;
           int temp = nums[lo];
           while(true) {
               //while(nums[++i] < temp);
               //while(nums[--j] > temp);
               while(i != hi && nums[++i] < temp);
               while(j != lo && nums[--j] > temp);
               // >=
               if(i >= j) break;
               swap(nums, i, j);
           }
           swap(nums, lo, j);
           return j;
       }

       private void swap(int[] nums, int i, int j) {
           int temp = nums[i];
           nums[i] = nums[j];
           nums[j] = temp;

       }
   }
   ```

2. 使用大顶堆来维护大小为 k 的最小堆，每当大顶堆的 size() 超过 k 时，就 poll 一个元素

   堆常用方法：`poll()`：弹出并删除；`peek()`：返回但是不删除

   ```java
   public class Main {
       public ArrayList<Integer> getMinK(int[] nums, int k) {
           if(k > nums.length || k <= 0) {
               return new ArrayList<>();
           }

           //构造一个大顶堆
           //PriorityQueue 默认情况是一个小顶堆
           //public PriorityQueue(Comparator<? super E> comparator)
           PriorityQueue<Integer> maxHeap = new PriorityQueue<>((o1, o2)->o2 - o1);

           for(int num : nums) {
               maxHeap.add(num);
               if(maxHeap.size() > k) {
                   maxHeap.poll();
               }
           }

           return new ArrayList<>(maxHeap);
       }
   }
   ```

### 数据流中的中位数

**思想：**

大顶堆存储左半边元素，小顶堆存储右半边元素，且右半边元素始终大于左半边元素

```java
public class Main {
    private PriorityQueue<Integer> maxHeapInLeft = new PriorityQueue<>((o1, o2)->o2 - o1);
    private PriorityQueue<Integer> minHeapInRight = new PriorityQueue<>((o1, o2)->o2 - o1);
    private int N;

    public void insert(int val) {
        if(N % 2 == 0) {
            maxHeapInLeft.add(val);
            minHeapInRight.add(maxHeapInLeft.poll());
        } else {
            minHeapInRight.add(val);
            maxHeapInLeft.add(minHeapInRight.poll());
        }
        N++;
    }

    public double getMiddle() {
        //注意返回 double 类型
        if(N % 2 == 0) {
            // 2.0
            return (maxHeapInLeft.peek() + minHeapInRight.peek()) / 2.0;
        } else {
            //(double)
            return (double)minHeapInRight.peek();
        }
    }
}
```

## **四、栈**

栈的常用方法：

- peek()：返回首元素不删除
- pop()：返回首元素且删除
- push()：压入元素
- isEmpty()：判空

### 用二个栈实现队列

```java
public class Main {
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

### **包含 min 函数的栈**

```java
public class Main{
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
public class Main {
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

## 五、数组

### 数组中重复的数字

```java
public class Main {
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
public class Main {
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
public class Main {
    public int getMinNumber(int[] rotate) {
        if(rotate == null || rotate.length == 0) {
            return Integer.MIN_VALUE;
        }

        int l = 0, h = rotate.length - 1;
        while(l < h) {
            int m = l + (h - l) / 2;
            if(rotate[m] <= rotate[h]) {
                h = m;
            } else {
                l = m + 1;
            }
        }
mai
        return ratate[l];
    }
}
```

### 数组中出现次数超过一半的数字

**思想：**

基于快排，数组中中位数肯定是出现超过一半的那一个数字

```java
public class Main {
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
        return nums[index];
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
        swap(nums, j, lo);
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
public class Main {
    pubic int[] reAdjustArr(int[] nums) {
        if(nums.length == null || nums.length == 0) {
            return null;
        }

        int i = 0, j = nums.length - 1;
        while(i < j) {
            while(nums[i] % 2 != 0) i++;
            while(nums[j] % 2 == 0) j++;
            swap(nums, i, j);
        }

        return nums;
    }
}
```

### 把数组中的所有数字拼接起来，排成最小的数

**思想：**

排序问题，比较 s1+s2 和 s2+s1 的大小

```java
public class Main{
    public String createMinNumber(int[] nums) {
        if(nums.length == 0 || nums == null) {
            return null;
        }

        String[] copyOfNums = new String[nums.length];
        for(int i = 0; i < nums.length; i++) {
            copyOfNums[i] = nums[i] + " ";
        }

        //使用自定义排序 Comparator 比较器
        // comparaTo() 方法是 Comparable默认排序器的比较方法
        /*Arrays.sort(nums, new Comparator<String>() {
           @Override
           public int compare(String s1, String s2) {
               return (s1+s2).compareTo(s2+s1);
           }
       });*/
        Arrays.sort(copyOfNums, (s1, s2)->(s1 + s2).comparaTo(s2 + s1));

        StringBuffer ret = new StringBuffer();
        for(String str : copyOfNums) {
            ret.append(str);
        }

        return ret.toString();
    }
}
```

### 数组中前一个数字大于后面一个数字构成逆序对，求数组中的逆序对个数

**思想：**

分治，采用归并排序。`逆序对的总数=左边数组中的逆序对的数量+右边数组中逆序对的数量+左右结合成新的顺序数组时中出现的逆序对的数量`

```java
public class Main{
    private int cnt = 0;
    private int[] copyOfNums;
    public int getInversePairs(int[] nums) {
        copyOfNums = new int[nums.length];
        sort(nums, 0, nums.length);
        return cnt;
    }
    private void sort(int[] nums, int lo, int hi) {
        if(lo >= hi) {
            return;
        }
        int mid = lo + (hi - lo) / 2;
        sort(nums, lo, mid);
        sort(nums, mid+1, hi);
        merge(nums, lo, mid, hi);

    }
    private void merge(int[] nums, int lo, int mid,int hi) {
        int i = lo, j = mid + 1;
        int k = lo;

        while(i <= mid || j <= hi) {
            if(i > mid) {
                copyOfNums[k] = nums[j++];
            } else if(j > hi) {
                copyOfNums[k] = nums[i++];
            } else if(nums[i] < nums[j]) {
                copyOfNums[k] = nums[i++];
            } else {
                copyOfNums[k] = nums[j++];
                //nums[i] > nums[j],说明nums[i...mid] > nums[j]
                //统计逆序对总数
                this.cnt += m - i + 1;
            }
            k++;
        }

        //由于已经统计了这两对子数组内部的逆序对， 因此需要把这两对子数组进行排序，避免在之后的统计过程中重复统计
        for(int k = lo, k <= hi; k++) {
            nums[k] = copyOfNums[k];
        }
    }
}
```

### 数组中只出现一次的数字

**思想：**

任何数字和 0 做异或运算的结果都是本身；任何数字和本身做异或运算的结果都是 0。

例如：`2 ^ 8 ^ 2 = 8`

异或运算符 `^` 运算规则：`0^0=0`、`0^1=1`、`1^0=1`、`1^1=0`；

```java
public class Main {
    public int getOnceNumber(int[] nums) {
        if(nums == null || nums.length <= 2) {
            throw new Exception("nums size must bigger than 2")
        }

        int ret = 0;
        for(int i = 0; i < nums.length; i++) {
            ret ^= nums[i];
        }
        return ret;
    }
}
```

### 递增数组中找和为 S 的二个数，若有多个， 输出乘积最小者

**思想：**

双指针，最小者一定先出现

```java
public class Main {
    public ArrayList<Integer> findNumbersWithNums(int[] nums, int number) {
        int i = 0, j = nums.length;
        while(i < j) {
            int sum = nums[i] + nums[j];
            if(sum == number) {
                return new ArrayList<>(Arrays.asList(nums[i], nums[j]));
            } else if(sum < number) {
                i++;
            } else {
                j--;
            }
        }
    }
}
```

### 和为 S 的连续正数序列

**[双指针](https://www.nowcoder.com/questionTerminal/c451a3fd84b64cb19485dad758a55ebe)，根据窗口内值之和来确定窗口的位置和宽度**

```java
public class Main {
    public ArrayList<ArrayList<Integer> FindContinuousSequence(int sum) {
        if(sum == 0) {
            return null;
        }
        ArrayList<ArrayList<Integer> result = new ArrayList<>();
        int plow = 1, phigh = 2;
        while(phigh > plow) {
            int cur = (plow + phigh) * (phigh - plow + 1) / 2;
            if(cur == sum) {
                ArrayList<Integer> list = new ArrayList<>();
                for(int i = plow; i <= phigh; i++) {
                    list.add(i);
                }
                result.add(list);
                plow++;
            } else if(cur > sum) {
                plow++;
            } else {
                phigh++;
            }
        }
        return result;
    }
}

```

### 滑动窗口中的最大值

**大顶堆每次存放滑动窗口中的值**

```java
public class Main {
    public ArrayList<Integer> getMaxInWindows(int[] nums, int size) {
        ArrayList<Integer> ret = new ArrayList<>();
        if(size < 1 || nums.length < size) {
            return ret;
        }

        //构造大顶堆
        PriorityQueue<Integer> heap = new PriorityQueue<>((o1, o2)->o2 - o1);

        for(int i = 0; i < size; i++) {
            heap.add(nums[i]);
        }
        ret.add(heap.peek());

        for(int i = 0, j = i + size; j < nums.length; i++, j++) {
            heap.remove(nums[i]);
            heap.add(nums[j]);
            ret.add(heap.peek());
        }
        return ret;
    }
}
```

### 5 张扑克牌能否组成顺子

```java
public class Main {
    public boolean isContinue(int[] nums) {
        if(nums.length) {
            return false;
        }

        Arrays.sort(nums);
        int cnt = 0;
        //癞子个数
        for(int num : nums) {
            if(num == 0) {
                cnt++;
            }
        }
        //使用癞子补全剩余牌
        for(int i = cnt; i < nums.length; i++) {
            if(nums[i+1] == nums[i]) {
                return false;
            }
            cnt -= nums[i+1] - nums[i] - 1;
        }
        return cnt >= 0;
    }
}
```

## 六、动态规划

### **连续子数组的最大和**

**思想：**
一维 dp，
`dp[i] = max(dp[i-1]+nums[i] , nums[i])`

```java
public class Main {
    public int getMaxSumOFSubArray(int[] nums) {
        if(nums == null || nums.length == 0) {
            return 0;
        }

        int max = nums[0], sum = nums[0];
        //for 循环从 i = 1 开始
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

### 最长不含重复字符的子字符串

**思想：**

[动态规划](https://blog.csdn.net/m0_37862405/article/details/80369128)，记录当前字符之前的最长非重复子字符串长度 f(i-1)，其中 i 为当前字符的位置，d 为当前字符与它上次出现位置之间的距离。

1. 当前字符第一次出现：`f(i) = f(i-1) + 1`
2. 当前字符不是第一次出现：
   - `d > f(i)`时，`f(i) = f(i-1) + 1`
   - `d <= f(i)`时，`f(i) = d`

```java
public class Main{
    public int getLongestSubString(String str) {
        if(str == null || str.length() == 0) {
            return 0;
        }

        int maxLength = 0, curLength = 0;
        //记录当前字符上一次出现的位置
        int[] positions = new int[26];
        //初始化为 -1，表示该字符在之前还没有出现过
        Arrays.sort(positions, -1);

        for(int i = 0; i < str.length(); i++) {
            int curChar = str.charAt(i) - 'a';
            //上一次出现的位置
            int prePostion = positions[curChar];
            //当前字符与它上次出现位置之间的距离
            int distances = i - prePostion;

            if(prePostion == -1 || distances > curLength) {
                curLength++;
            } else {
                //更新最长非重复子字符串的长度
                if(curLength > maxLength) {
                    maxLength = curLength;
                }
                curLength = distances;
            }
            //更新字符最近一次出现的位置
            positions[curChar] = i;
        }

        if(curLength > maxLength) {
            maxLength = curLength;
        }

        return maxLength;
    }
}
```

### **m \* n 的棋盘上拿礼物，求礼物的最大价值**

**思想：**

二维 dp，转化为一维 dp。
`dp[i] = Math.max(dp[i], dp[i-1]) + values[i]`;

```java
public class Main {
    public int getMaxValue(int[][] giftsValues) {
        if(giftValues == null) {
            return 0;
        }

        int n = giftValues[0].length;
        int[] maxValues = new int[n];
        for(int[] giftsValue : giftsValues) {
            maxValues[0] = giftsValue[0];
            for(int i = 1; i < n; i++) {
                maxValues[i] = Math.max(maxValues[i], maxValues[i-1]) + giftsValue[i];
            }
        }

        return maxValues[n-1];
    }
}
```

### 剪绳子，使得每段的长度乘积最大

**思想：**

`dp[i] = Math.max(dp[i], Math.max(dp[j] * (i - j), j * (i * j)))`

```java
public class Main {
    public int integerBreak(int n) {
        if(n == 0) {
            return 0;
        }

        int[] dp = new int[n];
        dp[0] = 1;
        for(int i = 1; i < n; i++) {
            for(int j = 0; j < i; j++) {
                dp[i] = Math.max(dp[i], Math.max(dp[j] * (i - j), j * (i * j)));
            }
        }
        return dp[n-1];
    }
}
```

### 变态跳台阶

**思想：**

动态规划

```java
public class Main{
    public int getJumpFloorNumbers(int n) {
        int[] dp = new int[n];
        Arrays.fill(dp, 1);
        for(int i = 1; i < n; i++) {
            for(int j = 0; j < i; j++) {
                dp[i] += dp[j];
            }
        }
        return dp[n-1];
    }
}
```

### 求按从小到大的顺序的第 N 个丑数，丑数只包含因子 2、3 和 5

**思想：**

[动态规划](https://www.cnblogs.com/lfeng1205/p/6932328.html)，

```java
public class Main {
    public int getUglyNumber(int N) {
        if(N <= 6) {
            return N;
        }

        int[] dp = new int[N];
        dp[0] = 1;
        int i2 = 0, i3 = o, i5 = 0;
        for(int i = 0; i < N; i++) {
            int next2 = dp[i2] * 2;
            int next3 = dp[i3] * 3;
            int next5 = dp[i5] * 5;

            dp[i] = Math.min(next2, Math.min(next3, next5));

            if(dp[i] == next2) {
                i2++;
            }
            if(dp[i] == next3) {
                i3++;
            }
            if(dp[i] == next5) {
                i5++;
            }
        }

        return dp[N - 1];
    }
}
```

## 七、贪心

### **股票的最大利润**

**思想：**

记录当前最小值和最大值差

```java
public class Main {
    public int getMostProfit(int[] prices) {
        if(prices == null || prices.length == 0) {
            return 0;
        }

        int sofarMin = prices[0];
        int maxProfit = 0;
        for(int i = 1; i < prices.length; i++) {
            sofarMin = Math.min(sofarMin, prices[i]);
            maxProfit = Math.max(maxProfit, prices[i] - sofarMin);
        }
        return maxProfit;
    }
}
```

## 八、递归

### **斐波那契数列**

**思想：**

第 i 项只与前二项相关，保存前二项就好了。
`f(i) = f(i-1) + f(i-2)`

```java
public class Main{
    public int fibonacci(int n) {
        if(n <= 1) {
            return n;
        }
        int pre2 = 0, pre1 = 1;
        int fib = 0;
        for(int i = 2; i <= n; i++) {
            fib  = pre1 + pre2;
            pre2 = pre1;
            pre1 = fib;
        }
        return fib;
    }
}
```

### 跳 n 级台阶总共的跳法

**思想：**

与 fibonacci 数列一样

```java
public class Main{
    public int getJumpFloorNumbers(int n) {
        if(n <= 2) {
            return n;
        }
        int pre1 = 2, pre2 = 1;
        int numbers = 1;
        for(int i = 3; i <= n; i++) {
            numbers = pre1 + pre2;
            pre2    = pre1;
            pre1    = numbers;
        }
        return numbers;
    }
}
```

### 用 2 _ 1 的小矩形不重叠的覆盖 2 _ n 的大矩形

**思想：**

与 fibonacci 数列一样

```java
public class Main{
    public int getCoverRectNumbers(int n) {
        if(n <= 2) {
            return n;
        }
        int pre1 = 2, pre2 = 1;
        int numbers = 1;
        for(int i = 3; i <= n; i++) {
            numbers = pre1 + pre2;
            pre2    = pre1;
            pre1    = numbers;
        }
        return numbers;
    }
}
```

### 变态跳台阶

**思想：**

f(n) 是一个等比数列，`f(n) = 2 * f(n-1)`

```java
public class Main{
    public int getJumpFloorNumbers(int n) {
        if (n <= 0) {
            return 0;
        }
        if (n == 1) {
            return 1;
        }

        return 2 * getJumpFloorNumbers(n-1);
    }
}
```

### 求 1+2+3+...+n，要求不能用 for、while、if、else 等关键字

**思想：**

递归

```java
public class Main {
    public int getSum(int N) {
        int sum = N;
        boolean b = (N > 0) && (sum += getSum(n - 1) > 0);
        return sum;
    }
}
```

## 九、字符串

### 最长不含重复字符的子字符串

**思想：**

[动态规划](https://blog.csdn.net/m0_37862405/article/details/80369128)，记录当前字符之前的最长非重复子字符串长度 f(i-1)，其中 i 为当前字符的位置，d 为当前字符与它上次出现位置之间的距离。

1. 当前字符第一次出现：`f(i) = f(i-1) + 1`
2. 当前字符不是第一次出现：
   - `d > f(i)`时，`f(i) = f(i-1) + 1`
   - `d <= f(i)`时，`f(i) = d`

```java
public class Main{
    public int getLongestSubString(String str) {
        if(str == null || str.length() == 0) {
            return 0;
        }

        int maxLength = 0, curLength = 0;
        //记录当前字符上一次出现的位置
        int[] positions = new int[26];
        //初始化为 -1，表示该字符在之前还没有出现过
        Arrays.sort(positions, -1);

        for(int i = 0; i < str.length(); i++) {
            int curChar = str.charAt(i) - 'a';
            //上一次出现的位置
            int prePostion = positions[curChar];
            //当前字符与它上次出现位置之间的距离
            int distances = i - prePostion;

            if(prePostion == -1 || distances > curLength) {
                curLength++;
            } else {
                //更新最长非重复子字符串的长度
                if(curLength > maxLength) {
                    maxLength = curLength;
                }
                curLength = distances;
            }
            //更新字符最近一次出现的位置
            positions[curChar] = i;
        }

        if(curLength > maxLength) {
            maxLength = curLength;
        }

        return maxLength;
    }
}
```

### 字符串中第一次只出现一次的字符位置

**思想：**

1. 使用整型数组代替 HashMap 对出现的次数进行统计

   ```java
   public class Main {
       public int getOncePosition(String str) {
           //定义为 256，字符的 ASCII 码不超过 256
           int[] number = new number[256];

           for(int i = 0; i < str.length(); i++) {
               number[str.charAt(i)]++;
           }

           for(int i = 0; i < str.length(); i++) {
               if(number[str.charAt(i)] == 1) {
                   return i;
               }
           }
           return -1;
       }
   }
   ```

2. 使用 BitSet 来存储元素，仅使用二个比特位，优化了空间复杂度

   ```java
   public class Main {
       private BitSet bs1 = new BitSet(256);
       private BitSet bs2 = new BitSet(256);
       public int getOncePosition(String str) {

           for (char c : str.toCharArray()) {
               //boolean get(int index) 返回指定索引处的位值
               if(!bs1.get(c) && !bs2.get(c))  {
                   //void set(int index)将指定索引处的位设置为 true
                   bs1.set(c);
               } else if(bs1.get(c) && !bs2.get(c)) {
                   bs2.set(c);
               }
           }

           for(int i = 0; i < str.length(); i++) {
               char c = str.charAt(i);
               if(bs1.get(c) && !bs2.get(c)) {
                   return i;
               }
           }
           return -1;
       }
   }
   ```

### 把数字翻译成字符串

**思想：**

[动态规划](https://www.cnblogs.com/shiganquan/p/9347102.html)，`f(i) = f(i+1) + g(i, i+1) * f(i+2)`

`f(i)` 来表示从第 i 位数字开始不同的翻译数目，`g(i,i+1)` 表示第 i 位和 i+1 位拼起来的数字在 10~25 范围内，值为 1，否则为 0。

```java
public class Main {
    public int numDecodings(String str) {
        if(str.length == 0 || str == null) {
            return 0;
        }

        int f2 = 1, f1 = 0, g = 0;
        for(int i = str.length - 2; i >= 0; i++) {
            int temp = str.charAt(i) + " " + str.charAt(i+1)；
            if(temp > 26 && temp < 10) {
                g = 0;
            } else {
                g = 1;
            }
            int temp = f2;
            f2 = f2 + g * f1;
            f1 = temp;
        }

        return f2;
    }
}
```

### 不用额外的空间，翻转单词顺序列

**思想：**

先翻转每个单词，在翻转整个字符串

```java
public class Main {
    public String reverseWord(String str) {
        int n = str.length;
        char[] arr = str.toCharArray();
        int i = 0, j = 0;
        while(j <= n) {
            if(j == n || arr[j] == " ") {
                reverse(arr, i, j - 1);
                i = j + 1;
            }
            j++;
        }
        reverse(arr, 0, n - 1);
        return new String(arr);
    }
    private void reverse(char[] arr, int i, int j) {
        while(i < j) {
            swap(arr, i++, j--);
        }
    }
    private void swap(char[] arr, int i, int j) {
        char temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```

### 左旋转字符串

**思想：**

先翻转部分，在翻转整体

```java
public class Main {
    public String reverseWord(String str， int k) {
        if(k >= str.length) {
            return str;
        }
        char[] arr = str.toCharArray();
        reverse(arr, 0, k);
        reverse(arr, k + 1; str.length - 1);
        reverse(arr, 0, str.length - 1);
        return new String(arr);
    }
    private void reverse(char[] arr, int i, int j) {
        while(i < j) {
            swap(arr, i++, j--);
        }
    }
    private void swap(char[] arr, int i, int j) {
        char temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```

### 把字符串转成整数

```java
public class Main {
    public int getStringToInteger(String str) {
        if(str.length == 0 || str ==null) {
            return 0;
        }

        boolean isNegtive = str.charAt(0) == '-';
        int ret = 0;

        for(int i = 0; i < str.length; i++) {
            char c = str.charAt(i);
            if(i == '0' && (c == '+' || c == '-')) {
                continue;
            }
            if(c < '0' || c > '9') {
                return 0;
            }
            ret += ret * 10 + (c - '0');
        }
    }
}

```

### 替换空格

## 十、数字

### 二进制中 1 的个数

**思想：**

把一个整数减去 1，再和原整数做与 `&` 运算，会把该整数最右边一个 1 变成 0。那么一个整数的二进制表示中有多少个 1，就可以进行多少次这样的操作。

`&` 运算规则：两位同时为 1，结果才为 1，否则为 0

```java
public class Main {
    public int getNumberOne(int n) {
        int cnt = 0;
        while(n != 0) {
            cnt++;
            n &= (n - 1);
        }

        return cnt;
    }
}
```

### 数值的整数次方

**思想：**

递归，$(x*x)^{n/2}$ 可以递归求解，每次 n 都减小一半，算法时间复杂度为 O($\log$N)

```java
public class Main {
    public double getPower(int base, int exponent) {
        if(exponent = 0) {
            return 1;
        }
        if(exponent = 1) {
            return base;
        }

        boolean isNegitive = false;
        if(exponent < 0) {
            exponent = -exponent;
            isNegitive = true;
        }

        double pow = getPower(base * base, exponent / 2);
        if(exponent % 2 != 0) {
            pow = base * pow;
        }

        return isNegitive ? 1 / pow : pow;
    }
}
```

### 最小的 k 个数

**思想：**

快排，找到切分点 j 使得 j 等于 k

```java
public class Main {
    public ArrayList<Integer> getMinK(int[] nums, int k) {
        ArrayList<Integer> ret = new ArrayList<>();
        if(k > nums.length || k <= 0) {
            return ret;
        }

        findKthSmallest(nums, k-1);

        for(int i = 0; i < k; i++) {
            ret.add(nums[i]);
        }
        return ret;
    }

    private void findKthSmallest(int nums, int k) {
        int lo = 0, hi = nums.length - 1;
        while(lo < hi) {
            int j = partition(nums, lo, hi);
            if(j == k) {
                break;
            } else if(j > k) {
                hi = j - 1;
            } else {
                lo = j + 1;
            }
        }
    }

    private int partition(int nums, int lo, int hi) {
        int i = lo, j = hi + 1;
        int temp = nums[lo];
        while(true) {
            //while(nums[++i] < temp);
            //while(nums[--j] > temp);
            while(i != hi && nums[++i] < temp);
            while(j != lo && nums[--j] > temp);
            // >=
            if(i >= j) break;
            swap(nums, i, j);
        }
        swap(nums, lo, j);
        return j;
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;

    }
}
```

### 数据流中的中位数

**思想：**

大顶堆存储左半边元素，小顶堆存储右半边元素，且右半边元素始终大于左半边元素

```java
public class Main {
    private PriorityQueue<Integer> maxHeapInLeft = new PriorityQueue<>((o1, o2)->o2 - o1);
    private PriorityQueue<Integer> minHeapInRight = new PriorityQueue<>((o1, o2)->o2 - o1);
    private int N;

    public void insert(int val) {
        if(N % 2 == 0) {
            maxHeapInLeft.add(val);
            minHeapInRight.add(maxHeapInLeft.poll());
        } else {
            minHeapInRight.add(val);
            maxHeapInLeft.add(minHeapInRight.poll());
        }
        N++;
    }

    public double getMiddle() {
        //注意返回 double 类型
        if(N % 2 == 0) {
            // 2.0
            return (maxHeapInLeft.peek() + minHeapInRight.peek()) / 2.0;
        } else {
            //(double)
            return (double)minHeapInRight.peek();
        }
    }
}
```

### 字符流中第一个不重复的字符

**思想：**

用一个数组存储字符出现的次数，用一个队列来存储第一次只出现一次的元素

```java
public class Main {
    private int[] cnt = new int[256];
    private LinkedList<Integer> list = new LinkedList<>();

    public void insert(char c) {
        cnt[c]++;
        if(cnt[c] == 1) {
            list.add(c);
        }
    }
    public char getFirstAppearingOnce() {
        if(!list.isEmpty() && cnt[list.peek()] > 1) {
            list.poll();
        }

        return list.isEmpty() ? '#' : list.peek();
    }
}
```

### 求按从小到大的顺序的第 N 个丑数，丑数只包含因子 2、3 和 5

**思想：**

[动态规划](https://www.cnblogs.com/lfeng1205/p/6932328.html)，

```java
public class Main {
    public int getUglyNumber(int N) {
        if(N <= 6) {
            return N;
        }

        int[] dp = new int[N];
        dp[0] = 1;
        int i2 = 0, i3 = o, i5 = 0;
        for(int i = 0; i < N; i++) {
            int next2 = dp[i2] * 2;
            int next3 = dp[i3] * 3;
            int next5 = dp[i5] * 5;

            dp[i] = Math.min(next2, Math.min(next3, next5));

            if(dp[i] == next2) {
                i2++;
            }
            if(dp[i] == next3) {
                i3++;
            }
            if(dp[i] == next5) {
                i5++;
            }
        }

        return dp[N - 1];
    }
}
```

### 圆圈中最后剩下的数

**思想：**

[用环形链表模拟圆圈](http://wiki.jikexueyuan.com/project/for-offer/question-forty-five.html)。创建一个总共有 n 个结点的环形链表，然后每次在这个链表中删除第 m 个结点

```java
public class Test {
    public int getLastRemaining(int n, int m) {
        if(n < 1 || m < 1) {
            return -1;
        }

        List<Integer> ret = new LinkedList<>();
        //要删除的元素位置
        int idx = 0;
        while(ret.size() > 1) {
            //只要移动 m-1 次就可以移动到下一个要删除的元素上
            for(int i = 1; i < m; i++) {
                idx = (idx + 1) % ret.size();
            }
            ret.remove(idx);
        }
        return ret.get(0);
    }
}
```

### 求 1+2+3+...+n，要求不能用 for、while、if、else 等关键字

**思想：**

递归

```java
public class Main {
    public int getSum(int N) {
        int sum = N;
        boolean b = (N > 0) && (sum += getSum(n - 1) > 0);
        return sum;
    }
}
```
