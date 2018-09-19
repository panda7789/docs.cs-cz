---
title: Vytvoření zobrazení dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: b88df66ef2e065d1db8d4033eb1fb0e47ebdd189
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45994001"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="77f50-102">Vytvoření zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="77f50-102">Creating a DataView</span></span>
<span data-ttu-id="77f50-103">Existují dva způsoby, jak vytvořit <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="77f50-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="77f50-104">Můžete použít **DataView** konstruktoru, nebo můžete vytvořit odkaz na <xref:System.Data.DataTable.DefaultView%2A> vlastnost <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="77f50-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="77f50-105">**DataView** konstruktor může být prázdný, nebo může trvat buď **DataTable** jako jediný argument, nebo **DataTable** spolu s kritéria filtru, kritéria řazení a řádek Filtr stavu.</span><span class="sxs-lookup"><span data-stu-id="77f50-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="77f50-106">Další informace o další argumenty nejsou k dispozici pro použití se službou **DataView**, naleznete v tématu [řazení a filtrování dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span><span class="sxs-lookup"><span data-stu-id="77f50-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="77f50-107">Protože index **DataView** tvoříme tak i v případě **DataView** je vytvořen a při jejich **řazení**, **RowFilter**, nebo  **Vlastnost RowStateFilter** jsou upraveny vlastnosti Description, dosáhnout co nejlepšího výkonu tím, že poskytuje všechny počáteční řazení nebo filtrování kritéria jako argumenty konstruktoru, když vytvoříte **DataView**.</span><span class="sxs-lookup"><span data-stu-id="77f50-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="77f50-108">Vytváření **DataView** bez zadání kritéria řazení nebo filtrování a pak nastavení **řazení**, **RowFilter**, nebo **Vlastnost RowStateFilter** Vlastnosti později způsobí, že index, který má být sestaven alespoň dvakrát: až při **DataView** je vytvořen, a znovu když některé vlastnosti řazení nebo filtrování se upraví.</span><span class="sxs-lookup"><span data-stu-id="77f50-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="77f50-109">Všimněte si, že pokud vytvoříte **DataView** pomocí konstruktoru, který nepřijímá žádné argumenty, nebudete moct používat **DataView** dokud nenastavíte **tabulky** vlastnost .</span><span class="sxs-lookup"><span data-stu-id="77f50-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="77f50-110">Následující příklad kódu ukazuje, jak vytvořit **DataView** pomocí **DataView** konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="77f50-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="77f50-111">A **RowFilter**, **řazení** sloupci a **DataViewRowState** dodávají spolu s **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="77f50-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="77f50-112">Následující příklad kódu ukazuje, jak získat odkaz na výchozí hodnotu **DataView** z **DataTable** pomocí **výchozí zobrazení** vlastnost tabulky.</span><span class="sxs-lookup"><span data-stu-id="77f50-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="77f50-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="77f50-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="77f50-114">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="77f50-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="77f50-115">Řazení a filtrování dat</span><span class="sxs-lookup"><span data-stu-id="77f50-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="77f50-116">Datové tabulky</span><span class="sxs-lookup"><span data-stu-id="77f50-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="77f50-117">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="77f50-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
