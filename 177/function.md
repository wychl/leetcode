UDF可以没有参数，但是必须有必须有一个返回值

## 语法
### 创建function
```sql
CREATE FUNCTION func_name ( [func_parameter] ) //括号是必须的，参数是可选的  
RETURNS type  
[ characteristic ...] routine_body  
```

- CREATE FUNCTION 用来创建函数的关键字；

- func_name 表示函数的名称；

- func_parameters为函数的参数列表，参数列表的形式为：[IN|OUT|INOUT] param_name type

- IN：表示输入参数；

- OUT：表示输出参数；

- INOUT：表示既可以输入也可以输出；

- param_name：表示参数的名称；

- type：表示参数的类型，该类型可以是MySQL数据库中的任意类型；

- RETURNS type：语句表示函数返回数据的类型；

- characteristic: 指定存储函数的特性，取值与存储过程时相同，详细请访问－MySQL存储过程使用;

### 定义变量
`DECLARE var_name[,varname]...data_type [DEFAULT VALUE];`

变量的作用范围是在BEGIN...END中,定义变量语句必须紧接着BEGIN语句之后定义

**example**
```sql
DELIMITER 
CREATE FUNCTION addTwoNumber(x SMALLINT UNSIGNED, Y SMALLINT UNSIGNED) 
RETURNS SMALLINT
BEGIN
DECLARE a, b SMALLINT UNSIGNED DEFAULT 10;
SET  a = x, b = y;
RETURN a+b;
END
```

### 变量赋值
```sql
SET parameter_name = value[,parameter_name = value...]

SELECT INTO parameter_name
```
**example**
```sql
DECLARE x int;
SELECT COUNT(id) FROM tdb_name INTO x;
RETURN x;
END
```

### 定义用户级别的变量
`SET @param_name = value`,其作用域只为当前用户的客户端有效

**example**
```sql
SET @allParam = 100;
SELECT @allParam;
```

### 流程控制语句
- IF语句

语法
```sql
IF search_condition THEN statement_list 
[ELSEIF search_condition THEN statement_list] ... 
[ELSE statement_list] 
END IF 
```
- CASE
    - CASE 1
        ```sql
        CASE case_value 
        WHEN when_value THEN statement_list 
        [WHEN when_value THEN statement_list] ... 
        [ELSE statement_list] 
        END CASE 
        ```
**example**
```sql

```

    - CASE 2
        ```sql
        CASE 
        WHEN search_condition THEN statement_list 
        [WHEN search_condition THEN statement_list] ... 
        [ELSE statement_list] 
        END CASE 
        ```
**example**
```sql

```    

**example**
```sql
IF age>20 THEN SET @count1=@count1+1;  
ELSEIF age=20 THEN SET @count2=@count2+1;  
ELSE SET @count3=@count3+1;  
END IF; 
```

### 调用function
```sql
SELECT function_name(parameters,...)
```

### 删除function 
```sql
DROP FUNCTION function_name
```
