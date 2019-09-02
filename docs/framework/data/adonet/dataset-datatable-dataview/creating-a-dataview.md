---
title: Vytvoření zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 391c071f19149e9690c9121b1094aef5bfa605cd
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203839"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="11fe6-102">Vytvoření zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="11fe6-102">Creating a DataView</span></span>
<span data-ttu-id="11fe6-103">Existují dva způsoby, jak vytvořit <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="11fe6-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="11fe6-104">Můžete použít konstruktor **DataView** , nebo můžete vytvořit odkaz na <xref:System.Data.DataTable.DefaultView%2A> vlastnost. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="11fe6-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="11fe6-105">Konstruktor **DataView** může být prázdný nebo může přijmout buď **DataTable** jako jeden argument, nebo **objekt DataTable** spolu s kritérii filtru, kritérii řazení a filtrem stavu řádků.</span><span class="sxs-lookup"><span data-stu-id="11fe6-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="11fe6-106">Další informace o dalších argumentech, které jsou k dispozici pro použití s **objektem DataView**, najdete v tématu [řazení a filtrování dat](sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="11fe6-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="11fe6-107">Vzhledem k tomu, že index pro zobrazení **dat** je sestaven při vytváření zobrazení **DataView** , a když se změní kterákoli z vlastností **Sort**, **RowFilter vyžaduje hodnotu**nebo **vlastnost RowStateFilter** , dosáhnete nejlepšího výkonu zadáním počáteční pořadí řazení nebo kritéria filtrování jako argumenty konstruktoru při vytváření zobrazení **DataView**.</span><span class="sxs-lookup"><span data-stu-id="11fe6-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="11fe6-108">Vytvořením objektu **DataView** bez zadání kritérií pro řazení nebo filtrování a následným nastavením vlastností **Sort**, **RowFilter vyžaduje hodnotu**nebo **vlastnost RowStateFilter** dojde k tomu, že se index sestaví alespoň dvakrát: když je zobrazení **DataView** vytvořen a znovu po úpravě vlastnosti řazení nebo filtru.</span><span class="sxs-lookup"><span data-stu-id="11fe6-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="11fe6-109">Všimněte si, že pokud vytvoříte zobrazení **DataView** pomocí konstruktoru, který nepřijímá žádné argumenty, nebudete moci použít **objekt DataView** , dokud nenastavíte vlastnost **Table** .</span><span class="sxs-lookup"><span data-stu-id="11fe6-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="11fe6-110">Následující příklad kódu ukazuje, jak vytvořit **DataView** pomocí konstruktoru **DataView** .</span><span class="sxs-lookup"><span data-stu-id="11fe6-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="11fe6-111">**RowFilter vyžaduje hodnotu**, sloupec **řazení** a **DataViewRowState** jsou zadány spolu s objektem **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="11fe6-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="11fe6-112">Následující příklad kódu ukazuje, jak získat odkaz na výchozí **objekt DataView** **objektu DataTable** pomocí vlastnosti " **výchozí zobrazení** " tabulky.</span><span class="sxs-lookup"><span data-stu-id="11fe6-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="11fe6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11fe6-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="11fe6-114">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="11fe6-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="11fe6-115">Řazení a filtrování dat</span><span class="sxs-lookup"><span data-stu-id="11fe6-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="11fe6-116">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="11fe6-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="11fe6-117">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="11fe6-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
