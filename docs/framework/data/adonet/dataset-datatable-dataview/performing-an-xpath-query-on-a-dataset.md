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
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="5d883-102">Provedení dotazu XPath u datové sady</span><span class="sxs-lookup"><span data-stu-id="5d883-102">Performing an XPath Query on a DataSet</span></span>
<span data-ttu-id="5d883-103">Vztah mezi synchronizované <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> a umožňuje využívat služby XML, jako je například dotaz Xml Path Language (XPath), které přistupují k **XmlDataDocument** a mohou provádět určité funkce pohodlněji než přímý přístup k **datové sadě.**</span><span class="sxs-lookup"><span data-stu-id="5d883-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="5d883-104">Například místo použití metody **Select** <xref:System.Data.DataTable> a k navigaci relací do jiných tabulek v **datové sadě**můžete provést dotaz XPath na **dokumentu XmlDataDocument,** který je <xref:System.Xml.XmlNodeList>synchronizován s **datovou sadou**, a získat tak seznam elementů XML ve formě .</span><span class="sxs-lookup"><span data-stu-id="5d883-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="5d883-105">Uzly v **XmlNodeList**, <xref:System.Xml.XmlElement> přetypování jako uzly, pak mohou být předány **GetRowFromElement** metoda **XmlDataDocument**, vrátit odpovídající <xref:System.Data.DataRow> odkazy na řádky tabulky v synchronizované **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="5d883-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="5d883-106">Například následující ukázka kódu provádí dotaz XPath "vnouče".</span><span class="sxs-lookup"><span data-stu-id="5d883-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="5d883-107">**DataSet** je vyplněn třemi tabulkami: **Zákazníci**, **Objednávky**a **Podrobnosti objednávky**.</span><span class="sxs-lookup"><span data-stu-id="5d883-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="5d883-108">V ukázce je nejprve vytvořen vztah nadřazený podřízený mezi **tabulkami Zákazníci** a **Objednávky** a mezi **tabulkami Orders** a **OrderDetails.**</span><span class="sxs-lookup"><span data-stu-id="5d883-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="5d883-109">Dotaz XPath se pak provede vrátit **XmlNodeList** uzlů **zákazníků,** kde vnouče **OrderDetails** uzel má **ProductID** uzel s hodnotou 43.</span><span class="sxs-lookup"><span data-stu-id="5d883-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="5d883-110">V podstatě ukázka používá dotaz XPath k určení, kteří zákazníci objednali produkt, který má **ProductID** 43.</span><span class="sxs-lookup"><span data-stu-id="5d883-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d883-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d883-111">See also</span></span>

- [<span data-ttu-id="5d883-112">Synchronizace datové sady a datového dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="5d883-112">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="5d883-113">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5d883-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
