---
title: Vytvoření zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151335"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="c4b12-102">Vytvoření zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="c4b12-102">Creating a DataView</span></span>
<span data-ttu-id="c4b12-103">Existují dva způsoby, <xref:System.Data.DataView>jak vytvořit .</span><span class="sxs-lookup"><span data-stu-id="c4b12-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="c4b12-104">Můžete použít **Konstruktor DataView** nebo můžete vytvořit odkaz <xref:System.Data.DataTable.DefaultView%2A> na <xref:System.Data.DataTable>vlastnost .</span><span class="sxs-lookup"><span data-stu-id="c4b12-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="c4b12-105">**Konstruktor DataView** může být prázdný nebo může trvat **datatable** jako jeden argument nebo **DataTable** spolu s kritérii filtru, kritéria řazení a filtr stavu řádku.</span><span class="sxs-lookup"><span data-stu-id="c4b12-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="c4b12-106">Další informace o dalších argumentech, které jsou k dispozici pro použití s **zobrazením DataView**, naleznete v [tématu Řazení a filtrování dat](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="c4b12-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="c4b12-107">Vzhledem k tomu, že index **pro DataView** je vytvořen při vytvoření **DataView** a při změně některé ho **sort**, **RowFilter**nebo **RowStateFilter** vlastnosti, můžete dosáhnout nejlepšího výkonu zadáním jakékoli počáteční pořadí řazení nebo filtrování kritéria jako argumenty konstruktoru při vytváření **DataView**.</span><span class="sxs-lookup"><span data-stu-id="c4b12-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="c4b12-108">Vytvoření **dataview** bez zadání kritéria řazení nebo filtru a potom nastavení **Řazení**, **RowFilter**nebo **RowStateFilter** vlastnosti později způsobí, že index, který má být sestaven alespoň dvakrát: jednou při **dataView** a znovu při změně některé ho řazení nebo filtr vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c4b12-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="c4b12-109">Všimněte si, že pokud vytvoříte **DataView** pomocí konstruktoru, který nepřijímá žádné argumenty, nebude možné použít **DataView,** dokud jste nastavili **Table** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c4b12-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="c4b12-110">Následující příklad kódu ukazuje, jak vytvořit **DataView** pomocí **konstruktoru DataView.**</span><span class="sxs-lookup"><span data-stu-id="c4b12-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="c4b12-111">**RowFilter**, **Sort** sloupec a **DataViewRowState** jsou dodávány spolu s **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="c4b12-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],
    "Country = 'USA'",
    "ContactName",
    DataViewRowState.CurrentRows);  
```  
  
 <span data-ttu-id="c4b12-112">Následující příklad kódu ukazuje, jak získat odkaz na výchozí **DataView** **datatable** pomocí **DefaultView** vlastnost tabulky.</span><span class="sxs-lookup"><span data-stu-id="c4b12-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4b12-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4b12-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="c4b12-114">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="c4b12-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="c4b12-115">Řazení a filtrování dat</span><span class="sxs-lookup"><span data-stu-id="c4b12-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="c4b12-116">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="c4b12-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="c4b12-117">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c4b12-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
