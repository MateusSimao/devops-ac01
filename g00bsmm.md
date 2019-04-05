select Production.Suppliers.contactname as 'Contato do Cliente',
Production.Products.productname 'Nome do Produto',
Sales.OrderDetails.qty as 'Quantidade de Produtos',
Sales.Orders.orderdate as 'Data do Pedido',
Production.Suppliers.city as 'Cidade do Fornecedor'

from Sales.Orders
join Sales.OrderDetails on Sales.Orders.orderid = Sales.OrderDetails.orderid
join Production.Products on Production.Products.productid = Sales.OrderDetails.productid
join Production.Suppliers on Production.Products.supplierid = Production.Suppliers.supplierid

where Sales.Orders.orderdate between '2006-07-01' and '2006-07-31' and Sales.OrderDetails.qty between 20 and 59
and Production.Products.productname like 'Product A%' or Production.Products.productname like 'Product G%'
and Production.Suppliers.city in ('Stockholm', 'Sydney', 'Sandvika', 'Ravenna')
order by Sales.Orders.empid desc
