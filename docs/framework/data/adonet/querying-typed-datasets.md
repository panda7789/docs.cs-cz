---
title: Dotazy na typové datové sady
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685813"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="be295-102">Dotazování typové datové sady</span><span class="sxs-lookup"><span data-stu-id="be295-102">Query typed DataSets</span></span>

<span data-ttu-id="be295-103">Pokud schéma <xref:System.Data.DataSet> je znám v době návrhu aplikací, doporučujeme použít zadaný <xref:System.Data.DataSet> při použití technologie LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="be295-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="be295-104">Zadaný <xref:System.Data.DataSet> je třída, která je odvozena z <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="be295-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="be295-105">V důsledku toho dědí všechny metody, události a vlastnosti <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="be295-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="be295-106">Kromě toho typovaného <xref:System.Data.DataSet> poskytuje silného typu metody, události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="be295-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="be295-107">To znamená, že dostanete tabulky a sloupce podle názvu, namísto použití metody založené na kolekci.</span><span class="sxs-lookup"><span data-stu-id="be295-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="be295-108">Díky tomu dotazy, jednodušší a lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="be295-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="be295-109">Další informace najdete v tématu [typované datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="be295-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="be295-110">Technologie LINQ to DataSet také podporuje dotazování typovaného <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="be295-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="be295-111">S typovaného <xref:System.Data.DataSet>, není nutné museli používat obecná <xref:System.Data.DataRowExtensions.Field%2A> metoda nebo <xref:System.Data.DataRowExtensions.SetField%2A> metody pro přístup k datům sloupce.</span><span class="sxs-lookup"><span data-stu-id="be295-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="be295-112">Názvy vlastností jsou k dispozici v době kompilace, protože je součástí informací o typu <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="be295-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="be295-113">Technologie LINQ to DataSet poskytuje přístup k hodnotám sloupce jako správný typ, tak, aby při kompilaci kódu místo v době běhu jsou zachyceny chyby typu neshoda.</span><span class="sxs-lookup"><span data-stu-id="be295-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="be295-114">Před zahájením dotazování typovaného <xref:System.Data.DataSet>, musíte vygenerovat třídu pomocí **Návrhář DataSet** v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="be295-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="be295-115">Další informace najdete v tématu [vytvoření a konfigurace datové sady](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="be295-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="be295-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="be295-116">Example</span></span>

<span data-ttu-id="be295-117">Následující příklad ukazuje dotaz nad typovaného <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="be295-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a><span data-ttu-id="be295-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be295-118">See also</span></span>

- [<span data-ttu-id="be295-119">Dotazy na datové sady</span><span class="sxs-lookup"><span data-stu-id="be295-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="be295-120">Dotazy na křížovou tabulku</span><span class="sxs-lookup"><span data-stu-id="be295-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="be295-121">Dotazy na jednu tabulku</span><span class="sxs-lookup"><span data-stu-id="be295-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
