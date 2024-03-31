+++
date = 2024-03-10T08:26:51-16:27
+++
# Binary Tree
Many exercises from [CodeSignal Interview Practice trail for Trees](https://app.codesignal.com/interview-practice/topics/trees-basic).

### Binary Tree Class
```
# Binary trees are already defined with this interface:
class Tree(object):
   def __init__(self, x):
      self.value = x
      self.left = None
      self.right = None
```
### hasPathWithGivenSum
Given a binary tree `t` and an integer `s`, determine whether there is a root to leaf path in `t` such that the sum of vertex values equals `s`.
```
def sumInPath(t, s, total):
    if not t:
        return False

    total += t.value
    if not t.left and not t.right and total == s:
        return True

    leftInPath = sumInPath(t.left, s, total)
    rightInPath = sumInPath(t.right, s, total)
    return leftInPath or rightInPath

return sumInPath(t, s, 0)
```
### isTreeSymmetric
Given a binary tree `t`, determine whether it is symmetric around its center, i.e. each side mirrors the other.
```
def isMirror(left, right):
    if not left and not right:
        return True
    if not left or not right:
        return False

    isMirrorLeft = isMirror(left.left, right.right)
    isMirrorRight = isMirror(right.left, left.right)
    return left.value == right.value and isMirrorLeft and isMirrorRight

if not t:
    return True
return isMirror(t.left, t.right)
```
### findProfession
Consider a special family of Engineers and Doctors. This family has the following rules:

Everybody has two children.
The first child of an Engineer is an Engineer and the second child is a Doctor.
The first child of a Doctor is a Doctor and the second child is an Engineer.
All generations of Doctors and Engineers start with an Engineer.
We can represent the situation using this diagram:
```
                E
           /         \
          E           D
        /   \        /  \
       E     D      D    E
      / \   / \    / \   / \
     E   D D   E  D   E E   D
```
Given the level and position of a person in the ancestor tree above, find the profession of the person.
**Note:** in this tree first child is considered as left child, second - as right.
```
def solution(level, pos):
    if level == 1:
        return "Engineer"

    parentPos = (pos + 1) // 2 
    parentProfession = solution(level - 1, parentPos)

    if pos % 2 == 1:
        return "Engineer" if parentProfession == "Engineer" else "Doctor"
    else:
        return "Doctor" if parentProfession == "Engineer" else "Engineer"
```
### kthSmallestInBST
A tree is considered a binary search tree (BST) if for each of its nodes the following is true:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and the right subtrees must also be binary search trees.
Given a binary search tree `t`, find the `k<sup>th</sup>` smallest element in it.

Note that `k<sup>th</sup>` smallest element means `k<sup>th</sup>` element in increasing order. See examples for better understanding.
```
# O(n) space solution
def solution(t, k):
    def inOrderTraversal(t):
        if not t:
            return []
        return inOrderTraversal(t.left) + [t.value] + inOrderTraversal(t.right)

    sortedElements = inOrderTraversal(t)
    return sortedElements[k - 1]
```
```
# O(1) space solution
def solution(t, k):
    count = 0
    kth_smallest = None

    def visit(node):
        nonlocal count, kth_smallest
        count += 1
        if count == k:
            kth_smallest = node.value

    morrisTraversal(t, visit)
    return kth_smallest

def morrisTraversal(node, visit):
    while node:
        if not node.left:
            visit(node)
            node = node.right
        else:
            predecessor = node.left
            while predecessor.right and predecessor.right != node:
                predecessor = predecessor.right

            if not predecessor.right:
                predecessor.right = node
                node = node.left
            else:
                predecessor.right = None
                visit(node)
                node = node.right
```
### isSubtree
Given two binary trees `t1` and `t2`, determine whether the second tree is a subtree of the first tree. A subtree for vertex `v` in a binary tree `t` is a tree consisting of `v` and all its descendants in `t`. Determine whether or not there is a vertex `v` (possibly none) in tree `t1` such that a subtree for vertex `v` (possibly empty) in `t1` equals `t2`.
```
     t1:              t2:
      5               10
     / \             /  \
    10  7           4    6
   /  \            / \    \
  4    6          1   2   -1
 / \    \
1   2   -1
```
As you can see, `t2` is a subtree of `t1` (the vertex in `t1` with value `10`). The output should be `solution(t1, t2) = true`.
```
def solution(t1, t2):
    if not t2:
        return True

    if t1:
        if t1.value == t2.value and isSubtree(t1, t2):
            return True
        return solution(t1.left, t2) or solution(t1.right, t2)
    return False

def isSubtree(t1, t2):
        if not t1:
            return not t2
        if not t2:
            return not t1

        return t1.value == t2.value and isSubtree(t1.left, t2.left) and isSubtree(t1.right, t2.right)
```
