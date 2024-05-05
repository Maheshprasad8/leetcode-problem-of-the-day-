5th may 24
**872. Leaf-Similar Trees**
class Solution {
    private:
    void solve(TreeNode* root, vector<int>&leaves){
        if(root==NULL){
            return;
        }
        if(root->left==NULL && root->right==NULL){
            leaves.push_back(root->val);
            return;
        }
        solve(root->left,leaves);
        solve(root->right,leaves);
    }
public:
    bool leafSimilar(TreeNode* root1, TreeNode* root2) {
      vector<int>leaves1,leaves2;
      solve(root1,leaves1);
      solve(root2,leaves2);  
      if(leaves1.size()!=leaves2.size()){
        return false;
      }
      for(int i=0;i<leaves1.size();i++){
if(leaves1[i]!=leaves2[i]){
    return false;
}

      }
      return true;
    }
};**

****Q.102. Binary Tree Level Order Traversal**
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
      vector<vector<int>>ans;
      if(root==NULL){
        return ans;
      }  
      queue<TreeNode*>q;
      q.push(root);
     // q.push(NULL);
      while(!q.empty()){
        vector<int>level;
        int n=q.size();
        for(int i=0;i<n;i++){
        TreeNode* front=q.front();
        q.pop();
        level.push_back(front->val);
        
if(front->left){
    q.push(front->left);
}
if(front->right){

    q.push(front->right);
}
        }
ans.push_back(level);
      }
      return ans;
    }
};
....................................................................
**Q.637. Average of Levels in Binary Tree**
class Solution {
public:
    vector<double> averageOfLevels(TreeNode* root) {
        vector<double>ans;
        if(root==NULL){
            return ans;
        }
     
     queue<TreeNode*>q;
     q.push(root);
    //  q.push(NULL);
     while(!q.empty()){
        int count=0;
     double sum=0;
        int n=q.size();
        for(int i=0;i<n;i++){
        TreeNode* front=q.front();
        q.pop();
        sum+=front->val;
        count++;
        if(front->left){
            q.push(front->left);
        }
        if(front->right){
            q.push(front->right);

        }
        }
ans.push_back(sum/count);
     }   
     return ans;
    }
};
