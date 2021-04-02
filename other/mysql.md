#### 一，数据库的基本操作

```mysql
SHOW DATABASES;
DROP DATABASES database_name;
SHOW ENGINES;
```

综合案例

```shell
mysql -h localhost -u root -p
```

```mysql
CREATE DATABASE zoo;
SHOW DATABASES;
USE zoo;
SHOW CREATE DATABASE zoo;
DROP DATABASE zoo;
```



#### 二，数据表的基本操作

```mysql
CREATE TABLE tb_emp1
(
    id INT(11),
    name VARCHAR(25),
    deptId INT(11),
    salary FLOAT
);

# 主键
CREATE TABLE tb_emp2
(
    id INT(11) PRIMARY KEY,
    name VARCHAR(25),
    deptId INT(11),
    salary FLOAT
);

CREATE TABLE tb_emp3
(
    id INT(11),
    name VARCHAR(25),
    deptId INT(11),
    salary FLOAT,
    PRIMARY KEY(id)
);

CREATE TABLE tb_emp4
(
    name VARCHAR(25),
    deptId INT(11),
    salary FLOAT,
    PRIMARY KEY(name, deptId)
);

# 外键
CREATE TABLE tb_dept1
(
    id INT(11) PRIMARY KEY,
    name VARCHAR(22) NOT NULL,
    location VARCHAR(50)
);

CREATE TABLE tb_emp5
(
    id INT(11) PRIMARY KEY,
    name VARCHAR(25),
    deptId INT(11),
    salary FLOAT,
    CONSTRAINT fk_emp_dept1 FOREIGN KEY(deptId) REFERENCES tb_dept1(id)
);

# 非空约束
CREATE TABLE tb_emp6
(
    id INT(11) PRIMARY KEY,
    name VARCHAR(25) NOT NULL,
    deptId FLOAT,
    CONSTRAIT fk_emp_dept2 FOREIGN KEY (deptId) REFERENCES tb_dept(id)
);

# 唯一性约束
CREATE TABLE tb_dept2
(
    id INT(11) PRIMARY KEY;
    name VARCHAR(22) UNIQUE,
    location VARCHAR(50)
);

```

