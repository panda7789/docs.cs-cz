---
title: DataRelations vnoření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 3f17d81ac41c90e7f1c48523a4ced91bc788a962
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761893"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="35664-102">DataRelations vnoření</span><span class="sxs-lookup"><span data-stu-id="35664-102">Nesting DataRelations</span></span>
<span data-ttu-id="35664-103">Jednotlivé tabulky v znázornění relační data obsahují řádky, které se vztahují na sebe navzájem pomocí sloupec nebo sadu sloupců.</span><span class="sxs-lookup"><span data-stu-id="35664-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="35664-104">V technologie ADO.NET <xref:System.Data.DataSet>, relace mezi tabulkami je implementovaná pomocí <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="35664-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="35664-105">Při vytváření **DataRelation**, vztahy podřízenosti sloupců, které lze spravovat pouze prostřednictvím vztah.</span><span class="sxs-lookup"><span data-stu-id="35664-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="35664-106">Tabulky a sloupce jsou samostatné entity.</span><span class="sxs-lookup"><span data-stu-id="35664-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="35664-107">V hierarchické reprezentace dat, který obsahuje XML vztahů nadřazenosti a podřízenosti reprezentována nadřazené elementy, které obsahují vnořené podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="35664-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="35664-108">Pro usnadnění vnoření podřízených objektů při **datovou sadu** je synchronizován se službou <xref:System.Xml.XmlDataDocument> nebo zapsat jako data XML pomocí **WriteXml**, **DataRelation** zpřístupní **vnořené** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="35664-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="35664-109">Nastavení **vnořené** vlastnost **DataRelation** k **true** způsobí, že podřízená řádky vztah k začlenit do nadřazeného sloupce, když se zapisují jako XML data nebo synchronizovat se službou **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="35664-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="35664-110">**Vnořené** vlastnost **DataRelation** je **false**, ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="35664-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="35664-111">Například vezměte v úvahu následující **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="35664-111">For example, consider the following **DataSet**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 <span data-ttu-id="35664-112">Protože **vnořené** vlastnost **DataRelation** objekt není nastavený na **true** pro tento **datovou sadu**, nejsou vnořené podřízené objekty v rámci nadřazené elementy při to **datovou sadu** je reprezentována jako XML data.</span><span class="sxs-lookup"><span data-stu-id="35664-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="35664-113">Převod reprezentace XML **datovou sadu** obsahující související **datovou sadu**s s-nested datové relace může způsobit snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="35664-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="35664-114">Doporučujeme vám, že je vnořovat datové relace.</span><span class="sxs-lookup"><span data-stu-id="35664-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="35664-115">Chcete-li to provést, nastavte **vnořené** vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="35664-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="35664-116">Potom napište kód v Styl XSLT používající vertikální hierarchické výrazy dotazů XPath pro vyhledání a transformovat data.</span><span class="sxs-lookup"><span data-stu-id="35664-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="35664-117">Následující příklad kódu ukazuje výsledek z volání **WriteXml** na **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="35664-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 <span data-ttu-id="35664-118">Všimněte si, že **zákazníci** element a **objednávky** elementy se zobrazují jako podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="35664-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="35664-119">Pokud jste chtěli **objednávky** elementy objeví jako podřízené objekty jejich příslušné nadřazené elementy, **vnořené** vlastnost **DataRelation** by bylo potřeba nastavit na **true** a by přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="35664-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="35664-120">Následující kód ukazuje, jak výsledný výstup bude vypadat, s **objednávky** vnořených elementů v rámci jejich příslušné nadřazené elementy.</span><span class="sxs-lookup"><span data-stu-id="35664-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35664-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="35664-121">See Also</span></span>  
 [<span data-ttu-id="35664-122">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="35664-122">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="35664-123">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="35664-123">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [<span data-ttu-id="35664-124">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="35664-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="35664-125">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="35664-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
