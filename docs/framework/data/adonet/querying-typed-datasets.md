---
title: Dotazování typové datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 30a6512202615590a4b399b8ce7173b213a8873c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353482"
---
# <a name="querying-typed-datasets"></a><span data-ttu-id="1f8db-102">Dotazování typové datové sady</span><span class="sxs-lookup"><span data-stu-id="1f8db-102">Querying Typed DataSets</span></span>
<span data-ttu-id="1f8db-103">Pokud schéma <xref:System.Data.DataSet> je známý v době návrhu aplikace, doporučujeme použít typem <xref:System.Data.DataSet> při použití [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f8db-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="1f8db-104">Představuje zadaný <xref:System.Data.DataSet> je třída, která je odvozena z <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1f8db-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1f8db-105">Jako takový dědí všechny metody, události a vlastnosti <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1f8db-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1f8db-106">Kromě toho typové <xref:System.Data.DataSet> poskytuje silného typu metody, události a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1f8db-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="1f8db-107">To znamená, že máte přístup tabulky a sloupce, podle názvu, namísto použití metody založené na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="1f8db-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="1f8db-108">Díky tomu dotazy jednodušší a srozumitelnější.</span><span class="sxs-lookup"><span data-stu-id="1f8db-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="1f8db-109">Další informace najdete v tématu [typové datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="1f8db-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="1f8db-110"> také podporuje dotazování přes představuje zadaný <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1f8db-110"> also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1f8db-111">S zadaný <xref:System.Data.DataSet>, není nutné používat obecná <xref:System.Data.DataRowExtensions.Field%2A> metoda nebo <xref:System.Data.DataRowExtensions.SetField%2A> metoda pro přístup k datům sloupce.</span><span class="sxs-lookup"><span data-stu-id="1f8db-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span>  <span data-ttu-id="1f8db-112">Názvy vlastností jsou k dispozici v době kompilace, protože je součástí informací o typu <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1f8db-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="1f8db-113"> poskytuje přístup k hodnotám sloupce jako správného typu, tak, aby chyby neshoda typu jsou zachyceny při kompilaci kódu místo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="1f8db-113"> provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>  
  
 <span data-ttu-id="1f8db-114">Před zahájením dotazování představuje zadaný <xref:System.Data.DataSet>, musíte vygenerovat třídy pomocí návrháře DataSet v [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f8db-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the DataSet Designer in [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span></span>  <span data-ttu-id="1f8db-115">Další informace najdete v tématu [vytvořit a nakonfigurovat datové sady](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="1f8db-115">For more information, see [Create and configure datasets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f8db-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f8db-116">Example</span></span>  
 <span data-ttu-id="1f8db-117">Následující příklad ukazuje dotaz přes představuje zadaný <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="1f8db-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1f8db-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f8db-118">See Also</span></span>  
 [<span data-ttu-id="1f8db-119">Dotazy na datové sady</span><span class="sxs-lookup"><span data-stu-id="1f8db-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="1f8db-120">Dotazy na křížovou tabulku</span><span class="sxs-lookup"><span data-stu-id="1f8db-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="1f8db-121">Dotazy na jednu tabulku</span><span class="sxs-lookup"><span data-stu-id="1f8db-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
