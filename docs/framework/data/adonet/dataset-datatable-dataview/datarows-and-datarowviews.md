---
title: DataRows a DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 5bd7ebefc03dbe6b44a199ba3123414e7b282c90
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43390034"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="7933e-102">DataRows a DataRowViews</span><span class="sxs-lookup"><span data-stu-id="7933e-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="7933e-103">A <xref:System.Data.DataView> zpřístupňuje vyčíslitelné kolekce <xref:System.Data.DataRowView> objekty.</span><span class="sxs-lookup"><span data-stu-id="7933e-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="7933e-104">**DataRowView** objekty zpřístupnění hodnot ve formě pole objektů, které jsou indexovány pomocí název nebo Řadový odkaz na sloupec v základní tabulce.</span><span class="sxs-lookup"><span data-stu-id="7933e-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="7933e-105">Můžete přistupovat <xref:System.Data.DataRow> , který je zveřejněný prostřednictvím **DataRowView** pomocí <xref:System.Data.DataRowView.Row%2A> vlastnost **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="7933e-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="7933e-106">Při zobrazení hodnoty pomocí **DataRowView**, <xref:System.Data.DataView.RowStateFilter%2A> vlastnost **DataView** rozhodne, kterou verzi řádku základního **DataRow** je přístupný.</span><span class="sxs-lookup"><span data-stu-id="7933e-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="7933e-107">Informace o přístupu k pomocí verze odlišný řádek **DataRow**, naleznete v tématu [stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="7933e-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="7933e-108">Následující příklad kódu zobrazuje všechny aktuální a původní hodnoty v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7933e-108">The following code example displays all the current and original values in a table.</span></span>  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)      
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7933e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7933e-109">See Also</span></span>  
 <xref:System.Data.DataRowVersion>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="7933e-110">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="7933e-110">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="7933e-111">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="7933e-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
