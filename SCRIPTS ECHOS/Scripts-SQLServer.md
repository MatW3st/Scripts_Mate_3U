# Scripts de SQL Server
**_Juan Mateo Hernández De Luna_ pt.2**

 **use tdasjoins (la mera buena)** 
 **USANDO INNERJOIN**


select * from categoria2
select * from producto

**Obtener información de categorías y productos**

select c.CategoryID as 'Clave categoria',
c.CategoryName as 'Nombre categoria',
p.nombreProucto as 'Descripcion del prodcuto',
p.precioUnitario as 'Precio',
p.existencia as 'existencia',
(preciounitario * existencia) as total
from categoria2 as c
join producto as p
on c.CategoryID = p.categoria

**Ver la informaciond de categorías y productos con condicional**

select *, (preciounitario * existencia) as total 
from 
categoria2 as c
inner join 
(select nombreProucto,
precioUnitario,
existencia, categoria
from producto) as p 
on c.CategoryID = p.categoria


select *, (preciounitario * existencia) as total ,
case  
when preciounitario = 0 then 'precio no existente'
when preciounitario >=1 and preciounitario <=100 then 
'precio medio'
else'precio mayor'
end as 'Datos Precio'
from 
categoria2 as c
inner join 
(select nombreProucto,
precioUnitario,
existencia, categoria
from producto) as p 
on c.CategoryID = p.categoria


**usando northwind, seleccionar las categorias y los producto que se tienen en la base de datos nombre de la categoria, nombre del pruse**

use Northwind
select * from categories
select * from Products

select CategoryName,ProductName from
(select CategoryID, CategoryName from Products) as c
inner join
(select ProductID, CategoryID from Products) as p
on c.CategoryID = p.CategoryID


**Cuantos productos se tiene por categoria**
select * from Products
select * from Categories

select categoryId,(select count(*) from Products) as 'numero de prodcutos'
from Products```

**seleccionar el numerod e prodcutos de categoria pero que contengan el nombre de la categoria**

select CategoryName as 'categoria', count(*) as 'numero de productos' from
(select categoryId, categoryname from Categories) as c
inner join
(select ProductName, CategoryID from Products) as p
on c.CategoryID = p.CategoryID
group by CategoryName

