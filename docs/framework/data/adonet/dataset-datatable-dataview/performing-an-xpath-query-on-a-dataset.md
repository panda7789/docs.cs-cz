---
title: "Provádění dotazu XPath na datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 62c5cef51e125443d87c47f7f62dc76aa5d352b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="658d6-102">Provádění dotazu XPath na datové sady</span><span class="sxs-lookup"><span data-stu-id="658d6-102">Performing an XPath Query on a DataSet</span></span>
<span data-ttu-id="658d6-103">Vztah mezi synchronizovaný <xref:System.Data.DataSet> a <xref:System.Xml.XmlDataDocument> umožňuje využívat XML služby, jako je dotaz XML Path Language (XPath), kteří se dostávají **XmlDataDocument** a může provádět určité funkce snadněji než přístup k **datovou sadu** přímo.</span><span class="sxs-lookup"><span data-stu-id="658d6-103">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="658d6-104">Například místo pomocí **vyberte** metodu <xref:System.Data.DataTable> přejděte s jinými v **datovou sadu**, dotaz XPath můžete provádět na **XmlDataDocument**  který je synchronizován se službou **datovou sadu**, chcete-li získat seznam elementů XML ve formě <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="658d6-104">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="658d6-105">Uzly v **XmlNodeList**, vícesměrového vysílání jako <xref:System.Xml.XmlElement> uzlů, může být předána do **GetRowFromElement** metodu **XmlDataDocument**, vrátit odpovídající <xref:System.Data.DataRow> odkazy na řádky tabulky synchronizované **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="658d6-105">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="658d6-106">Například následující ukázka kódu provede dotaz XPath "podřízený".</span><span class="sxs-lookup"><span data-stu-id="658d6-106">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="658d6-107">**Datovou sadu** , naplní se tři tabulky: **zákazníci**, **objednávky**, a **Rozpis objednávek**.</span><span class="sxs-lookup"><span data-stu-id="658d6-107">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="658d6-108">V ukázce je poprvé vytvořen vztah nadřazený podřízený mezi **zákazníci** a **objednávky** tabulky a mezi **objednávky** a **Rozpis objednávek** tabulky.</span><span class="sxs-lookup"><span data-stu-id="658d6-108">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="658d6-109">Dotaz XPath se potom provede na vrátit **XmlNodeList** z **zákazníci** uzly tam, kde pod podřízená **Rozpis objednávek** má uzel **ProductID**uzel s hodnotou 43.</span><span class="sxs-lookup"><span data-stu-id="658d6-109">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="658d6-110">V podstatě ukázku dotaz XPath používá k určení uvedeni zákazníci, kteří mají seřazené produkt, který má **ProductID** 43.</span><span class="sxs-lookup"><span data-stu-id="658d6-110">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="658d6-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="658d6-111">See Also</span></span>  
 [<span data-ttu-id="658d6-112">Synchronizace datové sady a datového dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="658d6-112">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [<span data-ttu-id="658d6-113">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="658d6-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
