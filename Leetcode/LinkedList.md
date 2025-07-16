# LinkedinList

## 160. Intersection of Two Linked Lists
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
            Set<ListNode> nodesSeen = new HashSet<>();
            ListNode cur = headA;
            ListNode list = headB;
            while(cur != null){
                nodesSeen.add(cur);
                cur = cur.next;
            }
            while(list != null){
               if (nodesSeen.contains(list)){
                   break;
               }
                list = list.next;
            }
     return list;
    }
}
```