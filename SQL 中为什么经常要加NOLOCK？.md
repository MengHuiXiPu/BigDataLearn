# SQL 中为什么经常要加NOLOCK？

刚开始工作的时候，经常听同事说在SQL代码的表后面加上WITH(NOLOCK)会好一些，后来仔细研究测试了一下，终于知道为什么了。

那么加与不加到底有什么区别呢？

SQL在每次新建一个查询，就相当于创建了一个会话。在不同的查询窗口操作，会影响到其他会话的查询。当某张表正在写数据时，这时候去查询很可能就会一直处于阻塞状态，哪怕你只是一个很简单的SELECT也会一直等待。

我们这里使用事务来往某张表里写数据，我们知道事务在写完表必须提交（COMMIT）或回滚（ROLLBACK）才能释放表，否则会一直处于阻塞状态。

在插入过程中，我们写一个简单的查询语句，在不添加WITH(NOLOCK)和添加WITH(NOLOCK)的情况下，看会发生什么。

**示例数据**

如下表A，是我们新建的一个非常简单的表。

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qFg7eH2dHKfv0G4lmLqe8Y1yDcVylMvXrfhibdXYVI82iaNe1zViaSwBZVM7F8C44h29Kga83Cw2RBDA/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)



下面我们创建一个往里面写数据的事务(使用BEGIN TRAN就可以开始一个事务了)

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qFg7eH2dHKfv0G4lmLqe8Y1NI8JpE6vSRg4cPG4f9gHHEDz4308WDGvktUYuK2LUtOwGj21PoQwHQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

我们发现有1行受影响了，注意这里的会话ID是59（左上角黄色标签上的数字）

**不添加NOLOCK**

我们新建一个查询窗口，然后查询A表

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qFg7eH2dHKfv0G4lmLqe8Y1f1IicasBT5QvJiaffXvicibEgPiaGVrWU8pLKiau6NicReqqABR8COn6qbxicg/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

从上面的查询可以看到，表A被锁住了，我们的查询一直处于阻塞状态。这里的会话ID是60

这个时候如果你在会话59的窗口执行COMMIT或ROLLBACK，会话60的查询结果会立刻显示出来，这里为了下面的演示我们暂时不提交或回滚。

**添加NOLOCK**

我们再新建一个查询窗口，还是查询A表，这次我们加上NOLOCK。

![图片](https://mmbiz.qpic.cn/mmbiz_png/icbViakEeV5qFg7eH2dHKfv0G4lmLqe8Y1HD4ctdCQAESD1pWPsWibibtDbnHfsZia9OXQrXnAMH0kubibcUC35ichWFQ/640?wx_fmt=png&wxfrom=5&wx_lazy=1&wx_co=1)

注意上图标红色的地方，当前会话ID是55，旁边的60还在执行状态，而我们加了NOLOCK后，瞬间就查询出结果了，而且还把事务里即将要插入的数据给查询到了。这是为什么呢？

事务里的数据虽然还没有提交，但是它实际上已经存在内存里面了，这个时候我们使用NOLOCK查询到的结果，实际上还没存储到硬盘。

从上面的两个测试可以看出，**NOLOCK的作用其实就是为了防止查询时被阻塞，只是这样会产生脏读（未提交的数据）。**

那么一般什么情况下使用NOLOCK呢？

通常是一些被频繁写的表，不管是插入，更新还是删除。这样的表在查询时，使用NOLOCK是非常有效的。

**WITH(NOLOCK)和NOLOCK的区别**

不知道小伙伴注意没，我前面介绍时是写的WITH(NOLOCK)，但是测试时，使用的是(NOLOCK)，它们有什么区别呢？

为了搞清楚WITH(NOLOCK)与NOLOCK的区别，我们先看看下面三个SQL语句有啥区别

```
SELECT * FROM A NOLOCK
SELECT * FROM A (NOLOCK);
SELECT * FROM A WITH(NOLOCK);
```

-  (NOLOCK)这样的写法，NOLOCK其实只是别名的作用，而没有任何实质作用。所以不要粗心将(NOLOCK)写成NOLOCK
- (NOLOCK)与WITH(NOLOCK)其实功能上是一样的。(NOLOCK)只是WITH(NOLOCK)的别名,但是在SQL Server 2008及以后版本中，(NOLOCK)不推荐使用了，"不借助 WITH 关键字指定表提示”的写法已经过时了。
- 在使用链接服务器的SQL当中，(NOLOCK)不会生效，WITH(NOLOCK)才会生效。

```
--这样会提示用错误
select * from [IP].[dbname].dbo.tableName with (nolock)
--这样就可以
select * from [dbname].dbo.tableName with(nolock)
```