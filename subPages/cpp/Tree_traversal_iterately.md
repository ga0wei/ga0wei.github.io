# [🏡Home](/) |   [👨‍💻About](/about)  |   [🗂️Texts](/allTexts)   |   [💬Web Quotes](/webQuotes)
#  📖树的遍历

✍Author：[GaoWei](/about)  

📆Data：23 / 06 / 01

📆Modified：-- / -- / --

---




## 前序遍历

先顺着最左边走到底，然后逆着这个顺序不断回退，如果有右树，就进入右树
### 递归
```c++
void dfs(TreeNode *root) {
    if (root) {
        cout << root->val << '\t';
        dfs(root->left);
        dfs(root->right);
    }
}
```
### 迭代
```c++
void iterate(TreeNode *root) {
    stack<TreeNode *> stk;
    if (root) stk.push(root);
    TreeNode *temp = nullptr;
    while (stk.size()) {
        temp = stk.top();
        stk.pop();
        cout << temp->val << '\t';
        if (temp->right) {
            stk.push(temp->right);
        }
        if (temp->left) {
            stk.push(temp->left);
        }
    }
}
```

## 中序遍历：
遇到当前节点，不能立刻遍历，而是需要先在栈中保存，然后顺着最左边不断向下，
如果无法向下了，就把栈顶元素取出来，访问栈顶元素，然后转向栈顶元素的右子树。
### 递归

```c++
void dfs(TreeNode *root) {
    if (root) {
        dfs(root->left);
        cout << root->val << '\t';
        dfs(root->right);
    }

}
```
### 迭代
```c++

void iterate(TreeNode *root) {
    stack<TreeNode *> stk;
    TreeNode *cur = root;
    while (cur || stk.size()) {
        if (cur) {
            stk.push(cur);
            cur = cur->left;
        } else {
            cur = stk.top();
            stk.pop();
            cout << cur->val << '\t';
            cur=cur->right;
        }
    }
}
```
