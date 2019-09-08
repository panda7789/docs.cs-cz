---
title: Provedení dotazu XPath u datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 6082a171d24c55ea52c153bbd920bb7486be78a7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784371"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Provedení dotazu XPath u datové sady
Vztah mezi synchronizovaným <xref:System.Data.DataSet> a <xref:System.Xml.XmlDataDocument> umožňuje využívat služby XML, jako je dotaz jazyka XML Path (XPath), který přistupuje k **objektu XmlDataDocument** a umožňuje pohodlnější fungování určitých funkcí než přímý přístup k **datové sadě** . Například namísto použití metody **Select** objektu <xref:System.Data.DataTable> pro navigaci na relace s jinými tabulkami v **datové sadě**můžete provést dotaz XPath v **objektu XmlDataDocument** , který je synchronizován s **datovou sadou**, a získat tak seznam elementů XML ve formě <xref:System.Xml.XmlNodeList>. Uzly v **XmlNodeList**, přetypování jako <xref:System.Xml.XmlElement> uzly, mohou být předány metodě **GetRowFromElement** **objektu XmlDataDocument**, aby vracely vyhovující <xref:System.Data.DataRow> odkazy na řádky tabulky v synchronizovaných.  **Datová sada**.  
  
 Například následující ukázka kódu provede "podřízený" dotaz XPath. **Datová sada** je vyplněna třemi tabulkami: **Zákazníci**, **objednávky**a **OrderDetails**. V ukázce je relace nadřazený-podřízený nejprve vytvořena mezi tabulkami **zákazníci** a **objednávky** a mezi tabulkami **Orders** a **OrderDetails** . Pak se provede dotaz XPath, který vrátí **XmlNodeList** **uzly,** kde má uzel **OrderDetails** uzel **ProductID** s hodnotou 43. V podstatě ukázka používá dotaz XPath k určení, kteří zákazníci objednali produkt s **ProductID** 43.  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],   
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);   
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Synchronizace datové sady a datového dokumentu XML](dataset-and-xmldatadocument-synchronization.md)
- [Přehled ADO.NET](../ado-net-overview.md)
