---
title: "Vytváření v zobrazení DataView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 53cbfc5097c28c0677a164f817cfe14927814d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-dataview"></a><span data-ttu-id="fd037-102">Vytváření v zobrazení DataView</span><span class="sxs-lookup"><span data-stu-id="fd037-102">Creating a DataView</span></span>
<span data-ttu-id="fd037-103">Existují dva způsoby, jak vytvořit <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="fd037-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="fd037-104">Můžete použít **DataView** konstruktoru, nebo můžete vytvořit odkaz na <xref:System.Data.DataTable.DefaultView%2A> vlastnost <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="fd037-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="fd037-105">**DataView** konstruktor nesmí být prázdné nebo může trvat buď **DataTable** jako jeden argument, nebo **DataTable** společně s kritéria filtru, kritéria řazení a řádek Stav filtru.</span><span class="sxs-lookup"><span data-stu-id="fd037-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="fd037-106">Další informace o další argumenty nejsou k dispozici pro použití s **DataView**, najdete v části [řazení a filtrování dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="fd037-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="fd037-107">Protože index **DataView** vychází i v případě **DataView** je vytvořen a při jejich **řazení**, **RowFilter**, nebo  **Vlastnost RowStateFilter** jsou upraveny vlastnosti Description, dosáhnout optimálního výkonu poskytuje všechny počáteční řazení nebo filtrování kritéria jako argumenty konstruktoru, když vytvoříte **DataView**.</span><span class="sxs-lookup"><span data-stu-id="fd037-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="fd037-108">Vytváření **DataView** bez zadání kritéria řazení nebo filtr a pak nastavení **řazení**, **RowFilter**, nebo **Vlastnost RowStateFilter** Vlastnosti později způsobí, že index, který má být sestaven alespoň dvakrát: Jakmile při **DataView** je vytvořen, a znovu jakékoli vlastnosti řazení nebo filtrování jsou změny.</span><span class="sxs-lookup"><span data-stu-id="fd037-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="fd037-109">Všimněte si, že pokud vytvoříte **DataView** pomocí konstruktoru, který nevyžaduje žádné argumenty, nebudete moci používat **DataView** nastaven **tabulky** vlastnost .</span><span class="sxs-lookup"><span data-stu-id="fd037-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="fd037-110">Následující příklad kódu ukazuje, jak vytvořit **DataView** pomocí **DataView** konstruktor.</span><span class="sxs-lookup"><span data-stu-id="fd037-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="fd037-111">A **RowFilter**, **řazení** sloupce a **DataViewRowState** se dodává spolu s **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="fd037-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="fd037-112">Následující příklad kódu ukazuje, jak získat odkaz na výchozí **DataView** z **DataTable** pomocí **výchozí zobrazení** vlastnosti tabulky.</span><span class="sxs-lookup"><span data-stu-id="fd037-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd037-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd037-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="fd037-114">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="fd037-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="fd037-115">Řazení a filtrování dat</span><span class="sxs-lookup"><span data-stu-id="fd037-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="fd037-116">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="fd037-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="fd037-117">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="fd037-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
