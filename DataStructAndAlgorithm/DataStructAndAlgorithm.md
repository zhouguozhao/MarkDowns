# DataStructAndAlgorithm

## 树

### 4.4 AVL树
#### 4.4.1 单旋转

`情形一`

![](Resources/AVLTree_SingleRotate1.png)

`情形二`

![](Resources/AVLTree_SingleRotate2.png)

#### 4.4.2 双旋转

`情形一`

![](Resources/AVLTree_DoubleRotate1.png)

`情形二`

![](Resources/AVLTree_DoubleRotate2.png)

#### 实现
`实现类`

![](Resources/AVLTree_JavaClass.png)

`插入`

![](Resources/AVLTree_JavaInsert.png)

`单旋转`

![](Resources/AVLTree_JavaSingleRotateWithLeftChild.png)

`双旋转`

![](Resources/AVLTree_JavaDoubleRotateWithLeftChild.png)

`删除`

![](Resources/AVLTree_JavaDelete.png)





### 4.7 B+树

#### B+树插入和删除

1. 将57插入4-60 B树中，由于插入后L=5，可直接插入（一次磁盘写）

   ![](G:\gitRepos\MarkDowns\MarkDowns\DataStructAndAlgorithm\Resources\BTreeInsert1.png)

![](G:\gitRepos\MarkDowns\MarkDowns\DataStructAndAlgorithm\Resources\BTreeInsert2.png)

2. 将55插入4-61中，由于现在有L+1项，因此需分为2个树叶，保证2个新树叶都有所需的最小记录数。写这2片树叶需要2次磁盘访问，更新父节点需要第三次磁盘访问。分裂相对较少发生，因为每次分裂都会多出约L/2次非分裂插入

   ![](G:\gitRepos\MarkDowns\MarkDowns\DataStructAndAlgorithm\Resources\BTreeInsert3.png)

3. 将40插入4-62中，此时父节点已满，需分裂这个父节点，结果如下。父节点分裂需更新关键字及父节点父亲的值，从而多2次磁盘写（本次插入为5次磁盘写）。该例子存在非叶子节点分裂，当非叶子节点的节点数超过限度时，需沿树向上分裂，直到不需要再分裂父节点，若分裂根，则得到2个根，此时我们建立新的根，分裂的2个树根为它的2个儿子。此为B树增加高度的唯一方式。

   另一种处理儿子过多的方式为领养，把一个儿子交给邻节点。例如把29插入4-63，把32移到下一片树叶。这种方法要求对父节点更改，然而它趋向于使节点更满，在长时间运行中节省空间。

   ![](G:\gitRepos\MarkDowns\MarkDowns\DataStructAndAlgorithm\Resources\BTreeInsert4.png)

4. 从4-63删除99。如果被删元所在的树叶数据项已经是最小值，那么可以从邻节点领养一个来矫正。若邻节点也是最小数据项，那么可以合并2个树叶，如果发生父节点的节点数小于最小值，则一路向上合并，若根只剩一个节点，则删除根，剩余的节点作新根。

   ![](G:\gitRepos\MarkDowns\MarkDowns\DataStructAndAlgorithm\Resources\BTreeRemove1.png)