## MultiCoreTree - Time Efficient Balanced BST
MultiCoreTree is an implementation of binary search tree using the parallel processing offered by modern multi-core processors. Instead of using a single balanced BST, this tree will create as many BSTs as configured. Will balance the inserts across the trees. If three cores are used then the operations would be as follows:-

**search** - O(logn/3). Three trees are searched by one thread each in parallel. Which ever finds the element aborts the search of other threads.

**insert** - O(2/3logn). Three trees are searched for element's existence, O(logn/3). Then the tree with minimum size is chosen and element is added in it, O(logn/3). Total, O(2/3logn).

**delete** - O(logn/3). Three trees are searched by one thread each in parallel. Which ever finds the element, deletes it and then aborts the operation of other threads.

Thread to CPU core mapping is beyond the scope of this implementation and left to the user. Thread affinity concepts can be explored for the purpose. This implementation shows how to use Java concurrent features to reduce time complexities of BST operations when each worker thread is linked to a core and all of them can run in parallel.
