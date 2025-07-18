# BinarySearchTree

## 235. Lowest Common Ancestor of a Binary Search Tree
```c++
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(p == NULL || q == NULL || root == NULL){
            return root;
        }

        if(p->val == root->val || q->val == root->val){
            return root;
        }

        if(p->val > root->val && q->val < root->val ){
            return root;
        }

        if(p->val < root->val && q->val > root->val ){
            return root;
        }

        if(p->val < root->val && q->val < root->val){
            return lowestCommonAncestor(root->left, p, q);
        }
        else{
            return lowestCommonAncestor(root->right, p, q);
        }
    }
};
```
** Time : O(h) total time is proportional to the number of nodes n **   
Time Complexity: O(h)
At each step, you move either left or right down the tree.

You stop when you find the split point or when you reach a target node.

h = height of the tree

Best case (balanced BST): O(log n)

Worst case (skewed BST): O(n)  
** Space : O(h) **
because of recursion stack.

Same as time complexity.

You don’t use any additional data structures.


## 98. Validate Binary Search Tree
```c++
class Solution {
public:
    bool isValidBST(TreeNode* root) {
        return helper(root, LONG_MIN, LONG_MAX);
    }

    bool helper(TreeNode* node, long minVal, long maxVal) {
        if(node == NULL){
            return true;
        }

        if(node->val <= minVal || node->val >= maxVal){
            return false;
        }

        return helper(node->left, minVal, node->val) && helper(node->right, node->val, maxVal);
    }
};
```
** Time : O(n) total time is proportional to the number of nodes n**     
**Space : O(h) where h is the height of the tree.

This comes from the recursion stack.

In the best case (balanced BST): O(log n)

In the worst case (skewed tree): O(n)**


