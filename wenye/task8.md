第96题

```C
int numTrees(int n){
    if(n==1)
        return 1;
    if(n==2)
        return 2;
    int num=2*numTrees(n-1);
    for(int i=1;i<n-1;i++)
    {
        num+=numTrees(i)*numTrees(n-1-i);
     }
    return num;
}
```

![屏幕截图 2021-01-18 131202](D:\task\task8\屏幕截图 2021-01-18 131202.jpg)

第101题

```
bool a(struct TreeNode *a1,struct TreeNode* a2);


bool isSymmetric(struct TreeNode* root){
    if(root==NULL)
        return true;
    if(root->left==NULL&&root->right==NULL)
        return true;
    if(root->left==NULL||root->right==NULL)
        return false;
    if(root->left->val!=root->right->val)
    {
        return false;
    }
    return a(root->left,root->right);

}

bool a(struct TreeNode *a1,struct TreeNode* a2)
{
    if(a1==NULL&&a2==NULL)
        return true;
    if(a1==NULL||a2==NULL)
        return false;
    if(a1->val!=a2->val)
        return false;
    
    
    return a(a1->left,a2->right)&&a(a2->left,a1->right);

}
```

![屏幕截图 2021-01-18 202635](D:\task\task8\屏幕截图 2021-01-18 202635.jpg)

第102题

```
int** levelOrder(struct TreeNode* root, int* returnSize, int** returnColumnSizes){
    *returnSize=0;
   struct TreeNode *queue[10001];
   int front,rear,i,j,temp;
    if(root==NULL)
        return NULL;
    
    front=-1;
    rear=-1;
    queue[++rear]=root;
    int **res=(int**)malloc(sizeof(int*)*10000);
    *returnColumnSizes=(int*)malloc(sizeof(int)*10000);
    
    while(rear!=front)
    {
         (*returnColumnSizes)[*returnSize]=rear-front;
        res[*returnSize]=(int*)malloc(sizeof(int)*(rear-front));
        for(i=0,j=front+1;i<rear-front;i++,j++)
        {
            res[*returnSize][i]=queue[j]->val;
        }
        (*returnSize)++;
        temp=rear;
        for(i=front+1;i<=temp;i++)
        {
            if(queue[i]->left)
            {
                queue[++rear]=queue[i]->left;
            }
            if(queue[i]->right)
            {
                queue[++rear]=queue[i]->right;
            }
         }
        front=temp; 
    }         
   return res; 
}
```

![屏幕截图 2021-01-21 122143](D:\task\task8\屏幕截图 2021-01-21 122143.jpg)

第105题

```

void a(struct TreeNode*,int *,int ,int *,int);
struct TreeNode* buildTree(int* preorder, int preorderSize, int* inorder, int inorderSize){
    int i,j,*m,*n;
    struct TreeNode*p,*root;
    if(preorder==NULL||inorder==NULL)
        return NULL;
    if(preorderSize==0)
        return NULL;
    p=(struct TreeNode*)malloc(sizeof(struct TreeNode));
    p->val=preorder[0];
    p->right=NULL;
    p->left=NULL;
    root=p;
    for(i=0;i<inorderSize;i++)
    {
        if(inorder[i]==p->val)
            break;
    }
    m=&preorder[i];
    n=&inorder[i];
    if(i!=0)
    {
      p->left=(struct TreeNode*)malloc(sizeof(struct TreeNode));
      a(p->left,&preorder[1],i,&inorder[0],i);
    }
    if(i!=preorderSize-1)
    {
     p->right=(struct TreeNode*)malloc(sizeof(struct TreeNode));
     a(p->right,m+1,preorderSize-i-1,n+1,preorderSize-i-1);
    }   
    return root;
}
void a(struct TreeNode*a1,int* preorder, int preorderSize, int* inorder, int inorderSize)
{
    int i;
    int *m,*n;
    a1->val=preorder[0];
    a1->left=NULL;
    a1->right=NULL;
    
    if(preorderSize==1||inorderSize==1)
        return;
    for(i=0;i<inorderSize;i++)
    {
        if(inorder[i]==a1->val)
            break;
    }
    m=&preorder[i];
    n=&inorder[i];
    if(i!=0)
    {
      a1->left=(struct TreeNode*)malloc(sizeof(struct TreeNode));
      a(a1->left,&preorder[1],i,&inorder[0],i);
    }
    if(i!=preorderSize-1)
    {
     a1->right=(struct TreeNode*)malloc(sizeof(struct TreeNode));
     a(a1->right,m+1,preorderSize-i-1,n+1,preorderSize-i-1);
    }   
    
}
```

![屏幕截图 2021-01-21 202155](D:\task\task8\屏幕截图 2021-01-21 202155.jpg)

第99题

```
![屏幕截图 2021-01-22 172523](D:\task\task8\屏幕截图 2021-01-22 172523.jpg)int search(struct TreeNode *root,struct TreeNode **pre, struct TreeNode **err1, struct TreeNode **err2)
{
    if(root==NULL)
        return 0;
    
    if(search(root->left,pre,err1,err2)==-1)
        return -1;
    if(*pre!=NULL&&(*pre)->val>root->val)
    {
        if(*err1==NULL)
        {
            *err1=*pre;
            *err2=root;
        }
        else{
            *err2=root;
            return -1;
        }
    }
    *pre=root;
    if(search(root->right,pre,err1,err2)==-1)
        return -1;
    return 0;
}
void recoverTree(struct TreeNode* root){
         struct TreeNode *pre=NULL;
         struct TreeNode *err1=NULL;
         struct TreeNode *err2=NULL;
    search(root,&pre,&err1,&err2);
    
    int temp;
    temp=err1->val;
    err1->val=err2->val;
    err2->val=temp;

}
```

