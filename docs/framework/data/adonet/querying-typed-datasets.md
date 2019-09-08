---
title: Dotazy na typové datové sady
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782964"
---
# <a name="query-typed-datasets"></a><span data-ttu-id="3c575-102">Datové sady s typovým dotazem</span><span class="sxs-lookup"><span data-stu-id="3c575-102">Query typed DataSets</span></span>

<span data-ttu-id="3c575-103">Pokud je schéma v <xref:System.Data.DataSet> době návrhu aplikace známo, doporučujeme při použití LINQ to DataSet zadat <xref:System.Data.DataSet> typ.</span><span class="sxs-lookup"><span data-stu-id="3c575-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using LINQ to DataSet.</span></span> <span data-ttu-id="3c575-104">Typ je třída, která je odvozena z typu <xref:System.Data.DataSet>. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="3c575-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3c575-105">V takovém případě dědí všechny metody, události a vlastnosti <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="3c575-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3c575-106">Kromě toho zadaný <xref:System.Data.DataSet> typ poskytuje metody, události a vlastnosti silného typu.</span><span class="sxs-lookup"><span data-stu-id="3c575-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="3c575-107">To znamená, že můžete získat přístup k tabulkám a sloupcům podle názvu namísto použití metod založených na kolekcích.</span><span class="sxs-lookup"><span data-stu-id="3c575-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="3c575-108">Díky tomu jsou dotazy jednodušší a čitelnější.</span><span class="sxs-lookup"><span data-stu-id="3c575-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="3c575-109">Další informace najdete v tématu [typové datové sady](./dataset-datatable-dataview/typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="3c575-109">For more information, see [Typed DataSets](./dataset-datatable-dataview/typed-datasets.md).</span></span>

<span data-ttu-id="3c575-110">LINQ to DataSet také podporuje dotazování na typovaném <xref:System.Data.DataSet>typu.</span><span class="sxs-lookup"><span data-stu-id="3c575-110">LINQ to DataSet also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3c575-111">Se zadaným typem <xref:System.Data.DataSet>není nutné pro přístup k datům sloupce používat obecnou <xref:System.Data.DataRowExtensions.Field%2A> metodu <xref:System.Data.DataRowExtensions.SetField%2A> nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="3c575-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span> <span data-ttu-id="3c575-112">Názvy vlastností jsou k dispozici v době kompilace, protože informace o typu jsou <xref:System.Data.DataSet>obsaženy v.</span><span class="sxs-lookup"><span data-stu-id="3c575-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3c575-113">LINQ to DataSet poskytuje přístup k hodnotám sloupců jako správný typ, takže pokud je kód kompilován při kompilaci namísto za běhu, jsou zachyceny chyby typu Neshoda typů.</span><span class="sxs-lookup"><span data-stu-id="3c575-113">LINQ to DataSet provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>

<span data-ttu-id="3c575-114">Předtím <xref:System.Data.DataSet>, než můžete začít dotazovat se na typ, musíte vygenerovat třídu pomocí **Návrháře DataSet v sadě** Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3c575-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the **DataSet Designer** in Visual Studio.</span></span> <span data-ttu-id="3c575-115">Další informace najdete v tématu [Vytvoření a konfigurace datových sad](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="3c575-115">For more information, see [Create and configure DataSets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>

## <a name="example"></a><span data-ttu-id="3c575-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c575-116">Example</span></span>

<span data-ttu-id="3c575-117">Následující příklad ukazuje dotaz na základě zadaného <xref:System.Data.DataSet>typu:</span><span class="sxs-lookup"><span data-stu-id="3c575-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3c575-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c575-118">See also</span></span>

- [<span data-ttu-id="3c575-119">Dotazy na datové sady</span><span class="sxs-lookup"><span data-stu-id="3c575-119">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="3c575-120">Dotazy na křížovou tabulku</span><span class="sxs-lookup"><span data-stu-id="3c575-120">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="3c575-121">Dotazy na jednu tabulku</span><span class="sxs-lookup"><span data-stu-id="3c575-121">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
