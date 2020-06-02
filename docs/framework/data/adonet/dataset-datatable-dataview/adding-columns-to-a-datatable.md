---
title: Přidání sloupců do datové tabulky
description: Objekt DataTable obsahuje objekty DataColumn, na které odkazuje vlastnost Columns tabulky. Pomocí tohoto ukázkového kódu můžete přidat sloupce do tabulky v ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 9d6d21696acd7a6b63cfd6d2ea7e906ec2acd7c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286944"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="eba11-104">Přidání sloupců do datové tabulky</span><span class="sxs-lookup"><span data-stu-id="eba11-104">Adding Columns to a DataTable</span></span>
<span data-ttu-id="eba11-105"><xref:System.Data.DataTable>Obsahuje kolekci objektů, na které <xref:System.Data.DataColumn> odkazuje vlastnost **Columns** v tabulce.</span><span class="sxs-lookup"><span data-stu-id="eba11-105">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="eba11-106">Tato kolekce sloupců, spolu s omezeními, definuje schéma nebo strukturu tabulky.</span><span class="sxs-lookup"><span data-stu-id="eba11-106">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="eba11-107">Objekty **DataColumn** lze vytvořit v tabulce pomocí konstruktoru **DataColumn** nebo voláním metody **Add** vlastnosti **Columns** tabulky, která je <xref:System.Data.DataColumnCollection> .</span><span class="sxs-lookup"><span data-stu-id="eba11-107">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="eba11-108">Metoda **Add** akceptuje volitelné argumenty **ColumnName**, **DataType**a **Expression** a vytvoří nový datový **sloupec** jako člena kolekce.</span><span class="sxs-lookup"><span data-stu-id="eba11-108">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="eba11-109">Přijímá také existující objekt **DataColumn** a přidává ho do kolekce a v případě potřeby vrátí odkaz na přidaný **DataColumn** .</span><span class="sxs-lookup"><span data-stu-id="eba11-109">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="eba11-110">Vzhledem k tomu, že objekty **DataTable** nejsou specifické pro žádný zdroj dat, .NET Framework typy se používají při zadávání datového typu **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="eba11-110">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="eba11-111">Následující příklad přidá čtyři sloupce do **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="eba11-111">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="eba11-112">V příkladu si všimněte, že vlastnosti pro sloupec **custid** jsou nastaveny tak, aby nepovolovaly hodnoty **DBNull** a omezily hodnoty tak, aby byly jedinečné.</span><span class="sxs-lookup"><span data-stu-id="eba11-112">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="eba11-113">Pokud však definujete sloupec **custid** jako sloupec primárního klíče tabulky, vlastnost **AllowDBNull** bude automaticky nastavena na **hodnotu false** a vlastnost **Unique** bude automaticky nastavena na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="eba11-113">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="eba11-114">Další informace najdete v tématu [Definování primárních klíčů](defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="eba11-114">For more information, see [Defining Primary Keys](defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="eba11-115">Pokud pro sloupec není zadán název sloupce, sloupec má při přidání do objektu **DataColumnCollection**přírůstkový výchozí název sloupce*N,* který začíná na "Sloupec1".</span><span class="sxs-lookup"><span data-stu-id="eba11-115">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="eba11-116">Doporučujeme vyhnout se konvenci pojmenování "Column*N*" při zadání názvu sloupce, protože zadané jméno může být v konfliktu s existujícím výchozím názvem sloupce v objektu **DataColumnCollection**.</span><span class="sxs-lookup"><span data-stu-id="eba11-116">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="eba11-117">Pokud zadaný název již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="eba11-117">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="eba11-118">Pokud používáte <xref:System.Xml.Linq.XElement> jako <xref:System.Data.DataColumn.DataType%2A> <xref:System.Data.DataColumn> v <xref:System.Data.DataTable> , serializace XML nebude při čtení dat fungovat.</span><span class="sxs-lookup"><span data-stu-id="eba11-118">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="eba11-119">Například pokud napíšete <xref:System.Xml.XmlDocument> `DataTable.WriteXml` metodu pomocí metody, po serializaci do XML je další nadřazený uzel v <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="eba11-119">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="eba11-120">Chcete-li tento problém obejít, použijte <xref:System.Data.SqlTypes.SqlXml> typ místo <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="eba11-120">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="eba11-121">`ReadXml`a `WriteXml` funguje správně s <xref:System.Data.SqlTypes.SqlXml> .</span><span class="sxs-lookup"><span data-stu-id="eba11-121">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba11-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="eba11-122">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="eba11-123">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="eba11-123">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="eba11-124">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="eba11-124">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="eba11-125">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="eba11-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
