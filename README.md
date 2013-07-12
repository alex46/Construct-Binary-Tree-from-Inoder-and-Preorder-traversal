Construct-Binary-Tree-from-Inoder-and-Preorder-traversal
========================================================

/**
  * Definition for binary tree
  * public class TreeNode {
 *     int val;
  *     TreeNode left;
  *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
 public class Solution {
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        // Start typing your Java solution below
        // DO NOT write main() function
        int preLength = preorder.length;
        int inLength = inorder.length;
        return buildTree(preorder, 0, preLength-1, inorder, 0, inLength-1);
    }
   
     public TreeNode buildTree(int[] pre, int preStart, int preEnd, int[] in, int inStart, int inEnd){
        if(inStart > inEnd){
            return null;
        }
       int rootVal = pre[preStart];
        TreeNode root = new TreeNode(rootVal);
        int rootIndex = 0;
      
      for(int i = inStart; i <= inEnd; i++){
             if(in[i] == rootVal){
                   rootIndex = i;
                  int len = rootIndex - inStart;
              
               
        root.left = buildTree(pre, preStart+1, preStart+len, in, inStart, rootIndex-1);
        root.right = buildTree(pre, preStart+len+1, preEnd, in, rootIndex+1, inEnd);
             }
        }
