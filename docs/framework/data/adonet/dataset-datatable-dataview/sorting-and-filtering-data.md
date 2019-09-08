---
title: Řazení a filtrování dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 09cee2f2b2c3288c835912c9f311bf2511c7b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785923"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="c5b1c-102">Řazení a filtrování dat</span><span class="sxs-lookup"><span data-stu-id="c5b1c-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="c5b1c-103">Poskytuje několik způsobů řazení a filtrování dat <xref:System.Data.DataTable>v: <xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="c5b1c-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
- <span data-ttu-id="c5b1c-104"><xref:System.Data.DataView.Sort%2A> Vlastnost můžete použít k určení řazení jednoho nebo více sloupců a zahrnutí parametrů ASC (vzestupně) a desc (sestupně).</span><span class="sxs-lookup"><span data-stu-id="c5b1c-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
- <span data-ttu-id="c5b1c-105"><xref:System.Data.DataView.ApplyDefaultSort%2A> Vlastnost můžete použít k automatickému vytvoření pořadí řazení ve vzestupném pořadí podle sloupce primárního klíče nebo sloupce v tabulce.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="c5b1c-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>platí pouze v případě, že vlastnost **Sort** je odkaz s hodnotou null nebo prázdný řetězec, a pokud je pro tabulku definována primární klíč.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
- <span data-ttu-id="c5b1c-107"><xref:System.Data.DataView.RowFilter%2A> Vlastnost můžete použít k určení podmnožiny řádků na základě hodnot jejich sloupců.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="c5b1c-108">Podrobnosti o platných výrazech pro vlastnost **RowFilter vyžaduje hodnotu** naleznete v referenčních informacích k <xref:System.Data.DataColumn.Expression%2A> vlastnosti <xref:System.Data.DataColumn> třídy.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="c5b1c-109">Pokud chcete vrátit výsledky konkrétního dotazu na data, na rozdíl od poskytování dynamického zobrazení podmnožiny dat, použijte <xref:System.Data.DataView.Find%2A> metody nebo <xref:System.Data.DataView.FindRows%2A> objektu **DataView** k dosažení nejlepšího výkonu místo nastavení  **Vlastnost RowFilter vyžaduje hodnotu**</span><span class="sxs-lookup"><span data-stu-id="c5b1c-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="c5b1c-110">Nastavením vlastnosti **RowFilter vyžaduje hodnotu** se znovu sestaví index dat, zvýší se režie do vaší aplikace a zmenší se výkon.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="c5b1c-111">Vlastnost **RowFilter vyžaduje hodnotu** se nejlépe používá v aplikaci vázané na data, kde vázaný ovládací prvek zobrazuje filtrované výsledky.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="c5b1c-112">Metody **find** a **FindRows** využívají aktuální index bez nutnosti opětovného vytvoření indexu.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="c5b1c-113">Další informace o metodách **find** a **FindRows** najdete v tématu [Vyhledání řádků](finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="c5b1c-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](finding-rows.md).</span></span>  
  
- <span data-ttu-id="c5b1c-114"><xref:System.Data.DataView.RowStateFilter%2A> Vlastnost můžete použít k určení, které verze řádků se mají zobrazit.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="c5b1c-115">**Objekt DataView** implicitně spravuje, která verze řádku má být vystavení v závislosti na **RowState** základního řádku.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="c5b1c-116">Pokud je například **vlastnost RowStateFilter** nastaveno na **DataViewRowState. Deleted**, zobrazení **DataView** zpřístupní **původní** verzi všech **odstraněných** řádků, protože neexistuje žádná verze **aktuálního** řádku.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="c5b1c-117">Můžete určit, která verze řádku řádku je zveřejněna, pomocí vlastnosti **rowversion** třídy **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="c5b1c-118">V následující tabulce jsou uvedeny možnosti pro **DataViewRowState**.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="c5b1c-119">DataViewRowState možnosti</span><span class="sxs-lookup"><span data-stu-id="c5b1c-119">DataViewRowState options</span></span>|<span data-ttu-id="c5b1c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c5b1c-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="c5b1c-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="c5b1c-121">**CurrentRows**</span></span>|<span data-ttu-id="c5b1c-122">**Aktuální** verze řádku všech **nezměněných**, **přidaných**a **upravených** řádků.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="c5b1c-123">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-123">This is the default.</span></span>|  
    |<span data-ttu-id="c5b1c-124">**Přidat**</span><span class="sxs-lookup"><span data-stu-id="c5b1c-124">**Added**</span></span>|<span data-ttu-id="c5b1c-125">**Aktuální** verze řádku všech **přidaných** řádků.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="c5b1c-126">**Odstraňování**</span><span class="sxs-lookup"><span data-stu-id="c5b1c-126">**Deleted**</span></span>|<span data-ttu-id="c5b1c-127">**Původní** verze řádků všech **odstraněných** řádků.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="c5b1c-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="c5b1c-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="c5b1c-129">**Aktuální** verze řádků všech **změněných** řádků.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="c5b1c-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="c5b1c-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="c5b1c-131">**Původní** verze řádků všech **upravených** řádků.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="c5b1c-132">**Žádné**</span><span class="sxs-lookup"><span data-stu-id="c5b1c-132">**None**</span></span>|<span data-ttu-id="c5b1c-133">Žádné řádky</span><span class="sxs-lookup"><span data-stu-id="c5b1c-133">No rows.</span></span>|  
    |<span data-ttu-id="c5b1c-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="c5b1c-134">**OriginalRows**</span></span>|<span data-ttu-id="c5b1c-135">**Původní** verze řádku všech **nezměněných**, **upravených**a **odstraněných** řádků.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="c5b1c-136">**Oproti**</span><span class="sxs-lookup"><span data-stu-id="c5b1c-136">**Unchanged**</span></span>|<span data-ttu-id="c5b1c-137">**Aktuální** verze řádku všech **nezměněných** řádků.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="c5b1c-138">Další informace o stavech řádků a verzích řádků najdete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="c5b1c-138">For more information about row states and row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="c5b1c-139">Následující příklad kódu vytvoří zobrazení, ve kterém se zobrazí všechny produkty, u kterých je počet jednotek v zásobách menší nebo roven úrovni přeřazení, seřazené podle prvního podle ID dodavatele a potom podle názvu produktu.</span><span class="sxs-lookup"><span data-stu-id="c5b1c-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5b1c-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5b1c-140">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="c5b1c-141">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="c5b1c-141">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="c5b1c-142">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c5b1c-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
