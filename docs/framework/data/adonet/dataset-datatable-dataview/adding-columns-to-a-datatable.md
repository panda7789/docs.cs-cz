---
title: Přidání sloupců do datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 2e7008f6693d7d76520a7ff6ae9172e28e4990c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207003"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="38a88-102">Přidání sloupců do datové tabulky</span><span class="sxs-lookup"><span data-stu-id="38a88-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="38a88-103">A <xref:System.Data.DataTable> obsahuje kolekci <xref:System.Data.DataColumn> objekty odkazují **sloupce** vlastnost tabulky.</span><span class="sxs-lookup"><span data-stu-id="38a88-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="38a88-104">Tuto sadu sloupců, společně s omezeními, definuje schéma a struktura tabulky.</span><span class="sxs-lookup"><span data-stu-id="38a88-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="38a88-105">Vytvoříte **DataColumn** objektů v rámci tabulky pomocí **DataColumn** konstruktoru, nebo pomocí volání **přidat** metodu **sloupce**vlastnost tabulky, který je <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="38a88-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="38a88-106">**Přidat** metoda přijímá volitelný **Názevsloupce**, **datový typ**, a **výraz** argumenty a vytvoří novou  **Objekt DataColumn** jako člena kolekce.</span><span class="sxs-lookup"><span data-stu-id="38a88-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="38a88-107">Také přijímá existující **DataColumn** objektu a přidá jej do kolekce a vrátí odkaz na přidaném **DataColumn** pokud o to požádá.</span><span class="sxs-lookup"><span data-stu-id="38a88-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="38a88-108">Protože **DataTable** objekty nejsou specifické pro libovolný zdroj dat, typy rozhraní .NET Framework se používají při zadávání datového typu **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="38a88-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="38a88-109">Následující příklad přidá čtyři sloupce **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="38a88-109">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="38a88-110">V příkladu, Všimněte si, že vlastnosti **CustID** sloupec je nastaven na nepovoluje **DBNull** hodnoty a k omezení hodnoty, které mají být jedinečné.</span><span class="sxs-lookup"><span data-stu-id="38a88-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="38a88-111">Ale pokud definujete **CustID** sloupec jako sloupec primárního klíče tabulky, **AllowDBNull** vlastnost bude automaticky nastavena **false** a **Jedinečné** vlastnost bude automaticky nastavena **true**.</span><span class="sxs-lookup"><span data-stu-id="38a88-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="38a88-112">Další informace najdete v tématu [definování primárních klíčů](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="38a88-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="38a88-113">Pokud není zadán název sloupce pro sloupec, ve sloupci je předána na přírůstkové výchozí název sloupce*N,* počínaje "Sloupec1", když se přidá do **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="38a88-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="38a88-114">Doporučujeme vám, že byste se vyhnout zásadu vytváření názvů "sloupce*N*" když zadáte název sloupce, vzhledem k tomu, že zadáte název dojít ke konfliktu s existujícím názvem sloupce výchozí v **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="38a88-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="38a88-115">Pokud zadaný název již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="38a88-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="38a88-116">Pokud používáte <xref:System.Xml.Linq.XElement> jako <xref:System.Data.DataColumn.DataType%2A> z <xref:System.Data.DataColumn> v <xref:System.Data.DataTable>, serializace XML nebude fungovat, pokud čtení v datech.</span><span class="sxs-lookup"><span data-stu-id="38a88-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="38a88-117">Například, pokud je vypsat <xref:System.Xml.XmlDocument> pomocí `DataTable.WriteXml` metoda po serializace za účelem je do další nadřazeného uzlu v XML <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="38a88-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="38a88-118">Chcete-li tento problém obejít, použijte <xref:System.Data.SqlTypes.SqlXml> zadejte místo <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="38a88-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="38a88-119">`ReadXml` a `WriteXml` fungují správně s <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="38a88-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a88-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38a88-120">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="38a88-121">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="38a88-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [<span data-ttu-id="38a88-122">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="38a88-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [<span data-ttu-id="38a88-123">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="38a88-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
