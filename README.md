Download Link: https://assignmentchef.com/product/solved-ve280-lab-8
<br>
<em>Note: You do not need to read this background to finish this lab, but you may find it helpful if you read it.</em>

After experiencing <em>Blackjack</em> and <em>The Disappearance of Suzumiya Haruhi</em>, Kyon want to write down these two special experiences. However, the complicated game rule and the jumping timeline really puzzled Kyon. Below is from Kyon’s monologue.

The game experience in November was really impressive. We chose to be players with bankroll 100 and maximum hand of 20 to compete Stardust Crusaders. Koizumi Itzuki chose to be a counting player, since he was really worried that Suzumiya

Haruhi might destroy the world if we lost the game. We played 6 rounds in total.

Suzumiya Haruhi beat Joseph Joestar in the first round, but she was kicked out by

Kujo Jotaro in the second round. Her dejection was a real delight to me. After Nagato Yuki entered the game, she won in each round and kicked out all the remaining members of Stardust Crusaders at last. I can only say, that’s the way she is.

Kyon &gt; Do you still remember our playing process of Blackjack?

Yuki.N &gt; There were in total 1402 lines of announcements in the game. The cards were shuffled 23 times. Kujo Jotaro shouted ‘Za Warudo’ for 41 times. He continuously shouted ‘Za Warudo’ for 9 times during the 9th hand with me. At last, I got 139. Kyon &gt; Why did Kujo Jotaro shout ‘Za Warudo’?

Yuki.N &gt; Because he stopped the time and took the same number of cards again.

Kyon &gt; Why didn’t you point out that he cheated?

Yuki.N &gt; Chengsong’s fault. Cannot blame on me.

Who is Chengsong? I don’t know. But Nagato is only an observer, so it is normal for her to keep silent. But it is really inconceivable that someone other than Haruhi can operate on time flow. It is really a miracle that we could beat Stardust Crusade. If we do not have Nagato, we must have lost the game. I want to write down this game experience, but the game rule is so complecated that I myself did not really understand. How about drawing an N-ary tree to help me figure out the rule?




<h1>Task 1: Implementation of N-ary Tree</h1>

<em>Note: You should read this part carefully.</em>

Your first task is to help Kyon implement the class of n-ary tree. A tree ADT organizes and manages data in a hierarchical tree structure. An n-ary tree is a generalization of a binary tree where any node in the tree has exactly one parent, except one node called root node, and any node may have zero up to n children, i.e. n is the <strong>maximum number of child</strong> for each node. For an example, see the following figure:

A tree ADT stores data in each node.




<h2>1.1 Terminology</h2>

<h3>1.1.1 Descendants</h3>

A descendant of a node X is a child of X or a descendant of a child of X.

For instance, the descendants of 2 in the previous figure are 4, 5, 6, 8, and 9.

<h3>1.1.2 Subtree</h3>

A subtree of the tree T is a tree consists of a node in T and all of this node’s descendants.

For instance, if we name the tree above as T, then the tree rooted in 2 is a subtree of T.




Also, the the tree rooted in 6 is a subtree of T.




<h3>1.1.3 Leaf</h3>

A node with no child is called a leaf node. For example, node 4, 5, 8, 9 and 7 are leaf nodes.

<h3>1.1.4 Path</h3>

A path is a sequence of nodes such that a next node in the sequence is a child of the previous one.

For example 2-&gt;6-&gt;9 is a path and the length of this path is 2.

<h3>1.1.5 Height</h3>

The height of a node is the length of a longest path from the node to a leaf.

For example, height(1) = 3, height(9) = 0




<h2>1.2 Implementation</h2>

A node of a tree can be represented by the following class and a tree ADT can be represented by the node corresponding to its root.

class Node {

// OVERVIEW: a node in the n-Ary tree, can also represent a n-ary tree rooted at ‘this’ protected:

int value;      // the integer value of this

int child_num;  // the number of child of this

int n;          // n for this n-Ary tree

Node *parent;   // parent node of this, for root node, parent = NULL

Node **children;

// children is an array of pointer to Node. Therefore, children is a pointer of pointer

int height;     // height of this node

void addChild(Node *child);

// REQUIRES: n of the child node is the same with n of this

// EFFECTS: add the node child to the children array

//          throw an exception tooManyChildren when child_num exceed n     bool equal(Node* sub);

// EFFECTS: return true if the tree rooted at ‘this’ and the tree rooted at ‘sub’

//          have the same shape and value.

public:

Node(int _value, int _n = 2);

// EFFECTS: create a root node with value and n

~Node();

// EFFECTS: destroy the whole tree rooted at sub

void addChild(int _value);

// EFFECTS: create a child node with value and add it to the children array

//          throw an exception tooManyChildren when child_num exceed n

void traverse(vector&lt;int&gt;&amp; traverseValue);

// EFFECTS: insert the value of the nodes into traverseValue using a preorder traversal,

//          A pre-order traversal insert the value of the node

//          and then traverse its child nodes

//          according to the sequence in children array.

//          For example, the value of traverseValue of the tree above is




<strong>Task 2: Output the Tree of a Story in a Pre-order      </strong> <strong>Way and Form a Full Story</strong>

<em>Note: You do not need to read those string arrays and those story-related messages inside the graph if you don’t want to. This is only to test whether your traverse function is correct. If it is, you will see a full story which should be logical. There will be only one test case for this task of which I will not show the detail to you.</em>

Not long after <em>Blackjack</em>, in December, Kyon experienced a more outrageous incident: Suzumiya Haruhi disappeared from his life. The graph below briefly introduced the whole story of Kyon in the format of a n-ary tree.

Each number in the bracket is the index of the string vector storyProcess . Your task is to build a tree like this. The shape should be the same as above and the value in each node should be the same as the number in the bracket, for example, the value of the root node should be 0. Traverse it in a pre-order way, get the index sequence of the story and output the string vector

storyProcess according to the index sequence you get. The index sequence for output is exactly

the same as the pre-order traverse of the tree you build. For example, the pre-order traverse of




<h1>Testing</h1>

Remember to check memory leak by valgrind . Those who failed to avoid memory leak will only get half of the case grade. You will be provided node.h and constant.h files in the starter file.


