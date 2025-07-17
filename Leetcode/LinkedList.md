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

───────────────────────

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


## 21. Merge Two Sorted Lists
Solution One(C++):
```c++
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode result = new ListNode(0); // 🎯 Dummy node
        ListNode s = result;

        while (list1 != null && list2 != null) {
            if (list1.val < list2.val) {
                s.next = list1;
                list1 = list1.next;
            } else {
                s.next = list2;
                list2 = list2.next;
            }
            s = s.next; // ✨ Move forward in the result list
        }

        // Attach remaining nodes if any ⛳
        if (list1 != null) s.next = list1;
        if (list2 != null) s.next = list2;

        return result.next; // Skip dummy node and return head 📤
    }
}
```
**Time : O(N+M)**     
**Space : O(1)**

───────────────────────

Recursion Solution (C++):
```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        ListNode* head = new ListNode(-1);

        if(list1 == NULL){
            return list2;
        }

        if(list2 == NULL){
            return list1;
        }

        if(list1->val <= list2->val){
            head = list1;
            head->next = mergeTwoLists(list1->next, list2);
        }
        else{
            head = list2;
            head->next = mergeTwoLists(list1, list2->next);
        }    

        return head;        
    }
};
```
**Time : O(N+M)**     
**Space : O(N+M)**

## 206. Reverse Linked List
Solution One(C++):
```c++
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = NULL;
        ListNode* nxt = head;
        ListNode* cur = head;
        
        while(cur){
            nxt = cur->next;
            cur->next = prev;
            prev = cur;
            cur = nxt;
        }
        
        return prev;
    }
};
```
**Time : O(n)**     
**Space : O(1)**

