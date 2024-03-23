# Scripts de Consultas
 **Consultas que fueron Tarea** 
 **_Juan Mateo Hernández De Luna_ pt.3**

## 1.-
```SELECT c.CategoryName AS 'Nombre de la Cateoría',
SUM(od.Quantity * od.UnitPrice) AS 'Ventas Totales en 1997' FROM Categories c
JOIN Products p ON c.CategoryID = p.CategoryID
JOIN [Order Details] od ON p.ProductID = od.ProductID
JOIN Orders o ON od.OrderID = o.OrderID
WHERE o.OrderDate BETWEEN '1997-01-01' AND '1997-12-31'
GROUP BY c.CategoryName;
select * from [Order Details]


## 2.-
 SELECT TOP 5 p.ProductName AS 'Producto', SUod.Quantity) AS 'Cantidad Total Vendida c/u'
FROM Products as p
JOIN [Order Details] od ON p.ProductID = od.ProductID 
JOIN Orders o ON od.OrderID = o.OrderID
GROUP BY p.ProductName
ORDER BY SUM(od.Quantity) DESC;

## 3.-
SELECT c.CustomerID AS Cliente, MAX(o.OrderDate) AS Ultimo_Pedido
FROM Customers AS c
INNER JOIN Orders AS o ON c.CustomerID = o.CustomerID
GROUP BY c.CustomerID
ORDER BY Ultimo_Pedido DESC;

## 4.-
SELECT e.FirstName as Empleadox, YEAR(o.OrderDate) AS Anio, 
SUM(od.Quantity * od.UnitPrice) AS Ventas_Totales
FROM Employees AS e
INNER JOIN Orders AS o ON e.EmployeeID = o.EmployeeID
INNER JOIN [Order Details] AS od ON o.OrderID = od.OrderID
GROUP BY e.FirstName, e.LastName, YEAR(o.OrderDate)
ORDER BY Anio, Ventas_Totales ASC;
select * from Employees
select * from [Order Details]

## 5.-
SELECT  p.ProductName as Producto ,o.OrderDate as Anio, p.Discontinued as Descontinuado
FROM Orders AS o
INNER JOIN [Order Details] AS od ON o.OrderID = od.OrderID
INNER JOIN Customers AS c ON o.CustomerID = c.CustomerID
INNER JOIN Products AS p ON od.ProductID = p.ProductID
--ORDER BY Descontinuado DESC;
select * from [Order Details]
select * from Products


## PARTE 2 | HAVING CONSULTAX'S

## --1.-
SELECT c.CategoryName, AVG(p.UnitPrice) AS  Promedio
FROM Categories AS c
INNER JOIN Products AS p ON c.CategoryID = p.CategoryID
GROUP BY c.CategoryName
HAVING AVG(p.UnitPrice) > 20
ORDER BY Promedio ASC;

## --2.-
SELECT p.SupplierID as Provedor_Id, COUNT(p.ProductID) AS Productos
FROM Products AS p
WHERE p.UnitsInStock < 10
GROUP BY p.SupplierID
HAVING COUNT(p.ProductID) > 2
select * from Products

## --3.-
SELECT e.EmployeeID as Empleado, SUM(od.Quantity * od.UnitPrice) AS Total_ventas_en_1997
FROM Employees AS e
INNER JOIN Orders AS o ON e.EmployeeID = o.EmployeeID
INNER JOIN [Order Details] AS od ON o.OrderID = od.OrderID
WHERE o.OrderDate BETWEEN '1997-01-01' AND '1997-12-31'
GROUP BY e.EmployeeID
HAVING SUM(od.Quantity * od.UnitPrice) > 50000
ORDER BY Total_ventas_en_1997 ASC;

## --4.-
SELECT c.CustomerID as Clientes, COUNT(*) AS Pedidos_en_total
FROM Customers AS c
INNER JOIN Orders AS o ON c.CustomerID = o.CustomerID
GROUP BY c.CustomerID
HAVING COUNT(*) > 15

## --5.-
SELECT p.ProductName as Productos, SUM(od.Quantity) AS Unidades
FROM Products AS p
INNER JOIN [Order Details] AS od ON p.ProductID = od.ProductID
GROUP BY p.ProductName
HAVING SUM(od.Quantity) > 1000```