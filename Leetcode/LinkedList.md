# LinkedinList

## 160. Intersection of Two Linked Lists
HashSet Solution (Java):
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
**Time : O(N+M)**     
**Space : O(N)**

────────────────────────────

Two Pointer Solution (C++):
```c++
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if (!headA || !headB) return nullptr;

        ListNode* pA = headA;
        ListNode* pB = headB;

        while (pA != pB) {
            pA = (pA) ? pA->next : headB;
            pB = (pB) ? pB->next : headA;
        }

        return pA;  // Can be nullptr if no intersection
    }
};
```
**Time : O(N+M)**     
**Space : O(1)**
