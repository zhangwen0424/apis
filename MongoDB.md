

## 聚合(aggregate)

### 管道操作符
常用管道	含义
- $group	将collection中的document分组，可用于统计结果
- $match	过滤数据，只输出符合结果的文档
- $project	修改输入文档的结构(例如重命名，增加、删除字段，创建结算结果等)
- $sort	将结果进行排序后输出
- $limit	限制管道输出的结果个数
- $skip	跳过制定数量的结果，并且返回剩下的结果
- $unwind	将数组类型的字段进行拆分

