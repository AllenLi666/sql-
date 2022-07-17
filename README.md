# sql-

## Task 01
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

## Task 02
2.1 SELECT product_name , regist_date FROM product
WHERE regist_date > '2009-04-28'

2.2 <img width="698" alt="image" src="https://user-images.githubusercontent.com/42401954/178975864-475ce899-6c01-4847-ae95-ad3136c15f28.png">
 <img width="698" alt="image" src="https://user-images.githubusercontent.com/42401954/178975882-497271fc-2943-4638-902d-e5deb0b4e72c.png">
 <img width="698" alt="image" src="https://user-images.githubusercontent.com/42401954/178975886-de2c6e41-e9e9-4aa5-9cc6-220f8aea5730.png">

2.3   SELECT product_name, sale_price, purchase_price
FROM product
WHERE sale_price - purchase_price >= 500;

2.4 SELECT product_name,product_type, (sale_price * 0.9 - purchase_price) as profit 
FROM product
WHERE sale_price * 0.9 - purchase_price > 100

2.5 WHERE应在GROUP BY 之前

2.6 SELECT product_type, SUM(sale_price) AS sum_sale, SUM(purchase_price) AS sum_pur_price
FROM product
GROUP BY product_type
HAVING SUM(sale_price) > (SUM(purchase_price)) * 1.5;

## Task 03

3.1  CREATE VIEW ViewPractice5_1 (product_type, sale_price,regist_date)
AS
SELECT product_type,sale_price,regist_date
  FROM product
  where sale_price>=1000 
        and regist_date="2009-09-20";
        
3.2 <img width="1104" alt="image" src="https://user-images.githubusercontent.com/42401954/179404743-565fb587-2dec-4ea5-a25e-73eaf340b64e.png">

3.3 select product_id ,product_name ,product_type ,sale_price ,
       (SELECT AVG(sale_price)  
               from product ) as sale_price_avg
from product

3.4  CREATE VIEW AvgPriceByType (product_id,product_name ,product_type ,sale_price ,sale_price_avg_type)
AS
select product_id,product_name ,product_type ,sale_price ,
                     (SELECT AVG(sale_price)
                       FROM product AS p2
                      WHERE p1.product_type = p2.product_type
                      GROUP BY product_type) as sale_price_avg_type
from product as p1 ;

3.5 是

3.6 

3.7 SELECT sum(case when sale_price<= 1000 then 1  else 0 end) as low_price,
       sum(case when sale_price between 1001 and 3000 then 1  else 0 end) as mid_price,
       sum(case when sale_price> 3000 then 1  else 0 end) as high_price
  FROM product;






