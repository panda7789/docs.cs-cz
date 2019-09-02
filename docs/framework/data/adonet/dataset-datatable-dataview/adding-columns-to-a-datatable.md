---
title: Přidání sloupců do datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 105537a5fccef6de7266407c78cc915f8c5d8678
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204056"
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="0085e-102">Přidání sloupců do datové tabulky</span><span class="sxs-lookup"><span data-stu-id="0085e-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="0085e-103">Obsahuje kolekci objektů, na které odkazuje vlastnost Columns v tabulce. <xref:System.Data.DataTable> <xref:System.Data.DataColumn></span><span class="sxs-lookup"><span data-stu-id="0085e-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="0085e-104">Tato kolekce sloupců, spolu s omezeními, definuje schéma nebo strukturu tabulky.</span><span class="sxs-lookup"><span data-stu-id="0085e-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="0085e-105">Objekty **DataColumn** lze vytvořit v tabulce pomocí konstruktoru DataColumn nebo voláním metody **Add** vlastnosti Columns tabulky, která je <xref:System.Data.DataColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="0085e-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="0085e-106">Metoda **Add** akceptuje volitelné argumenty **ColumnName**, **DataType**a **Expression** a vytvoří nový datový **sloupec** jako člena kolekce.</span><span class="sxs-lookup"><span data-stu-id="0085e-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="0085e-107">Přijímá také existující objekt **DataColumn** a přidává ho do kolekce a v případě potřeby vrátí odkaz na přidaný DataColumn .</span><span class="sxs-lookup"><span data-stu-id="0085e-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="0085e-108">Vzhledem k tomu, že objekty **DataTable** nejsou specifické pro žádný zdroj dat, .NET Framework typy se používají při zadávání datového typu **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="0085e-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="0085e-109">Následující příklad přidá čtyři sloupce do **objektu DataTable**.</span><span class="sxs-lookup"><span data-stu-id="0085e-109">The following example adds four columns to a **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="0085e-110">V příkladu si všimněte, že vlastnosti pro sloupec **custid** jsou nastaveny tak, aby nepovolovaly hodnoty **DBNull** a omezily hodnoty tak, aby byly jedinečné.</span><span class="sxs-lookup"><span data-stu-id="0085e-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="0085e-111">Pokud však definujete sloupec **custid** jako sloupec primárního klíče tabulky, vlastnost **AllowDBNull** bude automaticky nastavena na **hodnotu false** a vlastnost **Unique** bude automaticky nastavena na **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="0085e-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="0085e-112">Další informace najdete v tématu [Definování primárních klíčů](defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="0085e-112">For more information, see [Defining Primary Keys](defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0085e-113">Pokud pro sloupec není zadán název sloupce, sloupec má při přidání do objektu DataColumnCollection přírůstkový výchozí název sloupce*N,* který začíná na "Sloupec1".</span><span class="sxs-lookup"><span data-stu-id="0085e-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="0085e-114">Doporučujeme vyhnout se konvenci pojmenování "Column*N*" při zadání názvu sloupce, protože zadané jméno může být v konfliktu s existujícím výchozím názvem sloupce v objektu DataColumnCollection.</span><span class="sxs-lookup"><span data-stu-id="0085e-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="0085e-115">Pokud zadaný název již existuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0085e-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="0085e-116">Pokud používáte <xref:System.Xml.Linq.XElement> <xref:System.Data.DataColumn.DataType%2A> jako<xref:System.Data.DataColumn> v ,<xref:System.Data.DataTable>serializace XML nebude při čtení dat fungovat.</span><span class="sxs-lookup"><span data-stu-id="0085e-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="0085e-117">Například pokud napíšete <xref:System.Xml.XmlDocument> `DataTable.WriteXml` metodu pomocí metody, po serializaci do XML je <xref:System.Xml.Linq.XElement>další nadřazený uzel v.</span><span class="sxs-lookup"><span data-stu-id="0085e-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="0085e-118">Chcete-li tento problém obejít, <xref:System.Data.SqlTypes.SqlXml> použijte typ <xref:System.Xml.Linq.XElement>místo.</span><span class="sxs-lookup"><span data-stu-id="0085e-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="0085e-119">`ReadXml`a `WriteXml` funguje správně s <xref:System.Data.SqlTypes.SqlXml>.</span><span class="sxs-lookup"><span data-stu-id="0085e-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0085e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0085e-120">See also</span></span>

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="0085e-121">Definice schématu datové tabulky</span><span class="sxs-lookup"><span data-stu-id="0085e-121">DataTable Schema Definition</span></span>](datatable-schema-definition.md)
- [<span data-ttu-id="0085e-122">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="0085e-122">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="0085e-123">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="0085e-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
