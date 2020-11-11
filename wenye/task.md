# GitFlow

### 主要工作流程

1 . 初始化项目为gitflow , 默认创建master分支 , 然后从master拉取第一个develop分支
2 . 从develop拉取feature分支进行编码开发(多个开发人员拉取多个feature同时进行并行开发 , 互不影响)

3 . feature分支完成后 , 合并到develop(不推送 , feature功能完成还未提测 , 推送后会影响其他功能分支的开发)
  合并feature到develop , 可以选择删除当前feature , 也可以不删除 . 但当前feature就不可更改了 , 必须从release分支继续编码修改

4 . 从develop拉取release分支进行提测 , 提测过程中在release分支上修改BUG

5 . release分支上线后 , 合并release分支到develop/master并推送
   合并之后 , 可选删除当前release分支 , 若不删除 , 则当前release不可修改 . 线上有问题也必须从master拉取hotfix分支进行修改

6 . 上线之后若发现线上BUG , 从master拉取hotfix进行BUG修改

7 . hotfix通过测试上线后 , 合并hotfix分支到develop/master并推送
   合并之后 , 可选删除当前hostfix , 若不删除 , 则当前hotfix不可修改 , 若补丁未修复 , 需要从master拉取新的hotfix继续修改

8 . 当进行一个feature时 , 若develop分支有变动 , 如其他开发人员完成功能并上线 , 则需要将完成的功能合并到自己分支上
   即合并develop到当前feature分支
9 . 当进行一个release分支时 , 若develop分支有变动 , 如其他开发人员完成功能并上线 , 则需要将完成的功能合并到自己分支上
   即合并develop到当前release分支 (!!! 因为当前release分支通过测试后会发布到线上 , 如果不合并最新的develop分支 , 就会发生丢代码的情况)

# 结构体

```c
#include<stdio.h>
#include<stdlib.h>
typedef struct Stud{
    int id;
    double grade;
}stud;
stud *stud_sort(stud*);

int main()
{
    int i;
    stud studs[5],*stu;
    for(i=0;i<=4;i++)
    {
    printf("input the id and grade\n");
    scanf("%d %lf",&studs[i].id,&studs[i].grade);
    }
    stu=stud_sort(studs);
    for(i=0;i<=4;i++,stu++)
        printf("%d\t%lg\n",stu->id,stu->grade);
	return 0;

}

stud *stud_sort(stud *studs)
{
    int i,j;
    stud max,temp;

    for(int i=0;i<=4;i++)
    {
        max=studs[0];
        for(int j=1;j<=4-i;j++)
        {
            if(studs[j].grade>max.grade)
               {
                max=studs[j];
               }
            else
              {
                  temp=studs[j];
                  studs[j]=studs[j-1];
                  studs[j-1]=temp;

              }
        }
        studs[4-i]=max;
    }
    return studs;
}

```

# 命令行参数

`agrc`与`agrv`是主函数中的参数，`agrc`表示命令行参数的个数，`agrv`则储存命令行参数，`agrv[0]`储存exe文件名。命令行参数值文件在cmd中运行所带参数。

![](D:\task\屏幕截图 2020-11-09 213956.jpg)

