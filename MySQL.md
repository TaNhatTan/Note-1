## MySQL

* **[I. Simple command](#I)**
* **[II. Advanced command](#II)**
* **[III. Check info](#III)**

<a name="I"></a>
#### I. SIMPLE COMMAND:
##### 1. Show index from table:
```
   SHOW INDEX FROM TABLE;
```

##### 2. Create database user:
```
   GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password';
```

##### 3. Create database:
```
	CREATE DATABASE dbname;
```

##### 4. Create database with UTF-8:
```
  CREATE DATABASE mydatabase CHARACTER SET utf8 COLLATE utf8_general_ci;
```

<a name="II"></a>
#### II. ADVANCED COMMAND
##### 1. Allow Remote access:
```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;
mysql> FLUSH PRIVILEGES;
```

##### 2. Reset password
```
$ mysqld_safe --skip-grant-tables &
$ mysql -u root
mysql> use mysql;
mysql> update user set password=PASSWORD("pass") where User='root';
mysql> flush privileges;
```

<a name="III"></a>
#### III. CHECK INFO
##### 1 Show size of database:
```
mysql> SELECT table_schema "DB Name",
        ROUND(SUM(data_length + index_length) / 1024 / 1024, 1) "DB Size in MB"
FROM information_schema.tables
GROUP BY table_schema;
```

Nguồn: https://github.com/TraiOi/d7b3560525906f386528ca7d588ee5e9/blob/master/MyNote/MySQL.md
