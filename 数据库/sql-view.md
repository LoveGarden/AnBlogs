# SQL深入理解|从子查询到视图

# 子查询

子查询就是以另一个查询的结果作为本次查询的输入，一个SQL语句中存在多个`select`的情况。查询之间不同的联合方式，可以分成多种子查询。

## `in`关键字

`in`表示「是否存在于另一个集合」，这样的功能意味着它只能用于「条件筛选」，也就是`where`语句。「另一个」集合有两种表达方式，一种是由大括号产生的，另一种是一个查询。

前者相对简单，如要查找来自物理学院和数学学院的学生：

```sql
select * from student where department in ('physics', 'math');
```

后者极大地扩充了SQL的功能，使得一次查询可以拆分为多个阶段，这也就是「子查询」的价值所在。

作为条件筛选的一项，应该放到`where`语句中。如要查找二班`student_class2`中学生选课的情况：

```sql
select * from takes where ID in (select ID from student_class2);
```

括号中的就是所谓「子查询」，依附在「父查询」下。其中，子查询`select`后罗列的「列名」必须和「父查询」中罗列的列名相对应，如上面的`ID`就是相对应的。

可以同时判断多个属性是否在某集合中，同样要求

## 量词



