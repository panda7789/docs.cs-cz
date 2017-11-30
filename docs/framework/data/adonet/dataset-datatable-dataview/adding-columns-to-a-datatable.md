---
title: "Přidávání sloupců do DataTable"
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6107c21ed04c9c39d69c5c784244d8f6bf9560e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="669bf-102">Přidávání sloupců do DataTable</span><span class="sxs-lookup"><span data-stu-id="669bf-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="669bf-103">A <xref:System.Data.DataTable> obsahuje kolekci <xref:System.Data.DataColumn> objekty odkazuje **sloupce** vlastnosti tabulky.</span><span class="sxs-lookup"><span data-stu-id="669bf-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="669bf-104">Tato kolekce sloupců, společně s omezeními, definuje schéma a struktura tabulky.</span><span class="sxs-lookup"><span data-stu-id="669bf-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="669bf-105">Vytvoříte **DataColumn** objektů v rámci tabulky pomocí **DataColumn** konstruktoru, nebo voláním **přidat** metodu **sloupce**vlastnost tabulky, který je <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="669bf-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="669bf-106">**Přidat** metoda přijímá volitelný **ColumnName**, **datový typ**, a **výraz** argumenty a vytvoří novou  **DataColumn** jako člena kolekce.</span><span class="sxs-lookup"><span data-stu-id="669bf-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="669bf-107">Také přijímá existující **DataColumn** objektu a přidá do kolekce a vrátí odkaz na přidaném **DataColumn** Pokud požadovaný.</span><span class="sxs-lookup"><span data-stu-id="669bf-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="669bf-108">Protože **DataTable** objekty nejsou specifické pro libovolný zdroj dat, typy rozhraní .NET Framework se používají při zadávání datový typ **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="669bf-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="669bf-109">Následující příklad přidá čtyři sloupce, abyste **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="669bf-109">The following example adds four columns to a **DataTable**.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 <span data-ttu-id="669bf-110">V příkladu, Všimněte si, že vlastnosti **CustID** není povolena nastavení sloupec **DBNull** hodnoty a omezit hodnoty, které mají být jedinečné.</span><span class="sxs-lookup"><span data-stu-id="669bf-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="669bf-111">Ale pokud definujete **CustID** sloupec jako sloupec primárního klíče tabulky **AllowDBNull** vlastnost bude automaticky nastavena **false** a **Jedinečný** vlastnost bude automaticky nastavena **true**.</span><span class="sxs-lookup"><span data-stu-id="669bf-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="669bf-112">Další informace najdete v tématu [definování primárních klíčů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="669bf-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="669bf-113">Pokud je název sloupce není zadaný pro sloupec, sloupec je uveden přírůstkové výchozí název sloupce*N,* počínaje "Column1", když je přidán do **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="669bf-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="669bf-114">Doporučujeme, abyste se zabránilo pojmenovávací konvenci "sloupec*N*" Pokud zadáte název sloupce, protože název zadáte může dojít ke konfliktu s existujícím názvem sloupce výchozí v **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="669bf-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="669bf-115">Pokud se zadaným názvem již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="669bf-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="669bf-116">Pokud používáte <xref:System.Xml.Linq.XElement> jako <xref:System.Data.DataColumn.DataType%2A> z <xref:System.Data.DataColumn> v <xref:System.Data.DataTable>, serializace XML nebude fungovat při čtení v datech.</span><span class="sxs-lookup"><span data-stu-id="669bf-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="669bf-117">Například, pokud je zapsat <xref:System.Xml.XmlDocument> pomocí `DataTable.WriteXml` metoda při serializaci do formátu XML je další nadřazený uzel v <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="669bf-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="669bf-118">Chcete-li tento problém obejít, použijte <xref:System.Data.SqlTypes.SqlXml> zadejte místo <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="669bf-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="669bf-119">`ReadXml`a `WriteXml` pracovní správně s <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="669bf-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="669bf-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="669bf-120">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="669bf-121">Definice schématu DataTable</span><span class="sxs-lookup"><span data-stu-id="669bf-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="669bf-122">DataTables</span><span class="sxs-lookup"><span data-stu-id="669bf-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="669bf-123">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="669bf-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
