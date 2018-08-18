---
layout: post
title: 事务
date: 2018-08-18 14:15:27
categories: 
- spring
tags:
- java
- spring
- transaction
description: 事务
---


### 事务的隔离级别
#### PROPAGATION_NOT_SUPPORTED
1. 如果在方法中使用这个，则以非事务方式运行。
2. 如果当前存在事务、则两个事务是独立的。互不影响。

#### PROPAGATION_REQUIRED
1. 如果当前没有事务，就新建一个事务。
2. 如果已经存在一个事务中，加入到这个事务中。这是最常见的选择(默认)。 换言之是同一个事务，要么同时成功，要么同时失败。

#### PROPAGATION_SUPPORTS
Should roll back transaction but cannot - no transaction available
1. 支持当前事务，如果当前没有事务，就以非事务方式执行。
总结：一个事务方法A调用另一个事务方法B时，B如果报错事务就已经是回滚状态了，放回到A之后，A方法继续执行，提交了事务（已经是回滚状态的事务），就报错了 Transaction marked as rollback only。

#### PROPAGATION_MANDATORY
org.springframework.transaction.IllegalTransactionStateException: No existing transaction found for transaction marked with propagation 'mandatory'
1. 使用当前的事务（ 换言之是同一个事务），如果当前没有事务，就抛出异常。

#### PROPAGATION_REQUIRES_NEW
1. 新建事务，如果当前存在事务，把当前事务挂起。(新开的事务与原有的事务没有关系，独立的两个事务)。

#### PROPAGATION_NEVER
Should roll back transaction but cannot - no transaction available
1. 以非事务方式执行，如果当前存在事务，则抛出异常。
org.springframework.transaction.IllegalTransactionStateException: Existing transaction found for transaction marked with propagation 'never'

#### PROPAGATION_NESTED
1. 如果当前存在事务，则在嵌套事务内执行。
2. 如果当前没有事务，则执行与PROPAGATION_REQUIRED类似的操作。
org.springframework.transaction.NestedTransactionNotSupportedException: JpaDialect does not support savepoints - check your JPA provider's capabilities
当使用PROPAGATION_NESTED时，底层的数据源必须基于JDBC 3.0，并且实现者需要支持保存点事务机制

测试方法：
@Transactional
结合
DefaultTransactionDefinition def = new DefaultTransactionDefinition();
  def.setIsolationLevel(TransactionDefinition.ISOLATION_REPEATABLE_READ);
  def.setPropagationBehavior(TransactionDefinition.PROPAGATION_NESTED);
  // def.setTimeout(15);
  TransactionStatus status = transactionManager.getTransaction(def);