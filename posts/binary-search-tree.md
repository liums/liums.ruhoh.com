---
title: Binary Search Tree
date: '2012-11-28'
description: 记录各种二叉搜索树的学习过程
tagline: AVL, RBT, Splay, SBT, Treap...
tags: ['Data Structure', 'OI']
categories: Computer-Science
---
闲的无聊，开始研究各类BST。

首先先撸了一个公用模板库方便测试，包括了打印、查找、求最大最小值和前驱后驱。

	#include <iostream>
	
	template <typename BST_t>
	void printBST (BST_t *root, std::ostream &out) {
    	if (root == nullptr) return;
    	printBST(root->l, out);
    	out << root->k << ' ';
    	printBST(root->r, out);
	}
	
上面这段是输出整个树，简单的中续遍历。

	template <typename BST_t>
	BST_t* searchBST (BST_t *root, int key) {
    	while (root != nullptr && key != root->k) {
        	if (key < root->k)
            	root = root->l;
        	else root = root->r;
    	}
    	return root;
	}
	
这是查找，如果没找到返回nullptr，当然这次只是学习不是产品级的玩意，返回啥都无所谓。

	template <typename BST_t>
		BST_t* minimum (BST_t *root) {
    	while (root->l != nullptr)
        	root = root->l;
    	return root;
	}
	
这是求最小值，求最大值类似就不贴了。
	
	template <typename BST_t>
	BST_t* successor (BST_t *root) {
    	if (root->r != nullptr)
        	return minimum(root->r);
    	BST_t *t = root->p;
    	while (t != nullptr && root == t->r)
        	root = t, t = t->p;
    	return t;
	}
	
这是求后继，求前驱类似也不贴了。

最基本的BST
===
一直以为这货很简单，突然发现哪怕是它，删除操作都显得那么复杂。

	struct node {
        int k;
        node *l, *r, *p;
    };

node是树的节点类型，Destructor什么的请直接无视。只有一个key，和左右子树与父亲节点。

插入操作很好实现，和查找很类似：

	void plainBST::insert (int v) {
    	node *t = root, *t1 = nullptr,
    	*t2 = new node {v, nullptr, nullptr, nullptr};
    	while (t != nullptr) {
    	    t1 = t;
    	    if (t2->k < t->k)
    	        t = t->l;
    	    else t = t->r;
    	}
    	t2->p = t1;
    	if (t1 == nullptr)
    	    root = t2;
    	else if (t2->k < t1->k)
    	    t1->l = t2;
    	else t1->r = t2;
	}
	
t2是新节点，t1则是其父亲节点，中间先用查找-like的方式找到t1，如果t1为空，即树为空，则root = t2。否则看是插左子树还是右子树。很容易理解。

删除操作相比之下要复杂多了，情况很绕人。一开始先写了一半，发现太恶心了，又删了重来：

	void plainBST::erase (node *n) {
    	auto transplant = [&](node *u, node *v) {
        	if (u->p == nullptr) root = v;
        	else if (u == u->p->l)
            	u->p->l = v;
        	else u->p->r = v;
        	if (v != nullptr) v->p = u->p;
    	};
    	if (n->l == nullptr) transplant(n, n->r);
    	else if (n->r == nullptr) transplant(n, n->l);
    	else {
        	node *t = minimum(n->r);
        	if (t->p != n) {
            	transplant(t, t->r);
        	    t->r = n->r;
    	        t->r->p = t;
    	    }
    	    transplant(n, t);
    	    t->l = n->l;
    	    t->l->p = t;
    	}
	}

怎么连Lambda Expression都用上了，还不是想install B来攒点RP嘛！（才得喜讯NOIP 2012提高一等奖分数线极低，虽然感觉这个一等奖啥用都没有-_-#）

不扯淡了。transplant(u, v)把u直接替换为v，并且维护好v和v的新父亲之间的关系，**毫无疑问**这代码要出现很多次，又觉得在类中再定义一个函数很烦......

然后分析一下erase操作的主体，如果待删除节点左子树是空的，直接把右子树“提”上来；如果右子树是空的，同理。否则找到n的后继，即右子树的最小节点；如果它就是待删除节点的右孩子，然后直接“提”上来，把左子树嫁接过去，否则把它的右孩子嫁接到自己的位子上，再把待删除节点的右孩子变为自己的右孩子，然后就和前面一个情况一模一样了。

有点绕？回去再读一遍...代码。

好了，下面对plainBST做一点小小的封装啊什么的，一个无比坑爹的BST就诞生了（好吧正常情况下工作还算稳定）！休息一下，坐等AVL什么的重量级人物上场！！！

