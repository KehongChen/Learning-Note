# MySQL Learning Note

## 1 Database Management

### 1.1 Basic Command
*Based on Terminal:*  

```sql
show databases;  
create database database_name default charset utf8 collate utf8_general_ci;  
drop database database_name;  
use database_name;
```

### 1.2 Based on Python
```python
import pymysql
#linked ot mysql
conn = pymysql.connect(host="localhost", port=3306, user="root", passwd="PASSWORD", db='example', charset="utf8")
cursor = conn.cursor()

#review the database
cursor.execute('show databases')
result = cursor.fetchall()
print(result)

#create a database
cursor.execute('create database example_database default charset utf8 collate utd8_general_ci')
conn.commit() #Necessary for creating, deleting, modifying the database

#close the link
cursor.close()
conn.close()
```

## 2 Table Management

### 2.1 Basic Command 
#### 2.1.1 Create a Table
```sql
create table table_name(column_name, type,column_name, type)default charset=utf8;
```

*Examples*  
```sql
create table example(
         id int, 
         name verchar(16)
                    )default charset=utf8;

create table example(
         id int,           
         name verchar(16) not null  -- no permission to be null
                    )default charset=utf8;

create table example(
         id int primary key,        -- not null, no repeat
         name verchar(16)  
                    )default charset=utf8;

create table example(
         id int auto_increment,     -- automatically increase
         name verchar(16)  
                    )default charset=utf8;
```
#### 2.1.2 Delete and Clear a table
Drop:
```sql
Drop table table_name;
```
Clear: 
```sql
delete from table_name;  
truncate table table_name; --fast but unrecoverable
```

#### 2.1.3 Modify a table
Add and Drop column: 
```sql
alter table table_name add column_name type; 
--default, not null, auto_increment can be added at the end
drop table table_name drop column column_name;
```
Modify the column:
```sql
alter table table_name modify column column_name type; -- modify the column type
alter table table_name change column_name new_column_name type; -- modify the column name and type
alter table table_name alter column_name set default amount; -- modify the default amount
alter table table_name alter column_name drop default; -- drop the default amount
alter table table_name add primary key column_name; -- add a primary key
alter table table_name drop primary key; -- drop primary key
```

## 3 Column type
### 3.1 Common Column types

**int**:

```sql
[tiny] [big] int [unsigned] [zerofill]
```

**decimal:**

```sql
decimal [(m[,d])] [unsigned] [zerofill]
-- m: amount of the number of whole number
-- d: amount of the number after '.' 

float [(m[,d])] [unsigned] [zerofill]
double [(m[,d])] [unsigned] [zerofill]
```

**varchar**

```sql
char(m) -- fixed length, fixed using m characters storage, up to 255 characters
varchar(m) -- variable length, stored by actual length, up to 65535 bytes
```

**time**

```sql
datatime -- YYYY-MM-DD HH:MM:SS
timestamp -- YYYY-MM-DD HH:MM:SS, storage as the UTC timestamp
date -- YYYY-MM-DD
time -- HH:MM:SS
```







