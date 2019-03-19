# Challenge Set 9
## Part I: W3Schools SQL Lab 

*Introductory level SQL*

--

This challenge uses the [W3Schools SQL playground](http://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all). Please add solutions to this markdown file and submit.

1. Which customers are from the UK? SELECT * FROM Customers WHERE Country = 'UK';

2. What is the name of the customer who has the most orders? Wolski  SELECT * FROM Customers GROUP BY CustomerName ORDER BY CustomerName DESC LIMIT 1;

3. Which supplier has the highest average product price? Forêts d'érables,  SELECT SupplierName FROM Suppliers WHERE SupplierID=(SELECT SupplierId FROM Products GROUP BY SupplierID ORDER BY SupplierID DESC LIMIT 1);        

4. How many different countries are all the customers from? (*Hint:* consider [DISTINCT](http://www.w3schools.com/sql/sql_distinct.asp).)
 21, SELECT DISTINCT(Country) FROM Customers; 


5. What category appears in the most orders? 

6. What was the total cost for each order? 13175
SELECT OrderID, Quantity*Price FROM (SELECT o.OrderID,e.EmployeeID,e.LastName,e.FirstName,od.Quantity,p.Price FROM Employees e, Orders o, OrderDetails od, Products p WHERE e.EmployeeID=o.EmployeeID AND o.OrderID=od.OrderID AND od.ProductID=p.ProductID) GROUP BY OrderID ORDER BY Quantity*Price DESC LIMIT 1; 

7. Which employee made the most sales (by total price)? Margaret Peacock
SELECT EmployeeID, LastName, FirstName, Quantity*Price FROM (SELECT e.EmployeeID,e.LastName,e.FirstName,od.Quantity,p.Price FROM Employees e, Orders o, OrderDetails od, Products p WHERE e.EmployeeID=o.EmployeeID AND o.OrderID=od.OrderID AND od.ProductID=p.ProductID) GROUP BY EmployeeID ORDER BY Quantity*Price DESC LIMIT 1; 

8. Which employees have BS degrees? (*Hint:* look at the [LIKE](http://www.w3schools.com/sql/sql_like.asp) operator.)
SELECT FirstName, LastName FROM Employees WHERE Notes Like '%BS%';

9. Which supplier of three or more products has the highest average product price? (*Hint:* look at the [HAVING](http://www.w3schools.com/sql/sql_having.asp) operator.)46
SELECT AVG(Price) as avg FROM Products GROUP BY SupplierID HAVING COUNT(SupplierID)>=3 ORDER BY avg DESC LIMIT 1;


