<!-- TOC -->

- [链表](#链表)
  - [从尾到头打印链表](#从尾到头打印链表)
  - [在 O(1)时间内删除链表节点](#在-o1时间内删除链表节点)
  - [删除链表中重复的结点](#删除链表中重复的结点)
  - [链表中倒数第 k 个结点](#链表中倒数第-k-个结点)
  - [链表中环的入口结点](#链表中环的入口结点)
  - [合并二个排序的链表](#合并二个排序的链表)
  - [反转链表](#反转链表)
  - [两个链表的第一个公共结点](#两个链表的第一个公共结点)
  - [复杂链表的复制](#复杂链表的复制)
- [树](#树)
  - [根据前序中序遍历结果重建二叉树](#根据前序中序遍历结果重建二叉树)
  - [给定二叉树其中的一个节点，返回中序遍历顺序的下一个结点](#给定二叉树其中的一个节点返回中序遍历顺序的下一个结点)
  - [树的子结构](#树的子结构)
  - [二叉树的镜像](#二叉树的镜像)
  - [对称二叉树](#对称二叉树)
  - [从上往下打印二叉树](#从上往下打印二叉树)
  - [把二叉树打印成多行](#把二叉树打印成多行)
  - [按之字形顺序打印二叉树](#按之字形顺序打印二叉树)
  - [二叉查找树的第 K 个节点](#二叉查找树的第-k-个节点)
  - [二叉树的深度](#二叉树的深度)
  - [平衡二叉树](#平衡二叉树)
  - [二叉搜索树的后续遍历序列](#二叉搜索树的后续遍历序列)
  - [二叉树中和为某一值的路径](#二叉树中和为某一值的路径)
  - [树中二个节点的最低公共祖先](#树中二个节点的最低公共祖先)
  - [非递归的中序遍历](#非递归的中序遍历)
  - [二叉搜索树与双向链表](#二叉搜索树与双向链表)
- [排序](#排序)
  - [归并排序](#归并排序)
  - [快速排序](#快速排序)
  - [堆排序](#堆排序)
  - [数组中前一个数字大于后面一个数字构成逆序对，求数组中的逆序对个数](#数组中前一个数字大于后面一个数字构成逆序对求数组中的逆序对个数)
  - [数组中出现次数超过一半的数字](#数组中出现次数超过一半的数字)
  - [数组中只出现一次的字符，有二个只出现一次的字符](#数组中只出现一次的字符有二个只出现一次的字符)
  - [最小的 k 个数](#最小的-k-个数)
  - [数据流中的中位数](#数据流中的中位数)
  - [冒泡](#冒泡)
  - [选择排序](#选择排序)
  - [插入排序](#插入排序)
  - [希尔排序](#希尔排序)
  - [桶排序](#桶排序)
  - [基数排序](#基数排序)
  - [统计一个数字 k 在排序数组中出现的次数。](#统计一个数字-k-在排序数组中出现的次数)
- [栈](#栈)
  - [用二个栈实现队列](#用二个栈实现队列)
  - [包含 min 函数的栈](#包含-min-函数的栈)
  - [输入二个序列，第一个序列是栈的压入序列，判断第二个序列是否为栈的弹出序列](#输入二个序列第一个序列是栈的压入序列判断第二个序列是否为栈的弹出序列)
- [数组](#数组)
  - [数组中重复的数字](#数组中重复的数字)
  - [二维数组中的查找，数组从左到右从上到下递增](#二维数组中的查找数组从左到右从上到下递增)
  - [旋转数组的最小数字](#旋转数组的最小数字)
  - [数组中出现次数超过一半的数字](#数组中出现次数超过一半的数字-1)
  - [调整数组顺序使奇数位于偶数前面，并且相对位置不发生变化](#调整数组顺序使奇数位于偶数前面并且相对位置不发生变化)
  - [把数组中的所有数字拼接起来，排成最小的数](#把数组中的所有数字拼接起来排成最小的数)
  - [数组中前一个数字大于后面一个数字构成逆序对，求数组中的逆序对个数](#数组中前一个数字大于后面一个数字构成逆序对求数组中的逆序对个数-1)
  - [数组中只出现一次的数字](#数组中只出现一次的数字)
  - [递增数组中找和为 S 的二个数，若有多个， 输出乘积最小者](#递增数组中找和为-s-的二个数若有多个-输出乘积最小者)
  - [和为 S 的连续正数序列](#和为-s-的连续正数序列)
  - [滑动窗口中的最大值](#滑动窗口中的最大值)
  - [5 张扑克牌能否组成顺子](#5-张扑克牌能否组成顺子)
  - [顺时针打印矩阵](#顺时针打印矩阵)
- [动态规划](#动态规划)
  - [连续子数组的最大和](#连续子数组的最大和)
  - [最长不含重复字符的子字符串](#最长不含重复字符的子字符串)
  - [m \* n 的棋盘上拿礼物，求礼物的最大价值](#m--n-的棋盘上拿礼物求礼物的最大价值)
  - [剪绳子，使得每段的长度乘积最大](#剪绳子使得每段的长度乘积最大)
  - [变态跳台阶](#变态跳台阶)
  - [求按从小到大的顺序的第 N 个丑数，丑数只包含因子 2、3 和 5](#求按从小到大的顺序的第-n-个丑数丑数只包含因子-23-和-5)
- [贪心](#贪心)
  - [股票的最大利润](#股票的最大利润)
- [递归](#递归)
  - [斐波那契数列](#斐波那契数列)
  - [跳 n 级台阶总共的跳法](#跳-n-级台阶总共的跳法)
  - [用 2 _ 1 的小矩形不重叠的覆盖 2 _ n 的大矩形](#用-2-_-1-的小矩形不重叠的覆盖-2-_-n-的大矩形)
  - [变态跳台阶](#变态跳台阶-1)
  - [求 1+2+3+...+n，要求不能用 for、while、if、else 等关键字](#求-123n要求不能用-forwhileifelse-等关键字)
- [字符串](#字符串)
  - [最长不含重复字符的子字符串](#最长不含重复字符的子字符串-1)
  - [字符串中第一次只出现一次的字符位置](#字符串中第一次只出现一次的字符位置)
  - [把数字翻译成字符串](#把数字翻译成字符串)
  - [不用额外的空间，翻转单词顺序列](#不用额外的空间翻转单词顺序列)
  - [左旋转字符串](#左旋转字符串)
  - [把字符串转成整数](#把字符串转成整数)
  - [将字符串中的控格替换成" "](#将字符串中的控格替换成)
  - [字符串的排列](#字符串的排列)
- [数字](#数字)
  - [二进制中 1 的个数](#二进制中-1-的个数)
  - [数值的整数次方](#数值的整数次方)
  - [最小的 k 个数](#最小的-k-个数-1)
  - [数据流中的中位数](#数据流中的中位数-1)
  - [字符流中第一个不重复的字符](#字符流中第一个不重复的字符)
  - [求按从小到大的顺序的第 N 个丑数，丑数只包含因子 2、3 和 5](#求按从小到大的顺序的第-n-个丑数丑数只包含因子-23-和-5-1)
  - [圆圈中最后剩下的数](#圆圈中最后剩下的数)
  - [求 1+2+3+...+n，要求不能用 for、while、if、else 等关键字](#求-123n要求不能用-forwhileifelse-等关键字-1)
  - [不用加减乘除做加法](#不用加减乘除做加法)
- [回溯法](#回溯法)
  - [打印从 1 到最大的 n 个数](#打印从-1-到最大的-n-个数)
  - [矩阵中的路径](#矩阵中的路径)
- [其它](#其它)
  - [多线程死锁](#多线程死锁)
  - [读取文件中的内容写入到另外一个文件](#读取文件中的内容写入到另外一个文件)
  - [LRU 算法](#lru-算法)

<!-- /TOC -->

[剑指 Offer 学习心得](http://wiki.jikexueyuan.com/project/for-offer/)

[剑指 Offer 题集](https://github.com/wyjPro/JianZhiOffer/tree/master/src/com/offer)

# 链表

## 从尾到头打印链表

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

```java
public class Solution {
    ArrayList<Integer> arrayList=new ArrayList<Integer>();
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
        if(listNode!=null){
            this.printListFromTailToHead(listNode.next);
            arrayList.add(listNode.val);
        }
        return arrayList;
    }
}
```

## 在 O(1)时间内删除链表节点

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

## 删除链表中重复的结点

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

## 链表中倒数第 k 个结点

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

## 链表中环的入口结点

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

## 合并二个排序的链表

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

## 反转链表

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

## 两个链表的第一个公共结点

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

## 复杂链表的复制

[复杂链表的复制](https://www.nowcoder.com/questionTerminal/f836b2c43afc4b35ad6adc41ec941dba?f=discussion)

**思想：**

1. 遍历链表，复制每个结点，如复制结点 A 得到 A1，将结点 A1 插到结点 A 后面；
2. 重新遍历链表，复制老结点的随机指针给新结点，如 A1.random = A.random.next;
3. 拆分链表，将链表拆分为原链表和复制后的链表

```java
public class Solution {
    public RandomListNode Clone(RandomListNode pHead) {
        if(pHead == null) {
            return null;
        }

        RandomListNode currentNode = pHead;
        //1、复制每个结点，如复制结点A得到A1，将结点A1插到结点A后面；
        while(currentNode != null){
            RandomListNode cloneNode = new RandomListNode(currentNode.label);
            RandomListNode nextNode = currentNode.next;
            currentNode.next = cloneNode;
            cloneNode.next = nextNode;
            currentNode = nextNode;
        }

        currentNode = pHead;
        //2、重新遍历链表，复制老结点的随机指针给新结点，如A1.random = A.random.next;
        while(currentNode != null) {
            currentNode.next.random = currentNode.random==null?null:currentNode.random.next;
            currentNode = currentNode.next.next;
        }

        //3、拆分链表，将链表拆分为原链表和复制后的链表
        currentNode = pHead;
        RandomListNode pCloneHead = pHead.next;
        while(currentNode != null) {
            RandomListNode cloneNode = currentNode.next;
            currentNode.next = cloneNode.next;
            cloneNode.next = cloneNode.next==null?null:cloneNode.next.next;
            currentNode = currentNode.next;
        }

        return pCloneHead;
    }
}
```

# 树

## 根据前序中序遍历结果重建二叉树

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

## 给定二叉树其中的一个节点，返回中序遍历顺序的下一个结点

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

## 树的子结构

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

## 二叉树的镜像

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

## 对称二叉树

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

## 从上往下打印二叉树

```java
public class Main {
    public ArrayList<Integer> printBinaryTree(TreeNode pRoot) {
        if(pRoot == null) {
            return new ArrayList<>();
        }

        Queue<TreeNode> queue = new LinkedList<>();
        ArrayList<Integer> ret = new ArrayList<>();
        queue.add(pRoot);
        while(!queue.isEmpty()) {
            int size = queue.size();
            while(size-- > 0) {
                //队列的 poll()方法，返回并删除
                TreeNode t = queue.poll();
                if(t == null) {
                    continue;
                }
                ret.add(t.val);
                queue.add(t.left);
                queue.add(t.right);
            }
        }
        return ret;
    }
}
```

## 把二叉树打印成多行

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

## 按之字形顺序打印二叉树

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

## 二叉查找树的第 K 个节点

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

## 二叉树的深度

```java
public class Main{
    public int getTreeDepth(TreeNode pRoot) {
        return pRoot == null ? 0 : 1 + Math.max(getTreeDepth(pRoot.left), getTreeDepth(pRoot.right));
    }
}
```

## 平衡二叉树

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

## 二叉搜索树的后续遍历序列

**思想：**

采用分治法的思想，找到根结点、左子树的序列、右子树的序列，分别判断左右子序列是否为二叉树的后序序列。

由题意可得：

1. 后序遍历序列的最后一个元素为二叉树的根节点；
2. 二叉搜索树左子树上所有的结点均小于根结点、右子树所有的结点均大于根结点。

算法步骤如下：

1. 找到根结点；
2. 遍历序列，找到第一个大于等于根结点的元素 i，则 i 左侧为左子树、i 右侧为右子树；
3. 我们已经知道 i 左侧所有元素均小于根结点，那么再依次遍历右侧，看是否所有元素均大于根结点；若出现小于根结点的元素，则直接返回 false；若右侧全都大于根结点，则：
4. 分别递归判断左/右子序列是否为后序序列；

```java
public class Solution {
    public boolean VerifySquenceOfBST(int [] sequence) {
        if(sequence.length == 0)
            return false;
        if(sequence.length == 1)
            return true;
        return judge(sequence, 0, sequence.length-1);

    }
    public boolean judge(int[] a,int start,int root){
        if(start >= root)
            return true;
        int i = root;
        //从后面开始找
        while(i > start && a[i-1] > a[root])
            i--;//找到比根小的坐标

        //从前面开始找 star到i-1应该比根小
        for(int j = star;j<i-1;j++)
            if(a[j]>a[root])
                return false;

        return judge(a, star, i-1) && judge(a, i, root-1);
    }
}

```

## 二叉树中和为某一值的路径

**思想：**

递归实现

```java
public class Solution {
    ArrayList<ArrayList<Integer>> ret = new ArrayList<>();
    ArrayList<Integer> list = new ArrayList<>();
    public ArrayList<ArrayList<Integer>> FindPath(TreeNode root, int target) {
        if (root == null) {
            return ret;
        }
        list.add(root.val);
        target -= root.val;
        if (target == 0 && root.left == null && root.right == null) {
            ret.add(new ArrayList<>(list));
        }
        FindPath(root.left, target);
        FindPath(root.right, target);
        list.remove(list.size() - 1);
        return ret;
    }
}
```

## 树中二个节点的最低公共祖先

1. 二叉查找树

```java
public TreeNode getLowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if(root == null) {
        return root;
    }

    if(root.val > p.val && root.val > q.val) {
        return getLowestCommonAncestor(root.left, p, q);
    }
    if(root.val < p.val && root.val < q.val) {
        return getLowestCommonAncestor(root.right, p, q);
    }

    return root;
}
```

2. 普通二叉树

```java
public TreeNode getLowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if(root == null || p == null || q == null) {
        return root;
    }

    TreeNode left  = getLowestCommonAncestor(root.left, p, q);
    TreeNode right = getLowestCommonAncestor(root.right, p, q);

    return root == null ? right : right == null ? left : root;
}
```

## 非递归的中序遍历

**思想：**

1. 如果 head 非空，把它压入栈中，并让 head 指向它的左孩子。
2. 如果 head 为空，弹出栈顶节点，用 head 保存该节点，并打印该节点的值，并让 head 指向它的右孩子。

```java
public void middleorderTraversal(TreeNode root) {
    if (root == null) return;

    Stack<TreeNode> stack = new Stack<>();
    TreeNode p = root;
    while (p != null || !stack.isEmpty()) {
        while (p != null) {
            stack.push(p);
            p = p.left;
        }
        if (!stack.isEmpty()) {
            p = stack.pop();
            System.out.println(p.val);
            p = p.right;
        }
    }
}
```

## 二叉搜索树与双向链表

**思想：**

1. 核心是中序遍历的非递归算法。
2. 修改当前遍历节点与前一遍历节点的指针指向。

```java
public TreeNode Convert(TreeNode pRootOfTree) {
    if (pRootOfTree == null) {
        return null;
    }
    TreeNode p = pRootOfTree;
    TreeNode pre = p;//记录p的前一个节点
    Stack<TreeNode> stack = new Stack<>();
    boolean isFirst = true;
    while(p != null || !stack.isEmpty()) {
        while (p != null) {
            stack.push(p);
            p = p.left;
        }
        p = stack.pop();
        if (isFirst) {
            pRootOfTree = p;
            pre = pRootOfTree;
            isFirst = false;
        } else {
            p.left = pre;
            pre.right = p;
            pre = p;
        }
        p = p.right;
    }
    return pRootOfTree;
}
```

# 排序

[【数据结构与算法】这或许是东半球分析十大排序算法最好的一篇文章](https://mp.weixin.qq.com/s/iiH2wSG-hVeUHxIsfuu9gw)

[面试时写不出排序算法？看这篇就够了。](https://juejin.im/post/5cb6b8f551882532c334bcf2)

|              | 排序类别 | 平均时间复杂度 | 最好时间复杂度 | 最坏时间复杂度 | 空间复杂度 | 复杂性 |
| ------------ | -------- | -------------- | -------------- | -------------- | ---------- | ------ |
| 冒泡排序     | 交换排序 | O(N2)          | O(N)           | O(N2)          | O(1)       | 稳定   | 简单 |
| 简单选择排序 | 选择排序 | O(N2)          | O(N2)          | O(N2)          | O(1)       | 不稳定 | 简单 |
| 直接插入排序 | 插入排序 | O(N2)          | O(N)           | O(N2)          | O(1)       | 稳定   | 简单 |
| 希尔排序     | 插入排序 | O(Nlog2N)      |                | O(N1.5)        | O(1)       | 不稳定 | 较复杂 |
| 归并排序     | 归并排序 | O(nlog2n)      | O(nlog2n)      | O(nlog2n)      | O(n)       | 稳定   | 较复杂 |
| 快速排序     | 快速排序 | O(Nlog2N)      | O(Nlog2N)      | O(N2)          | O(Nlog2N)  | 不稳定 | 较复杂 |
| 堆排序       | 堆排序   | O(nlog2n)      | O(nlog2n)      | O(nlog2n)      | O(1)       | 不稳定 | 较复杂 |
| 基数排序     | 基数排序 | O(d(n+r))      | O(d(n+r))      | O(d(n+r))      | O(n+r)     | 稳定   | 较复杂 |

## 归并排序

**思想：**

归并排序是利用归并的思想实现的排序方法，将已有序的子序列合并，得到完全有序的序列；即先使每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，称为二路归并。

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

归并排序的形式就是一棵二叉树，它需要遍历的次数就是二叉树的深度，而根据完全二叉树的可以得出它的时间复杂度是 O(n\*log2n)

## 快速排序

**思想：**

通过一趟排序将要排序的数据分割成独立的两部分：分割点左边都是比它小的数，右边都是比它大的数。
然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列。

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

最坏情况数组本身有序，以第一个关键字为基准分为两个子序列，前一个子序列为空，此时执行效率最差，最坏 O($N^2$)

**空间复杂度：**

快速排序在每次分割的过程中，需要 1 个空间存储基准值。而快速排序的大概需要 Nlog2N 次的分割处理，所以占用空间也是 Nlog2N 个。

## 堆排序

**思想：**

分两个阶段：

1. 根据初始数组去构造初始堆（构建一个完全二叉树，保证所有的父结点都比它的孩子结点数值大）。
2. 每次交换第一个和最后一个元素，输出最后一个元素（最大值），然后把剩下元素重新调整为大根堆。

**代码实现：**

```java
public class HeapSort {
    public static void sort(int[] arr) {
        int length = arr.length;
        buildHeap(arr, length);

        // 进行n-1次循环，完成排序
        for (int i = length - 1; i > 0; i--) {
            //将堆顶元素与末位元素交换
            swap(arr, 0, i);
            // 数组长度 -1 隐藏堆尾元素
            length--;
            // 将堆顶元素下沉,目的是将最大的元素浮到堆顶来
            sink(arr, 0,length);
        }
    }

    /**
     * 构建初始堆
     */
    public static void buildHeap(int[] arr, int length) {
        for (int i = length / 2; i >= 0; i--) {
            sink(arr, i, length);
        }
    }

    /**
     * 下沉堆元素
     */
    public static void sink(int[] arr, int index, int length) {
        while (2 * index + 1 < length) {
            int j = 2 * index + 1;
            if (j < length - 1 && arr[j] < arr[j + 1]) j++;
            if (arr[index] >= arr[j]) {
                break;
            }
            swap(arr, index, j);
        }
    }

    public static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
```

**时间复杂度：**

最好最坏平均情况下都为 O(N$\log$N)

当想得到一个序列中第 k 个最小的元素之前的部分排序序列，最好采用堆排序。

## 数组中前一个数字大于后面一个数字构成逆序对，求数组中的逆序对个数

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

## 数组中出现次数超过一半的数字

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

## 数组中只出现一次的字符，有二个只出现一次的字符

```java

```

## 最小的 k 个数

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

## 数据流中的中位数

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

---

## 冒泡

**思想：**

从序列的一端开始往另一端冒泡，依次比较相邻的两个数的大小。两层循环，外层冒泡轮数，里层依次比较

```java
public void bubbleSort(int[] array) {
        if (array.length == 0 || array == null) {
            return;
        }

        for (int i = 0; i < array.length - 1; i++) {
            for (int j = 0; j < array.length - 1 - i; j++) {
                if (array[j] > array[j + 1]) {
                    swap(array, j, j + 1);
                }
            }
        }
    }

    private void swap(int[] array, int i, int j) {
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }
}
```

**优化：**

如果有序，停止遍历

```java
public void bubbleSortOptimized(int[] array) {
    if (array.length == 0 || array == null) {
        return;
    }

    for (int i = 0; i < array.length - 1; i++) {
        boolean isSorted = true;
        for (int j = 0; j < array.length - 1 - i; j++) {
            if (array[j] > array[j + 1]) {
                swap(array, j, j + 1);
                isSorted = false;
            }
        }
        if (isSorted) {
            return;
        }

    }
}
```

**时间复杂度**

## 选择排序

**思想：**

每趟从待排序的记录中选出关键字最小的记录，顺序放在已排序的记录序列末尾，直到全部排序结束为止。

```java
public void selectSort(int[] arr) {
    if (arr.length == 0 || arr == null) {
        return;
    }

    for (int i = 0; i < arr.length; i++) {
        int min = i;
        for (int j = i + 1; j < arr.length; j++) {
            if (arr[j] < arr[min]) {
                min = j;
            }
        }
        swap(arr, i, min);
    }
}
```

**时间复杂度**

1. 简单选择排序的比较次数与序列的初始排序无关。假设待排序的序列有 N 个元素，则比较次数总是 N (N - 1) / 2；
2. 而移动次数与序列的初始排序有关。当序列正序时，移动次数最少，为 0。当序列反序时，移动次数最多，为 3N (N - 1) / 2。

综合以上，简单排序的时间复杂度为 O(N2)。

## 插入排序

**思想：**

每一趟将一个待排序的记录，按照其关键字的大小插入到有序队列的合适位置里，直到全部插入完成。

```java
public void insertSort(int[] arr) {
    if (arr.length == 0 || arr == null) {
        return;
    }

    for (int i = 1; i < arr.length; i++) {
        int j = 0;//插入的位置
        int temp = arr[i];// 取出第i个数，和前i-1个数比较后，插入合适位置
        for (j = i - 1; j >= 0; j--) {
            if (arr[j] > temp) {
                arr[j + 1] = arr[j];
            }
        }
        arr[j + 1] = temp;
    }
}
```

**时间复杂度**

1. 当数据正序时，执行效率最好，每次插入都不用移动前面的元素，时间复杂度为 O(N)。
2. 当数据反序时，执行效率最差，每次插入都要前面的元素后移，时间复杂度为 O(N2)。

所以，数据越接近正序，直接插入排序的算法性能越好。

## 希尔排序

**思想：**

它是一种插入排序。把记录按步长 gap 分组，对每组记录采用直接插入排序方法进行排序。 随着步长逐渐减小，所分成的组包含的记录越来越多，当步长的值减小到 1 时，整个数据合成为一组，构成一组有序记录，则完成排序。

```java
public void shellSort(int[] arr) {
    if (arr.length == 0 || arr == null) {
        return;
    }

    int gap = arr.length / 2;
    while (gap >= 1) {
        for (int i = gap; i < arr.length; i++) {
            int j = 0;
            int temp = arr[i];

            for (j = i - gap; j >= 0; j -= gap) {
                if (arr[j] > temp) {
                    arr[j + gap] = arr[j];
                }
            }
            arr[j + gap] = temp;
        }
        gap = gap / 2;
    }
}
```

## 桶排序

**思想**

将要排的数据分到多个有序的桶里，每个桶里的数据再单独排序，再把每个桶的数据依次取出，即可完成排序。

**代码**

```java
public class BucketSort {
    public void bucketSort(int[] arr) {
        int max = arr[0], min = arr[0];
        int length = arr.length;

        //最大值和最小值的差
        for (int i = 0; i < length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            } else if (arr[i] < min) {
                min = arr[i];
            }
        }
        int diff = max - min;

        //桶列表
        ArrayList<ArrayList<Integer>> bucketList = new ArrayList<>();
        for (int i = 0; i < length; i++) {
            bucketList.add(new ArrayList<>());
        }

        //每个桶的存数区间
        float section = (float) diff / (float) (length - 1);

        //数据如桶
        for (int i = 0; i < length; i++) {
            //当前数除以区间得出存放桶的位置 减1后得出桶的下标
            int num = (int) (arr[i] / section) - 1;
            if (num < 0) {
                num = 0;
            }
            bucketList.get(num).add(arr[i]);
        }

        //桶内排序
        for (int i = 0; i < bucketList.size(); i++) {
            Collections.sort(bucketList.get(i));
        }

        //写入原数组
        int index= 0;
        for (ArrayList<Integer> arrayList : bucketList) {
            for (Integer value : arrayList) {
                arr[index++] = value;
            }
        }
    }
}

```

**时间复杂度**

在额外空间充足的情况下，尽量增大桶的数量，极限情况下每个桶只有一个数据时，或者是每只桶只装一个值时，完全避开了桶内排序的操作，桶排序的最好时间复杂度就能够达到 O(n)。

如果所有得数据都放在了一个桶内，这是非常影响效率的情况，会使时间复杂度下降到 O(nlogn)

## 基数排序

**思想**

将数据按位数切割成不同的数字，然后按每个位数分别比较。不管你的数字有多大，按照一位一位的排，0 - 9 最多也就十个桶：先按权重小的位置排序，然后按权重大的位置排序。

基数排序可以看成桶排序的扩展，也是用桶来辅助排序

**代码**

```java
public class RadixSort {
    public static void radixSort(int[] arr) {
        int length = arr.length;
        int max = arr[0];

        //最大值
        for (int i = 1; i < length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }

        //当前排序位置
        int location = 1;
        //桶列表
        ArrayList<ArrayList<Integer>> bucketList = new ArrayList<>();
        //长度为10 装入余数0-9的数据
        for (int i = 0; i < 10; i++) {
            bucketList.add(new ArrayList<>());
        }

        while (true) {
            //判断是否排完
            double dd = Math.pow(10, location - 1);
            if (max < dd) {
                break;
            }

            //数据入桶
            for (int i = 0; i < length; i++) {
                int number = (int) (arr[i] / dd) % 10;
                bucketList.get(number).add(arr[i]);
            }

            //写回数组
            int nn = 0;
            for (int i=0;i<10;i++){
                int size = bucketList.get(i).size();
                for(int ii = 0;ii < size;ii ++){
                    arr[nn++] = bucketList.get(i).get(ii);
                }
                bucketList.get(i).clear();
            }
            location++;
        }
    }
}

```

**时间复杂度**

假设在基数排序中，r 为基数，d 为位数。则基数排序的时间复杂度为 O(d(n+r))。

**空间复杂度**

在基数排序过程中，对于任何位数上的基数进行装桶操作时，都需要 n+r 个临时空间。

## 统计一个数字 k 在排序数组中出现的次数。

**思想：**

1. 算 k+0.5 和 k-0.5 之间的距离
2. 二分法，分别定位最左，最右的数字

```java

```

# 栈

栈的常用方法：

- peek()：返回首元素不删除
- pop()：返回首元素且删除
- push()：压入元素
- isEmpty()：判空

## 用二个栈实现队列

```java
public class Main {
    private Stack<Integer> stack1;
    private Stack<Integer> stack2;
    public void push(int node) {
        stack1.push(node);
    }
    public void pop() {
        if(stack2.isEmpty()) {
            //if(in.isEmpty())
            //    throw new Exception("queue is Empty");
            while(!stack1.isEmpty()) {
                stack2.push(stack1.pop());
            }
        }

        if(stack2.isEmpty())
            throw new Exception("queue is Empty");

        return stack2.pop();
    }
}
```

## 包含 min 函数的栈

```java
public class Main{
    private Stack<Integer> dataStack = new Stack<>();
    private Stack<Integer> minStack = new Stack<>();

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

## 输入二个序列，第一个序列是栈的压入序列，判断第二个序列是否为栈的弹出序列

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

# 数组

## 数组中重复的数字

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

## 二维数组中的查找，数组从左到右从上到下递增

**思想：**

类似二分查找

```java
public class Main {
    public boolean Find(int target, int[][] array) {
        if (array.length == 0 || array == null || array[0] == null) {
            return false;
        }

        int row = array.length, col = array[0].length;
        int i = 0, j = col - 1;

        while (i <= row - 1 && j >= 0) {
            if (target == array[i][j]) {
                return true;
            } else if (target > array[i][j]) {
                i++;
            } else {
                j--;
            }
        }

        return false;
    }
}
```

## 旋转数组的最小数字

**思想：**

[二分查找](https://www.nowcoder.com/questionTerminal/9f3231a991af4f55b95579b44b7a01ba?f=discussion)变形，含有重复数组

旋转之后的数组实际上可以划分成两个有序的子数组：前面子数组的大小都大于后面子数组中的元素

array[mid] == array[high]：出现这种情况的 array 类似 [1,0,1,1,1] 或者[1,1,1,0,1]，此时最小数字不好判断在 mid 左边
还是右边，这时只好一个一个试：high = high - 1

```java
public class Main {
    public int getMinNumber(int[] array) {
        if(array == null || array.length == 0) {
            return 0;
        }

        int l = 0, h = array.length - 1;
        while(l < h) {
            int m = l + (h - l) / 2;
            if(array[m] <= array[h]) {
                h = m;
            } else {
                l = m + 1;
            }
        }

        return array[l];
    }
}
```

## 数组中出现次数超过一半的数字

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

## 调整数组顺序使奇数位于偶数前面，并且相对位置不发生变化

**思想**

相对位置不发生变化可知保持稳定性，可以考虑采用插入排序的思想实现

```java
public class Main {
    public void reOrderArray(int [] array) {
        int len = array.length;
        int oddNum = 0;// 存储已经摆好位置的奇数个数

        for (int i = 0; i < len; i++) {
            if (array[i] % 2 == 1) {
                int j = i;// i 前面有几个偶数
                while (j > oddNum) {
                    int temp = array[j];
                    array[j] = array[j - 1];
                    array[j - 1] = temp;
                    j--;
                }
                oddNum++;
            }
        }
    }
}
```

## 把数组中的所有数字拼接起来，排成最小的数

**思想：**

解题思路：
先将整型数组转换成 String 数组，然后将 String 数组排序，最后将排好序的字符串数组拼接出来。关键就是制定排序规则。

排序规则如下：

- 若 ab > ba 则 a > b，
- 若 ab < ba 则 a < b，
- 若 ab = ba 则 a = b；

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

## 数组中前一个数字大于后面一个数字构成逆序对，求数组中的逆序对个数

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

## 数组中只出现一次的数字

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

## 递增数组中找和为 S 的二个数，若有多个， 输出乘积最小者

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

## 和为 S 的连续正数序列

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

## 滑动窗口中的最大值

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

## 5 张扑克牌能否组成顺子

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

## 顺时针打印矩阵

**思想：**

用四个变量分别控制矩阵的上下左右角变量，进行打印输出，还需要判断矩阵是否是单行或者单列。

```java
public ArrayList<Integer> printMatrix(int [][] matrix) {
    ArrayList<Integer> ret = new ArrayList<>();

    int r1 = 0, r2 = matrix.length - 1, c1 = 0, c2 = matrix[0].length - 1;

    while (r1 <= r2 && c1 <= c2) {
        for (int i = c1; i <= c2; i++) {
            ret.add(matrix[r1][i]);
        }
        for (int i = r1 + 1; i <= r2; i++) {
            ret.add(matrix[i][c2]);
        }
        if (r1 != r2) {
            for (int i = c2 - 1; i >= c1; i--) {
                ret.add(matrix[r2][i]);
            }
        }
        if (c1 != c2) {
            for (int i = r2 - 1; i > r1; i--) {
                ret.add(matrix[i][c1]);
            }
        }
        r1++; r2--; c1++; c2--;
    }
    return ret;
}
```

# 动态规划

## 连续子数组的最大和

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

雷同：

```java
    int[] dp = new int[array.length];
    int max = array[0];
    dp[0] = array[0];

    for (int i = 1; i < array.length; i++) {
        dp[i] = Math.max(array[i], dp[i-1] + array[i]);
        if (dp[i] > max) {
            max = dp[i];
        }
    }
```

## 最长不含重复字符的子字符串

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

## m \* n 的棋盘上拿礼物，求礼物的最大价值

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

## 剪绳子，使得每段的长度乘积最大

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

## 变态跳台阶

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

## 求按从小到大的顺序的第 N 个丑数，丑数只包含因子 2、3 和 5

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

# 贪心

## 股票的最大利润

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

# 递归

## 斐波那契数列

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

## 跳 n 级台阶总共的跳法

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

## 用 2 _ 1 的小矩形不重叠的覆盖 2 _ n 的大矩形

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

## 变态跳台阶

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

## 求 1+2+3+...+n，要求不能用 for、while、if、else 等关键字

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

# 字符串

## 最长不含重复字符的子字符串

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

## 字符串中第一次只出现一次的字符位置

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

## 把数字翻译成字符串

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

## 不用额外的空间，翻转单词顺序列

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

## 左旋转字符串

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

## 把字符串转成整数

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

## 将字符串中的控格替换成"%20"

**思想：**

从后往前遍历字符串，p1 指针指向字符串原来的末尾位置，p2 指针指向现在的末尾位置

```java
public class Main {
    public String replaceSpace(StringBuffer str) {
        //字符串原来的末尾位置
        int p1 = str.length() - 1;
        for(int i = 0; i <= p1; i++) {
            if(str.charAt(i) == ' ') {
                //这里要拼接二个空格
                str.append("  ");
            }
        }

        //现在的末尾位置
        int p2 = str.length() - 1;
        while(p1 >= 0 && p2 > p1) {
            char c = str.charAt(p1--);
            if(c == ' ') {
                str.setCharAt(p2--, '0');
                str.setCharAt(p2--, '2');
                str.setCharAt(p2--, '%');
            } else {
                str.setCharAt(p2--, c);
            }
        }
        return str.toString();
    }
```

## 字符串的排列

[字符串的排列](https://www.nowcoder.com/questionTerminal/fe6b651b66ae47d7acce78ffdd9a96c7?f=discussion)

**思想：**

回溯法

```java
public class Solution {
    public ArrayList<String> Permutation(String str) {
        if (str.length() == 0 || str == null) {
            return new ArrayList<>();
        }
        List<String> ret = new ArrayList<>();
        fun(str.toCharArray(), ret, 0);
        Collections.sort(ret);
        return (ArrayList)ret;
    }

    private static void fun(char[] chars, List<String> list, int i) {
        if (i == chars.length - 1) {
            if (!list.contains(new String(chars))) {
                list.add(new String(chars));
                return;
            }
        } else {
            //i = 0开始回溯
            for (int j = i; j < chars.length; j++) {
                swap(chars, i, j);
                fun(chars, list, i + 1);
                swap(chars, i, j);
            }
        }
    }

    //交换数组的两个下标的元素
    private static void swap(char[] str, int i, int j) {
        if (i != j) {
            char t = str[i];
            str[i] = str[j];
            str[j] = t;
        }
    }
}
```

# 数字

## 二进制中 1 的个数

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

## 数值的整数次方

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

## 最小的 k 个数

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

## 数据流中的中位数

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

## 字符流中第一个不重复的字符

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

## 求按从小到大的顺序的第 N 个丑数，丑数只包含因子 2、3 和 5

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

## 圆圈中最后剩下的数

**思想：**

[用环形链表模拟圆圈](http://wiki.jikexueyuan.com/project/for-offer/question-forty-five.html)。创建一个总共有 n 个结点的环形链表，然后每次在这个链表中删除第 m 个结点

```java
public class Test {
    public int getLastRemaining(int n, int m) {
        if(n < 0 || m < 1) {
            return -1;
        }

        List<Integer> ret = new LinkedList<>();
        for(int i = 0; i < n; i++) {
            ret.add(i);
        }
        //要删除的元素位置
        int idx = -1;
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

## 求 1+2+3+...+n，要求不能用 for、while、if、else 等关键字

```java
public class Solution {
    public int Sum_Solution(int n) {
        int sum = n;
        boolean b = (n > 0) && (sum += Sum_Solution(n - 1)) > 0;
        return sum;
    }
}
```

## 不用加减乘除做加法

思想：

1. 两个数异或：相当于每一位相加，而不考虑进位；
2. 两个数相与，并左移一位：相当于求得进位；
3. 将上述两步的结果相加

```java
public int Add(int num1,int num2) {
    while( num2!=0 ){
        int sum = num1 ^ num2;
        int carray = (num1 & num2) << 1;
        num1 = sum;
        num2 = carray;
    }
    return num1;
}
```

# 回溯法

## 打印从 1 到最大的 n 个数

```java

```

## 矩阵中的路径

**思想**

回朔法。首先，在矩阵中任选一个格子作为路径的起点。如果路径上的第 i 个字符不是 ch，那么这个格子不可能处在路径上的第 i 个位置。如果路径上的第 i 个字符正好是 ch，那么往相邻的格子寻找路径上的第 i+1 个字符。除在矩阵边界上的格子之外，其他格子都有 4 个相邻的格子。重复这个过程直到路径上的所有字符都在矩阵中找到相应的位置。

由于回朔法的递归特性，路径可以被开成一个栈。当在矩阵中定位了路径中前 n 个字符的位置之后，在与第 n 个字符对应的格子的周围都没有找到第 n+1 个字符，这个时候只要在路径上回到第 n-1 个字符，重新定位第 n 个字符。

由于路径不能重复进入矩阵的格子，还需要定义和字符矩阵大小一样的布尔值矩阵，用来标识路径是否已经进入每个格子。 当矩阵中坐标为 (row,col) 的格子和路径字符串中相应的字符一样时，从 4 个相邻的格子 (row,col-1)，(row-1,col)，(row,col+1) 以及(row+1,col) 中去定位路径字符串中下一个字符。如果 4 个相邻的格子都没有匹配字符串中下一个的字符，表明当前路径字符串中字符在矩阵中的定位不正确，我们需要回到前一个，然后重新定位。
　　一直重复这个过程，直到路径字符串上所有字符都在矩阵中找到合适的位置。

```java

//用一个状态数组保存之前访问过的字符，然后再分别按上，下，左，右递归
public class Solution {
    public boolean hasPath(char[] matrix, int rows, int cols, char[] str) {
        int flag[] = new int[matrix.length];
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (helper(matrix, rows, cols, i, j, str, 0, flag))
                    return true;
            }
        }
        return false;
    }

    private boolean helper(char[] matrix, int rows, int cols, int i, int j, char[] str, int k, int[] flag) {
        // index (i, j) 元素在数组 matrix 中的位置
        int index = i * cols + j;
        // 路径上的第一个字符不是 matrix[index] : matrix[index] != str[k]
        // 1 表示 index 位置访问过了， 0 表示没有访问过
        if (i < 0 || i >= rows || j < 0 || j >= cols || matrix[index] != str[k] || flag[index] == 1)
            return false;
        // str数组访问完
        if(k == str.length - 1) return true;

        flag[index] = 1;
        if (helper(matrix, rows, cols, i - 1, j, str, k + 1, flag)
                || helper(matrix, rows, cols, i + 1, j, str, k + 1, flag)
                || helper(matrix, rows, cols, i, j - 1, str, k + 1, flag)
                || helper(matrix, rows, cols, i, j + 1, str, k + 1, flag)) {
            return true;
        }
        // 上面 if 返回 0，说明以 index 为第一个起点是找不到一条完整的路径的，需要把 flag[index] 置为 0，开始下一个位置的回溯
        flag[index] = 0;
        return false;
    }
}
```

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

# 其它

## 多线程死锁

```java
public class MyLock {
    //创建两把锁对象
    public static final Object objA = new Object();
    public static final Object objB = new Object();
}

//竞争资源
public class DieLock extends Thread {
    private boolean flag;

    public DieLock(boolean flag) {
        this.flag = flag;
    }

    public void run() {
        if(flag) {
            sychronized(MyLock.objA) {
                //
                sychronized(MyLock.objB) {
                    //do
                }
            }
        } else {
            sychronized(MyLock.objB) {
                //
                sychronized(MyLock.objA) {
                    //do
                }
            }
        }
    }
}


//测试类
public class DeadLockDemo {
    public static void main(String[] args) {
        DieLock dl1 = new DieLock(true);
        DieLock dl2 = new DieLock(false);
        dl1.start();
        dl2.start();
    }
}
```

## 读取文件中的内容写入到另外一个文件

```java
public class Main {
    public void solution() {
        try {
            FileInputStream fis = new FileInputStream("c:\\..\\tmp.txt");
            FileOutputStream fos = new FileOutputStream("c:\\..\\tmp1.txt");

            int len = 0;
            byte[] b = new byte[fis.available()];

            while((len == fis.read(b)) != -1) {
                fos.write(b, 0, len);
                fos.flush();
            }
        } catch(FileNotFoundException e) {
            e.printStackTrace();
        } catch(IOException e) {
            e.printStackTrace();
        }
    }
}
```

```java
public class Main {
    public void solution() {
        try {
			BufferedReader  br =  new BufferedReader(
                new InputStreamReader(new FileInputStream("C:\\...\\tmp.txt"),"GB2312"));
			String b="";
			StringBuffer sb = new StringBuffer();
			try {
				while((b = br.readLine())!=null){
					//得到文件内容放到sb中
					sb.append(b);
					//这里可以写自己想对每一行的处理代码
				}
				String s = sb.toString();
				BufferedWriter bw = new BufferedWriter(
                    new OutputStreamWriter(new FileOutputStream("C:\\...\\tmp1.txt"),"GB2312"));
				bw.write(s);
				bw.flush();
			} catch (IOException e) {
				e.printStackTrace();
			}
		} catch (UnsupportedEncodingException | FileNotFoundException e) {
			e.printStackTrace();
		}
    }
}
```

## LRU 算法

**思想：**

LRU 使用了哈希链表来实现。所以需要维护一个 HashMap 和定义为 Node 类的链表

使用 head 和 end 表示链表的头和尾，在时间上先被访问的数据作为双向链表的 head，后被访问的数据作为双向链表的 end，当达到内存设置大小之后，新进入未被访问过的数据，则将 head 的节点删除，将新的数据插入 end 处，如果访问的数据在内存中，则将数据更新到 end 初，删除原始在的位置。

```java
class Node {
    Node(String key, String value) {
        this.key = key;
        this.value = value;
    }
    public Node pre;
    public Node next;
    public String key;
    public String val;
}

class LRUCache {
    private Node head;
    private Node end;
    //缓存存储上限
    private int limit;

    private HashMap<String, Node> map;

    public LRUCache(int limit) {
        this.limit = limit;
        map = new HashMap<String, Node>();
    }

    //删除结点：删除头尾中间结点
    private String removeNode(Node node) {
        if(node == end) {
            node = node.pre;
        } else if(node == head) {
            node = node.next;
        } else {
            node.next.pre = node.pre;
            node.pre.next = node.next;
        }
        return node.key;
    }

    //插入结点：Node链表为空或者不为空
    public void addNode(Node node) {
        if(end != null) {
            end.next = node;
            node.pre = end;
            node.next = null;
        }
        end = node;

        if(head == null) {
            head = node;
        }
    }

    //刷新被访问的结点
    private void refreshNode(Node node) {
        //如果访问的是尾结点
        if(node == end) {
            return;
        }

        removeNode(node);
        addNode(node);
    }

    public void remove(String key) {
        Node node = map.get(key);
        removeNode(node);
        map.remove(key);
    }

    public void put(String key, String value) {
        Node node = map.get(key);
        if(node == null) {
            if(map.size() >= limit) {
                String oldKey = removeNode(key);
                map.remove(key);
            }
            node = new Node(key, value);
            addNode(key);
            map.put(key, node);
        } else {
            node.val = value;
            refreshNode(node);
        }
    }

    public String get(String key) {
        Node node = map.get(key);
        if(node == null) {
            return null;
        }
        refreshNode(node);
        return node.val;
    }


}

```
