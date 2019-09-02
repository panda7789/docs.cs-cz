---
title: Vnoření datových relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: 08149de9222c34928078c0ca9d88096f7a4a88d1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203271"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="b71e6-102">Vnoření datových relací</span><span class="sxs-lookup"><span data-stu-id="b71e6-102">Nesting DataRelations</span></span>
<span data-ttu-id="b71e6-103">V relačních zastoupeních dat jednotlivé tabulky obsahují řádky, které jsou vzájemně propojené pomocí sloupce nebo sady sloupců.</span><span class="sxs-lookup"><span data-stu-id="b71e6-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="b71e6-104">V ADO.NET <xref:System.Data.DataSet>je relace mezi tabulkami implementována <xref:System.Data.DataRelation>pomocí.</span><span class="sxs-lookup"><span data-stu-id="b71e6-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="b71e6-105">Při vytváření objektu **DataRelation**jsou vztahy nadřazenosti a podřízenosti sloupců spravovány pouze prostřednictvím vztahu.</span><span class="sxs-lookup"><span data-stu-id="b71e6-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="b71e6-106">Tabulky a sloupce jsou samostatné entity.</span><span class="sxs-lookup"><span data-stu-id="b71e6-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="b71e6-107">V hierarchickém znázornění dat, která poskytuje XML, jsou vztahy typu nadřazený-podřízený zastoupeny nadřazenými prvky, které obsahují vnořené podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="b71e6-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="b71e6-108">Pro usnadnění vnoření podřízených objektů, pokud je **datová sada** synchronizována s <xref:System.Xml.XmlDataDocument> nebo zapsaná jako XML data pomocí funkce **WriteXml**, objekt DataRelation zpřístupňuje **vnořenou** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b71e6-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="b71e6-109">Nastavení **vnořené** vlastnosti DataRelation na **hodnotu true** způsobí, že podřízené řádky relace budou vnořené do nadřazeného sloupce, pokud jsou zapsány jako data XML nebo synchronizovány pomocí **objektu XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="b71e6-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="b71e6-110">Ve výchozím nastavení je vnořená vlastnost DataRelation nastavena na **hodnotu false**.</span><span class="sxs-lookup"><span data-stu-id="b71e6-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="b71e6-111">Zvažte například následující **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="b71e6-111">For example, consider the following **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="b71e6-112">Vzhledem k tomu, že vlastnost **Nested** objektu DataRelation není pro tuto **datovou sadu**nastavena na **hodnotu true** , podřízené objekty nejsou vnořené v rámci nadřazených elementů, pokud je tato **datová sada** reprezentována jako data XML.</span><span class="sxs-lookup"><span data-stu-id="b71e6-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="b71e6-113">Transformace reprezentace XML pro **datovou sadu** , která obsahuje související **datovou sadu**s nevnořenými datovými relacemi, může způsobit pomalý výkon.</span><span class="sxs-lookup"><span data-stu-id="b71e6-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="b71e6-114">Doporučujeme, abyste provedli vnořování datových vztahů.</span><span class="sxs-lookup"><span data-stu-id="b71e6-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="b71e6-115">To provedete tak, že nastavíte vnořenou vlastnost na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="b71e6-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="b71e6-116">Potom v šabloně stylů XSLT napíšete kód, který použije k vyhledání a transformaci dat horních hierarchické výrazy XPath.</span><span class="sxs-lookup"><span data-stu-id="b71e6-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="b71e6-117">Následující příklad kódu ukazuje výsledek volání **WriteXml** na **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="b71e6-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
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
  
 <span data-ttu-id="b71e6-118">Všimněte si, že elementy Customers a Orders se zobrazují jako elementy na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="b71e6-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="b71e6-119">Pokud jste chtěli, aby se prvky **objednávky** zobrazovaly jako podřízené objekty svých příslušných nadřazených prvků, je nutné, aby byla **vnořená** vlastnost DataRelation nastavena na **hodnotu true** a přidáte následující:</span><span class="sxs-lookup"><span data-stu-id="b71e6-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="b71e6-120">Následující kód ukazuje, jaký výsledný výstup by vypadal jako, s prvky **Orders** vnořené v rámci svých příslušných nadřazených prvků.</span><span class="sxs-lookup"><span data-stu-id="b71e6-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b71e6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b71e6-121">See also</span></span>

- [<span data-ttu-id="b71e6-122">Použití XML v datové sadě</span><span class="sxs-lookup"><span data-stu-id="b71e6-122">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="b71e6-123">Přidání datových relací</span><span class="sxs-lookup"><span data-stu-id="b71e6-123">Adding DataRelations</span></span>](adding-datarelations.md)
- [<span data-ttu-id="b71e6-124">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="b71e6-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="b71e6-125">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b71e6-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
