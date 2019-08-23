---
title: Použití transformace XSLT u datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: 56f6e13763b5230e046c0838892393b3672a54be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937040"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="f83d0-102">Použití transformace XSLT u datové sady</span><span class="sxs-lookup"><span data-stu-id="f83d0-102">Applying an XSLT Transform to a DataSet</span></span>
<span data-ttu-id="f83d0-103">Metoda<xref:System.Data.DataSet> **WriteXml** pro umožňuje napsat obsah **datové sady** jako data XML.</span><span class="sxs-lookup"><span data-stu-id="f83d0-103">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="f83d0-104">Běžným úkolem je pak transformovat tento kód XML do jiného formátu pomocí transformací XSL (XSLT).</span><span class="sxs-lookup"><span data-stu-id="f83d0-104">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="f83d0-105">Synchronizace **datové sady** se <xref:System.Xml.XmlDataDocument> sadou vám ale umožňuje použít šablonu stylů XSLT na obsah **datové sady** , aniž byste museli nejdřív zapsat obsah **datové sady** jako XML data pomocí **WriteXml**.</span><span class="sxs-lookup"><span data-stu-id="f83d0-105">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="f83d0-106">Následující příklad naplní datovou **sadu** tabulkami a relacemi, synchronizuje **datovou sadu** s **objektu XmlDataDocument**a zapíše část **datové sady** jako soubor HTML pomocí šablony stylů XSLT.</span><span class="sxs-lookup"><span data-stu-id="f83d0-106">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="f83d0-107">Následuje obsah šablony stylů XSLT.</span><span class="sxs-lookup"><span data-stu-id="f83d0-107">Following are the contents of the XSLT stylesheet.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="f83d0-108">Následující kód vyplní **datovou sadu** a použije šablonu stylů XSLT.</span><span class="sxs-lookup"><span data-stu-id="f83d0-108">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f83d0-109">Pokud aplikujete šablonu stylů XSLT na **datovou sadu** , která obsahuje vztahy, dosáhnete nejlepšího výkonu, pokud nastavíte **vnořenou** <xref:System.Data.DataRelation> vlastnost na **hodnotu true** pro každou vnořenou relaci.</span><span class="sxs-lookup"><span data-stu-id="f83d0-109">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="f83d0-110">Díky tomu můžete použít šablony stylů XSLT, které implementují přirozené křížové zpracování pro navigaci v hierarchii a transformují data, a to na rozdíl od použití osy umístění XPath s náročnou výkonem (například předcházející na stejné úrovni a po sobě jdoucí na stejné úrovni). výrazy testu tabulkového uzlu) pro navigaci.</span><span class="sxs-lookup"><span data-stu-id="f83d0-110">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="f83d0-111">Další informace o vnořených relacích najdete v tématu [vnořování datových vztahů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="f83d0-111">For more information on nested relations, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);   
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",   
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="f83d0-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f83d0-112">See also</span></span>

- [<span data-ttu-id="f83d0-113">Synchronizace datové sady a datového dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f83d0-113">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="f83d0-114">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="f83d0-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
