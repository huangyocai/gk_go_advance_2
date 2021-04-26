# gk_go_advance_2
## Q: 我们在数据库操作的时候，比如 dao 层中当遇到一个 sql.ErrNoRows 的时候，是否应该 Wrap 这个 error，抛给上层。为什么，应该怎么做请写出代码？

## A: dao层在框架设计中主要负责数据的CRUD，不涉及业务。所以对于数据库操作异常时，需要让上层知道，并执行对应的处理。并且对于事务中可能会存在部分SQL执行失败导致rollback，此时如果只是抛出error是无法确认哪个语句执行异常，所以需要对wrap error，提供调用栈，这样便于异常确认
``

## reference
* https://golang.org/pkg/database/sql/
* https://www.jianshu.com/p/403acf6df656
