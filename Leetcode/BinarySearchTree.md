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
**Time : O(N)**     
**Space : O(1)**

```