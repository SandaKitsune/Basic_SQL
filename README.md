# Basic_SQL
Here you can find a spreadsheet with basic SQL codes: 

https://docs.google.com/spreadsheets/d/1mzyoxoEZtCKqkX7cdjQAFhxtj8362q-xzJyT6JN1To4/edit#gid=389760228

Examples: 

1.

SELECT p.ProductID, p.Name, p.ProductNumber, p.Size, p.Color , ps.ProductSubcategoryID, ps.Name as SubCategory, pc.Name as Category, p.ListPrice, p.SellEndDate

FROM `adwentureworks_db.product` p

JOIN `adwentureworks_db.productsubcategory` ps ON ps.ProductSubcategoryID = p.ProductSubcategoryID

JOIN `adwentureworks_db.productcategory` pc ON ps.ProductCategoryID = pc.ProductCategoryID

WHERE p.ListPrice > 2000 AND p.SellEndDate is NULL AND pc.Name = 'Bikes'

ORDER BY p.ListPrice;

2.
SELECT DISTINCT sd.SalesOrderID, sd.OrderQty,sd.UnitPrice,sd.LineTotal, sd.ProductID, sd.SpecialOfferID, sp.ModifiedDate, so.Category, so.Description, sp.Rowguid

FROM `adwentureworks_db.specialofferproduct`sp

LEFT JOIN `adwentureworks_db.salesorderdetail`sd ON sp.SpecialOfferID = sd.SpecialOfferID and sp.ProductID = sd.ProductID

LEFT JOIN `adwentureworks_db.specialoffer`so ON sd.SpecialOfferID = so.SpecialOfferID

WHERE so.SpecialOfferID != 1

ORDER BY LineTotal DESC;
