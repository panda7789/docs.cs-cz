---
title: Vnoření datových relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 9255615c7786773f1d4f453b910fdccdf191721f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45617029"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="20ec0-102">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="20ec0-102">Nesting DataRelations</span></span>
<span data-ttu-id="20ec0-103">Jednotlivé tabulky v relační znázornění dat, obsahovat řádky, které se vztahují k navzájem pomocí sloupec nebo sadu sloupců.</span><span class="sxs-lookup"><span data-stu-id="20ec0-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="20ec0-104">V ADO.NET <xref:System.Data.DataSet>, relace mezi tabulkami se implementuje pomocí <xref:System.Data.DataRelation>.</span><span class="sxs-lookup"><span data-stu-id="20ec0-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="20ec0-105">Když vytvoříte **DataRelation**, vztahy nadřazenosti a podřízenosti sloupce, které se spravují jenom do relace.</span><span class="sxs-lookup"><span data-stu-id="20ec0-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="20ec0-106">Tabulky a sloupce jsou samostatné entity.</span><span class="sxs-lookup"><span data-stu-id="20ec0-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="20ec0-107">V Hierarchická reprezentace dat, které obsahuje XML nadřazené a podřízené vztahy jsou reprezentovány nadřazené elementy, které obsahují vnořené podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="20ec0-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="20ec0-108">Pro usnadnění vnoření podřízené objekty při **datovou sadu** synchronizována s <xref:System.Xml.XmlDataDocument> nebo zapsat jako dat XML pomocí **WriteXml**, **DataRelation** Zpřístupňuje **vnořené** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="20ec0-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="20ec0-109">Nastavení **vnořené** vlastnost **DataRelation** k **true** způsobí, že podřízené řádky vztahu, chcete-li být vnořen v rámci nadřazeného sloupce při zápisu jako XML data nebo synchronizovat se službou **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="20ec0-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="20ec0-110">**Vnořené** vlastnost **DataRelation** je **false**, ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="20ec0-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="20ec0-111">Představte si třeba následující **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="20ec0-111">For example, consider the following **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="20ec0-112">Protože **vnořené** vlastnost **DataRelation** není nastaven na **true** pro tuto **datovou sadu**, nejsou vnořené podřízené objekty v rámci nadřazené prvky při to **datovou sadu** je vyjádřena jako XML data.</span><span class="sxs-lookup"><span data-stu-id="20ec0-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="20ec0-113">Transformace reprezentace XML **datovou sadu** , který obsahuje související **datovou sadu**s s-nested datové relace může způsobit snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="20ec0-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="20ec0-114">Doporučujeme vám, že byste vnořit datové relace.</span><span class="sxs-lookup"><span data-stu-id="20ec0-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="20ec0-115">Chcete-li to provést, nastavte **vnořené** vlastnost **true**.</span><span class="sxs-lookup"><span data-stu-id="20ec0-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="20ec0-116">Teprve pak píšete kód v šabloně stylů XSLT, který používá výrazy dotazu XPath hierarchické shora dolů k vyhledání a transformovat data.</span><span class="sxs-lookup"><span data-stu-id="20ec0-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="20ec0-117">Následující příklad kódu ukazuje výsledek z volání **WriteXml** na **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="20ec0-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="20ec0-118">Všimněte si, že **zákazníkům** elementu a **objednávky** prvky jsou uvedeny jako prvky na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="20ec0-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="20ec0-119">Pokud byste chtěli **objednávky** prvků, které se zobrazují jako podřízené objekty daného jejich příslušné nadřazené elementy **vnořené** vlastnost **DataRelation** by bylo potřeba nastavit na **true** a přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="20ec0-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="20ec0-120">Následující kód ukazuje, co výsledný výstup bude vypadat, se **objednávky** vnořené elementy v rámci svých odpovídajících nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="20ec0-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20ec0-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="20ec0-121">See Also</span></span>  
 [<span data-ttu-id="20ec0-122">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="20ec0-122">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="20ec0-123">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="20ec0-123">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [<span data-ttu-id="20ec0-124">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="20ec0-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="20ec0-125">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="20ec0-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
