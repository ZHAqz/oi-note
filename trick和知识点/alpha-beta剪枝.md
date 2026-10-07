## alpha-beta搜索（min-max搜索）：

简称mfs，用来解决双方最优决策博弈问题。 \*\*核心思想：\*\*在搜索树中，下一层越小，对当前层越有利，由于取max，一旦下一层出现了比其他孩子结果更大的值，那么停止搜索。（最优性剪枝）。 **模板：**

```cpp
//upd是本层值，将传给下一层。
//lim是上一层给这一层的下限。
//op决定本层是先手还是后手（可能无用）。
int mfs(int upd,int lim,int op){
//	判断mfs终止。

//	贪心地选择合适的mfs顺序（先走结果可能大的）

	for(/*枚举*/){
    
        //做操作
        
        val=-mfs(-lim,-(upd-V),-op)+V;
        //V是走这一步的贡献
        //对手的结果对自己取负。
        //自己的lim滚动给孩子的upd，使同一个人一直是同一个变量
        //因为实际结果比里面会＋V，所以lim要比实际的-V。
        //op取负，换下一个人。
        
        //回溯
        
        if(val >= lim)	return INF;//剪枝
        if(val > upd)	upd=val;//更新
    }
    return upd;
}
```

作者：Smeow    创建时间：2019-02-14 17:09:02



-   min-max搜索
-   alpha-beta搜索（min-max搜索）：