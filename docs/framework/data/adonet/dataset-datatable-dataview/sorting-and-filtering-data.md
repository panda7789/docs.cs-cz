---
title: Řazení a filtrování dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 02a67a490eb8339663aac08c97c665ffee09f0df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760606"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="2a82f-102">Řazení a filtrování dat</span><span class="sxs-lookup"><span data-stu-id="2a82f-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="2a82f-103"><xref:System.Data.DataView> Nabízí několik způsobů řazení a filtrování dat v <xref:System.Data.DataTable>:</span><span class="sxs-lookup"><span data-stu-id="2a82f-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
-   <span data-ttu-id="2a82f-104">Můžete použít <xref:System.Data.DataView.Sort%2A> vlastnosti a určit jeden nebo více sloupců pořadí řazení a zahrnují (vzestupně) ASC a DESC (sestupně) parametry.</span><span class="sxs-lookup"><span data-stu-id="2a82f-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
-   <span data-ttu-id="2a82f-105">Můžete použít <xref:System.Data.DataView.ApplyDefaultSort%2A> vlastnost pro automatické vytvoření pořadí řazení, ve vzestupném pořadí, na základě sloupec primárního klíče nebo sloupců tabulky.</span><span class="sxs-lookup"><span data-stu-id="2a82f-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="2a82f-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> kdy se vztahuje pouze **řazení** vlastnost je odkaz s hodnotou null nebo prázdný řetězec, a pokud tabulka má definovaný primární klíč.</span><span class="sxs-lookup"><span data-stu-id="2a82f-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
-   <span data-ttu-id="2a82f-107">Můžete použít <xref:System.Data.DataView.RowFilter%2A> vlastnosti k určení podmnožiny řádků podle jejich hodnot sloupců.</span><span class="sxs-lookup"><span data-stu-id="2a82f-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="2a82f-108">Podrobnosti o platné výrazy pro **RowFilter** vlastnost, najdete v referenčních informacích pro <xref:System.Data.DataColumn.Expression%2A> vlastnost <xref:System.Data.DataColumn> třídy.</span><span class="sxs-lookup"><span data-stu-id="2a82f-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="2a82f-109">Pokud chcete vrátit výsledky konkrétní dotaz na data, a poskytuje dynamické zobrazení podmnožinu dat, použijte <xref:System.Data.DataView.Find%2A> nebo <xref:System.Data.DataView.FindRows%2A> metody **DataView** k dosažení nejlepšího výkonu místo nastavení **RowFilter** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2a82f-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="2a82f-110">Nastavení **RowFilter** vlastnost znovu sestaví index pro data, přidávání režie k vaší aplikaci a snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="2a82f-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="2a82f-111">**RowFilter** vlastnost nejlépe slouží v aplikaci vázané na data kde připojeného ovládacího prvku zobrazí filtrované výsledky.</span><span class="sxs-lookup"><span data-stu-id="2a82f-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="2a82f-112">**Najít** a **FindRows** metody využít aktuální index bez nutnosti znovu sestavit index.</span><span class="sxs-lookup"><span data-stu-id="2a82f-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="2a82f-113">Další informace o **najít** a **FindRows** metody, najdete v části [hledání řádky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="2a82f-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
-   <span data-ttu-id="2a82f-114">Můžete použít <xref:System.Data.DataView.RowStateFilter%2A> vlastnosti k určení, které verze řádku zobrazíte.</span><span class="sxs-lookup"><span data-stu-id="2a82f-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="2a82f-115">**DataView** implicitně spravuje které verze řádku vystavit, v závislosti na **RowState** základní řádku.</span><span class="sxs-lookup"><span data-stu-id="2a82f-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="2a82f-116">Například pokud **Vlastnost RowStateFilter** je nastaven na **DataViewRowState.Deleted**, **DataView** zpřístupní **původní** verze řádku všechny **odstraněné** řádků, protože neexistuje žádný **aktuální** verze řádku.</span><span class="sxs-lookup"><span data-stu-id="2a82f-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="2a82f-117">Můžete určit, které verze řádku řádku je vystavení pomocí **RowVersion** vlastnost **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="2a82f-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="2a82f-118">Následující tabulka znázorňuje možnosti pro **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="2a82f-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="2a82f-119">Možnosti DataViewRowState</span><span class="sxs-lookup"><span data-stu-id="2a82f-119">DataViewRowState options</span></span>|<span data-ttu-id="2a82f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2a82f-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="2a82f-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="2a82f-121">**CurrentRows**</span></span>|<span data-ttu-id="2a82f-122">**Aktuální** verze řádku všech **Unchanged**, **Added**, a **změněné** řádků.</span><span class="sxs-lookup"><span data-stu-id="2a82f-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="2a82f-123">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="2a82f-123">This is the default.</span></span>|  
    |<span data-ttu-id="2a82f-124">**Přidat**</span><span class="sxs-lookup"><span data-stu-id="2a82f-124">**Added**</span></span>|<span data-ttu-id="2a82f-125">**Aktuální** verze řádku všech **Added** řádků.</span><span class="sxs-lookup"><span data-stu-id="2a82f-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="2a82f-126">**Odstranit**</span><span class="sxs-lookup"><span data-stu-id="2a82f-126">**Deleted**</span></span>|<span data-ttu-id="2a82f-127">**Původní** verze řádku všech **odstraněné** řádků.</span><span class="sxs-lookup"><span data-stu-id="2a82f-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="2a82f-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="2a82f-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="2a82f-129">**Aktuální** verze řádku všech **změněné** řádků.</span><span class="sxs-lookup"><span data-stu-id="2a82f-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="2a82f-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="2a82f-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="2a82f-131">**Původní** verze řádku všech **změněné** řádků.</span><span class="sxs-lookup"><span data-stu-id="2a82f-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="2a82f-132">**None**</span><span class="sxs-lookup"><span data-stu-id="2a82f-132">**None**</span></span>|<span data-ttu-id="2a82f-133">Žádné řádky.</span><span class="sxs-lookup"><span data-stu-id="2a82f-133">No rows.</span></span>|  
    |<span data-ttu-id="2a82f-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="2a82f-134">**OriginalRows**</span></span>|<span data-ttu-id="2a82f-135">**Původní** verze řádku všech **Unchanged**, **změněné**, a **odstraněné** řádků.</span><span class="sxs-lookup"><span data-stu-id="2a82f-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="2a82f-136">**Beze změny**</span><span class="sxs-lookup"><span data-stu-id="2a82f-136">**Unchanged**</span></span>|<span data-ttu-id="2a82f-137">**Aktuální** verze řádku všech **Unchanged** řádků.</span><span class="sxs-lookup"><span data-stu-id="2a82f-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="2a82f-138">Další informace o stavy řádků a řádek verzích najdete v tématu [stavy řádků a verze řádku](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="2a82f-138">For more information about row states and row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="2a82f-139">Následující příklad kódu vytvoří zobrazení, zobrazí všechny produkty, kde počet jednotek v stock je menší než nebo rovna úrovni na změnit pořadí seřazeny nejprve podle ID dodavatele a poté podle názvu produktu.</span><span class="sxs-lookup"><span data-stu-id="2a82f-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a82f-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a82f-140">See Also</span></span>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="2a82f-141">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="2a82f-141">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="2a82f-142">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="2a82f-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
