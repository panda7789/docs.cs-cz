---
title: Přidání DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 451ee0eee466efca86345ea7112e9b178a2c66e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="adding-datarelations"></a><span data-ttu-id="ae720-102">Přidání DataRelations</span><span class="sxs-lookup"><span data-stu-id="ae720-102">Adding DataRelations</span></span>
<span data-ttu-id="ae720-103">V <xref:System.Data.DataSet> s více <xref:System.Data.DataTable> objekty, můžete použít <xref:System.Data.DataRelation> objekty, které se týkají jednu tabulku do jiné, můžete procházet pomocí tabulky a vrátí řádky nadřazená nebo podřízená z tabulek v relaci.</span><span class="sxs-lookup"><span data-stu-id="ae720-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="ae720-104">Argumenty, které jsou nutné k vytváření **DataRelation** jsou název **DataRelation** vytváří a pole jednoho nebo více <xref:System.Data.DataColumn> odkazy na sloupce, které slouží jako nadřazené a podřízené sloupce v relaci.</span><span class="sxs-lookup"><span data-stu-id="ae720-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="ae720-105">Po vytvoření **DataRelation**, můžete použít, přejděte mezi tabulkami a k načtení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ae720-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="ae720-106">Přidání **DataRelation** k <xref:System.Data.DataSet> přidá, ve výchozím nastavení, <xref:System.Data.UniqueConstraint> nadřazené tabulky a <xref:System.Data.ForeignKeyConstraint> do podřízené tabulky.</span><span class="sxs-lookup"><span data-stu-id="ae720-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="ae720-107">Další informace o těchto výchozí omezení najdete v tématu [DataTable omezení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="ae720-107">For more information about these default constraints, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="ae720-108">Následující příklad kódu vytvoří **DataRelation** pomocí dvou <xref:System.Data.DataTable> objekty v <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ae720-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ae720-109">Každý <xref:System.Data.DataTable> obsahuje sloupec s názvem **CustID**, který slouží jako propojení mezi těmito dvěma <xref:System.Data.DataTable> objekty.</span><span class="sxs-lookup"><span data-stu-id="ae720-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="ae720-110">V příkladu přidáme jedné **DataRelation** k **vztahů** kolekce <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="ae720-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="ae720-111">Určuje název prvního argumentu v příkladu **DataRelation** vytváří.</span><span class="sxs-lookup"><span data-stu-id="ae720-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="ae720-112">Druhý argument nastaví nadřazeného **DataColumn** a třetí argument nastaví podřízené **DataColumn**.</span><span class="sxs-lookup"><span data-stu-id="ae720-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="ae720-113">A **DataRelation** má také **vnořené** vlastnost která, pokud nastavíte hodnotu **true**, způsobí, že řádky z tabulky podřízené být Nested v přidružené řádku, od nadřazené tabulky Když se zapisují jako elementů XML pomocí <xref:System.Data.DataSet.WriteXml%2A> .</span><span class="sxs-lookup"><span data-stu-id="ae720-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="ae720-114">Další informace najdete v tématu [pomocí XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ae720-114">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae720-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae720-115">See Also</span></span>  
 [<span data-ttu-id="ae720-116">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="ae720-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="ae720-117">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="ae720-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
