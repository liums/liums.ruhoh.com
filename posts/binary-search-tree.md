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
	
这个是查找，如果没找到返回nullptr，当然这次只是学习不是产品级的所以后面其他相关代码都没做检测。

	template <typename BST_t>
		BST_t* minimum (BST_t *root) {
    	while (root->l != nullptr)
        	root = root->l;
    	return root;
	}
	
求最大值，最小值类似就不贴了。
	
	template <typename BST_t>
	BST_t* successor (BST_t *root) {
    	if (root->r != nullptr)
        	return minimum(root->r);
    	BST_t *t = root->p;
    	while (t != nullptr && root == t->r)
        	root = t, t = t->p;
    	return t;
	}
	
求后驱，前驱类似也不贴了。