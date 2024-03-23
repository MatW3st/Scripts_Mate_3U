# Scripts Echas en Clase
 **_Juan Mateo Hernández De Luna_ pt.3**


**create database tdasjoins**
**use tdasjoins**

create table categorias(
idcategoria int not null identity(1,1),
nombre varchar (100) not null,
constraint pk_categoria 
primary key (idcategoria)
)


 **crea la estructura de una tabla desde una consulta**
use Northwind
select top 0 CategoryID,CategoryName 
into categoria2
from  Northwind.dbo.categories

**agrega un contarint a una tabla 
alter table categoria2**
add constraint pk_categoria2
primary key (CategoryID)

**elimina un constrain** 
alter table categoria2
drop pk_categoria2

**este elimina una columna existente**
alter table categoria2
drop column CategoryID

**agrega una columna a una tabla**
alter table categoria2
add CategoryID int not null identity(1,1)

**llnear la tabla categoria y categoria2 con una consulta**
insert into categoria2 (CategoryName)
select CategoryName from Northwind.dbo.Categories

**llenar una tabla y llenarla con datos**
select ProductID as numeroProducto, ProductName as nombreProucto,
CategoryID as categoria, UnitPrice as precioUnitario, UnitsInStock as existencia 
into producto
from Northwind.dbo.Products

alter table producto 
add constraint pk_producto
primary key (numeroproducto)

alter table producto 
add constraint unico_nombreProducto
unique (unico_nombreProducto)

alter table producto 
add constraint chk_preciounitario
check (preciounitario between 1 and 10000)

alter table producto 
add constraint chk_existencia
check (existencia >=0 and existencia <=100)

alter table producto 
add constraint fk_producto_categoria
foreign key categoria(idcategoria)
on delete cascade
on update cascade
select * from producto