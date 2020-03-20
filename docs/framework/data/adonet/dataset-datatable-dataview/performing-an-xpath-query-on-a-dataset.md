---
title: Provedení dotazu XPath u datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 5e9a00ab78a57c3c1686d7c87ed8b45d9b2649af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150828"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a>Provedení dotazu XPath u datové sady
Vztah mezi synchronizované <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> a umožňuje využívat služby XML, jako je například dotaz Xml Path Language (XPath), které přistupují k **XmlDataDocument** a mohou provádět určité funkce pohodlněji než přímý přístup k **datové sadě.** Například místo použití metody **Select** <xref:System.Data.DataTable> a k navigaci relací do jiných tabulek v **datové sadě**můžete provést dotaz XPath na **dokumentu XmlDataDocument,** který je <xref:System.Xml.XmlNodeList>synchronizován s **datovou sadou**, a získat tak seznam elementů XML ve formě . Uzly v **XmlNodeList**, <xref:System.Xml.XmlElement> přetypování jako uzly, pak mohou být předány **GetRowFromElement** metoda **XmlDataDocument**, vrátit odpovídající <xref:System.Data.DataRow> odkazy na řádky tabulky v synchronizované **DataSet**.  
  
 Například následující ukázka kódu provádí dotaz XPath "vnouče". **DataSet** je vyplněn třemi tabulkami: **Zákazníci**, **Objednávky**a **Podrobnosti objednávky**. V ukázce je nejprve vytvořen vztah nadřazený podřízený mezi **tabulkami Zákazníci** a **Objednávky** a mezi **tabulkami Orders** a **OrderDetails.** Dotaz XPath se pak provede vrátit **XmlNodeList** uzlů **zákazníků,** kde vnouče **OrderDetails** uzel má **ProductID** uzel s hodnotou 43. V podstatě ukázka používá dotaz XPath k určení, kteří zákazníci objednali produkt, který má **ProductID** 43.  
  
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
  
## <a name="see-also"></a>Viz také

- [Synchronizace datové sady a datového dokumentu XML](dataset-and-xmldatadocument-synchronization.md)
- [Přehled ADO.NET](../ado-net-overview.md)
