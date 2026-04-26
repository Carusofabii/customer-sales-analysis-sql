create database CustomerESalesAnalysis;

create table customers (
 customer_id int
, nome varchar(50)
, city varchar(50)
,constraint PK_PRODUCT primary key (customer_id));

create table orders (
order_id int
,customer_id int
, order_date date
, total_amount decimal (10,2)
,constraint PK_orders primary key (order_id)
, constraint FK_customers_orders foreign key (customer_id) 
references customers (customer_id)) ;

create table order_items(
order_id int
, product varchar(50)	
, quantity int
, price decimal (10,2)
,constraint FK_orders_order_items foreign key (order_id) references orders (order_id));

insert into customers values 
(1 , "Giulia" , "Custozza")
,(2, "Antonietta", "Dossobuono")
,(3, "Lauretta", "Vicenza")
,(4,"Giovanna", "San Massimo")
, (5, "SabrinaB","Verona")
, (6, "SabrinaZ", "Verona")
, (7, "Diana", "Bussolengo")
, (8, "Marco", "Valpolicella")
, (9, "Michela", "San Giovanni Lupatoto")
, (10, "Isabella", "Villafranca")
, (11, "Elena", "Castel d'Azzano")
, (12, "Claudia", "Nogarole");

INSERT INTO orders VALUES
(1, 1, '2024-01-10', 120.00),
(2, 2, '2024-01-12', 80.00),
(3, 1, '2024-02-05', 150.00),
(4, 3, '2024-02-10', 200.00),
(5, 4, '2024-02-15', 60.00),
(6, 5, '2024-03-01', 300.00),
(7, 6, '2024-03-03', 90.00),
(8, 2, '2024-03-10', 110.00),
(9, 7, '2024-03-12', 75.00),
(10, 8, '2024-03-15', 220.00),
(11, 9, '2024-04-01', 130.00),
(12, 10, '2024-04-05', 95.00),
(13, 1, '2024-04-10', 180.00),
(14, 11, '2024-04-12', 70.00),
(15, 12, '2024-04-15', 160.00),
(16, 3, '2024-04-18', 140.00),
(17, 5, '2024-04-20', 250.00),
(18, 6, '2024-04-22', 85.00);


INSERT INTO order_items VALUES
(1, 'Trattamento Viso', 2, 60.00),
(2, 'Massaggio', 1, 80.00),
(3, 'Trattamento Viso', 3, 50.00),
(4, 'Pacchetto Relax', 1, 200.00),
(5, 'Pulizia Viso', 1, 60.00),
(6, 'Pacchetto Premium', 2, 150.00),
(7, 'Massaggio', 1, 90.00),
(8, 'Pulizia Viso', 2, 55.00),
(9, 'Trattamento Corpo', 1, 75.00),
(10, 'Pacchetto Premium', 1, 220.00),
(11, 'Trattamento Viso', 2, 65.00),
(12, 'Massaggio', 1, 95.00),
(13, 'Pacchetto Relax', 1, 180.00),
(14, 'Pulizia Viso', 1, 70.00),
(15, 'Pacchetto Premium', 1, 160.00),
(16, 'Trattamento Corpo', 2, 70.00),
(17, 'Pacchetto Premium', 1, 250.00),
(18, 'Massaggio', 1, 85.00);



-- Spesa media per cliente
select nome
, avg(total_amount)
from orders as o
join customers as c
on c.customer_id = o.customer_id
where total_amount > 100
group by nome ;

-- Prezzo medio dei prodotti 
select product
, avg(quantity * price) as prezzomedio
from order_items 
group by product ;

-- Totale vendite per mese
select month(order_date) as mese,
sum(total_amount)
from orders
group by mese
order by mese;

-- Percentuale di fatturato per prodotto
SELECT 
product,
SUM(quantity * price) AS ricavi,
SUM(quantity * price) / (
        SELECT SUM(quantity * price) FROM order_items
    ) * 100 AS percentuale_ricavi
FROM order_items
GROUP BY product;

-- Top 3 clienti per spesa
select nome
, sum(total_amount) as totale_speso
from customers as c
join orders as o on c.customer_id = o.customer_id
group by nome
order by totale_speso desc 
limit 3;

