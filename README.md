## What is a deadlock.

A: A **lock** occurs when multiple processes try to access the same resource at the same time.
   One process loses out and must wait for the other to finish.

   A **deadlock** occurs when the waiting process is still holding on to another resource that the first needs before it can finish.

   So, an example:

   Resource A and resource B are used by process X and process Y

+ X starts to use A.
+ X and Y try to start using B
+ Y 'wins' and gets B first
+ now Y needs to use A
+ A is locked by X, which is waiting for Y

   The best way to avoid deadlocks is to avoid having processes cross over in this way. Reduce the need to lock anything as much as you can.

   In databases avoid making lots of changes to different tables in a single transaction, avoid triggers and switch to optimistic/dirty/nolock reads as much as possible.

## What is a transaction.
