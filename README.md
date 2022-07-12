# sql-
1. CREATE TABLE Addressbook
(regist_no    INT      NOT NULL,
name   VARCHAR(128) NOT NULL,
address   VARCHAR(256)  NOT NULL,
tel_no     CHAR(10)    ,
mail_address  CHAR(20) ,
PRIMARY KEY (regist_no)); 

2. ALTER TABLE Addressbook ADD COLUMN postal_code VARCHAR(8) NOT NULL;

3. Drop table Addressbook;

4. 删除的表是无法恢复的，即使是误删。只能重新创建该表，然后重新插入数据。
