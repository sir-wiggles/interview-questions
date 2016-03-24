## What is a deadlock.

A **lock** occurs when multiple processes try to access the same resource at the same time.
One process loses out and must wait for the other to finish.

A **deadlock** occurs when the waiting process is still holding on to another resource that the first needs before it can finish.

So, an example:

Resource _A_ and resource _B_ are used by process _X_ and process _Y_

+ _X_ starts to use _A_.
+ _X_ and _Y_ try to start using _B_
+ _Y_ 'wins' and gets _B_ first
+ Now _Y_ needs to use _A_
+ _A_ is locked by _X_, which is waiting for _Y_

The best way to avoid deadlocks is to avoid having processes cross over in this way. Reduce the need to lock anything as much as you can.

In databases avoid making lots of changes to different tables in a single transaction, avoid triggers and switch to optimistic/dirty/nolock reads as much as possible.

## What is a transaction.

A **transaction** is a unit of work that you want to treat as "a whole". It has to either happen in full, or not at all.

A classical example is transferring money from one bank account to another. To do that you have to first withdraw the amount from the source account, and then deposit it to the destination account. The operation has to succeed in full. If you stop halfway, the money will be lost, and that is Very Bad.

In modern databases transactions also do some other things - like ensure that you can't access data that another person has written halfway. But the basic idea is the same - transactions are there to ensure, that **no matter what happens, the data you work with will be in a sensible state**. They guarantee that there will NOT be a situation where money is withdrawn from one account, but not deposited to another.

## (Code)
Given the following tree, describe the nodes at every level.

Level     Tree
1:          A
           / \
2:        B   C
         / \   \
3:      D  E    F
               / \
4:            G   H

Output:
Level 1: A
Level 2: B, C
Level 3: D, E, F
Level 4: G, H
