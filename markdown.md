# markdown 语法集
[toc]

[toc] 生成文档目录

## 标题
```
# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题

我展示的是一级标题
=================
我展示的是二级标题
-----------------
```
效果：  
# 这是一级标题  
## 这是二级标题  
### 这是三级标题  
#### 这是四级标题  
##### 这是五级标题  
###### 这是六级标题  

我展示的是一级标题
=================
我展示的是二级标题
-----------------


## 字体
```
*这是倾斜的文字*
**这是加粗的文字**
***这是斜体加粗的文字***
~~这是加删除线的文字~~
```
效果：  
**这是加粗的文字**  
*这是倾斜的文字*  
***这是斜体加粗的文字***  
~~这是加删除线的文字~~  


## 段落
段落的换行是使用两个以上空格加上回车


## 引用
```
>这是引用的内容
>>这是引用的内容
>>>>>>>>>>这是引用的内容
```
效果：  
>这是引用的内容
>>这是引用的内容
>>>>>>>>>>这是引用的内容


## 分割线
```
---
----
***
*****
```
效果：  
---
----
***
*****


## 图片
```
![图片alt](图片地址 ''图片title'')
图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加
```
效果：  
![vue](https://ss0.baidu.com/73x1bjeh1BF3odCf/it/u=1681391545,4187928589&amp;fm=85 'vue')


## 超链接
```
[超链接名](超链接地址 "超链接title")
title可加可不加
```
效果：  
[vue](https://vuejs.org/ "vue官网")


## 列表
### 无序列表
```
- 列表内容
+ 列表内容
* 列表内容
注意：- + * 跟内容之间都要有一个空格
```
效果：  
- 列表内容
+ 列表内容
* 列表内容

### 有序列表
```
1.列表内容
2.列表内容
3.列表内容
注意：序号跟内容之间要有空格
```
效果：  
1.列表内容  
2.列表内容  
3.列表内容  


### 列表嵌套
```
- 一级无序列表内容   
   - 二级无序列表内容  
   - 二级无序列表内容  
   - 二级无序列表内容  
上一级和下一级之间敲三个空格即可   
```
效果：  
- 一级无序列表内容   
   - 二级无序列表内容  
   - 二级无序列表内容  
   - 二级无序列表内容  


##  表格
```
表头|表头|表头
---|:--:|---:
内容|内容|内容
内容|内容|内容

第二行分割表头和内容。
- 有一个就行，为了对齐，多加了几个
文字默认居左
-两边加：表示文字居中
-右边加：表示文字居右
注：原生的语法两边都要用 | 包起来。此处省略
```
效果：  
表格表头1|表格表头2|表格表头3
---|:--:|---:
内容|内容|内容
内容|内容|内容

## 代码
```
`单行代码`

(```)
多行代码内容
(```)
括号可省略
```
效果：  
`代码内容`
```
多行代码
```

vscode 中.md文件预览快捷键：command+shift+v


<!-- ## 流程图
```
```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
&```
```
效果：  
```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
&``` -->