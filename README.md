## What is a deadlock.

A **lock** occurs when multiple processes try to access the same resource at the same time.
One process loses out and must wait for the other to finish.

A **deadlock** occurs when the waiting process is still holding on to another resource that the first needs before it can finish.

So, an example:

Resource A and resource B are used by process X and process Y

+ `X` starts to use `A`.
+ `X` and `Y` try to start using `B`
+ `Y` 'wins' and gets `B` first
+ Now `Y` needs to use `A`
+ `A` is locked by `X`, which is waiting for `Y`

The best way to avoid deadlocks is to avoid having processes cross over in this way. Reduce the need to lock anything as much as you can.

In databases avoid making lots of changes to different tables in a single transaction, avoid triggers and switch to optimistic/dirty/nolock reads as much as possible.

## What is a transaction.

A transaction is a unit of work that you want to treat as "a whole". It has to either happen in full, or not at all.

A classical example is transferring money from one bank account to another. To do that you have to first withdraw the amount from the source account, and then deposit it to the destination account. The operation has to succeed in full. If you stop halfway, the money will be lost, and that is Very Bad.

In modern databases transactions also do some other things - like ensure that you can't access data that another person has written halfway. But the basic idea is the same - transactions are there to ensure, that **no matter what happens, the data you work with will be in a sensible state**. They guarantee that there will NOT be a situation where money is withdrawn from one account, but not deposited to another.
