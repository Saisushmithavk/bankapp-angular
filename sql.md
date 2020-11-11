#### Task #1: Create Database

```sql
create database naresh_db;
use naresh_db;
```

#### Task 2: Create Users table
```sql
create table users(
id int primary key auto_increment,
name varchar(50) not null,
email varchar(50) not null,
password varchar(50) not null,
role varchar(10) not null,
active boolean not null default 1,
created_date timestamp not null default current_timestamp,
modified_date timestamp not null default current_timestamp on update current_timestamp,
unique(email),
check (role in ('USER','ADMIN'))
);
```

##### Task 2.1: Load Sample Data
```sql
insert into users (name,email,password,role) values ( 'Naresh','naresh@gmail.com', 'pass123', 'ADMIN');

insert into users (name,email,password,role) values ( 'Siva','siva@gmail.com', 'pass123', 'USER');

insert into users (name,email,password,role) values ( 'Prabhu','prabhu@gmail.com', 'pass123', 'USER');
```

##### Task 2.2: List All Users
```sql
select * from users;
```

#### Task 3: Create Acccounts 
```sql
-- drop table accounts;
create table accounts 
( 
id bigint primary key auto_increment,
user_id int not null,
account_type varchar(50) not null,
balance int not null default 0,
active boolean not null default 0,
created_date timestamp not null default current_timestamp,
modified_date timestamp not null default current_timestamp on update current_timestamp,
unique ( user_id, account_type),
foreign key (user_id) references users(id)
);
```

#### Task 3.1: Load Sample Data
```sql
insert into accounts ( user_id, account_type) values ( 3,'Personal');

insert into accounts ( user_id, account_type) values ( 3,'Business');

insert into accounts ( user_id, account_type) values ( 4'Personal');
```

#### Task 3.2: List All Accounts ( Admin)
```sql
select * from accounts;
```

#### Task 3.2: Activate Account ( Admin )
```sql
update accounts set active =1 where id = 1;
```

#### Task 3.3: List My Accounts ( Users)
```sql
-- My accounts
select * from accounts where user_id = 3;
```

#### Task 3.4: View my balance
```sql
select balance from accounts where id = 1;
```


