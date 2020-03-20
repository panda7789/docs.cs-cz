---
title: DataRows a DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 14e7e1ccb051410c351e49afee9f2d6809264833
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151296"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="e991f-102">DataRows a DataRowViews</span><span class="sxs-lookup"><span data-stu-id="e991f-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="e991f-103">A <xref:System.Data.DataView> zpřístupňuje výčtu <xref:System.Data.DataRowView> kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="e991f-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="e991f-104">Objekty **DataRowView** zveřejňují hodnoty jako pole objektů, které jsou indexovány názvem nebo ordinálním odkazem na sloupec v podkladové tabulce.</span><span class="sxs-lookup"><span data-stu-id="e991f-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="e991f-105">Můžete <xref:System.Data.DataRow> přistupovat, který je vystaven **DataRowView** pomocí <xref:System.Data.DataRowView.Row%2A> **vlastnosti DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="e991f-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="e991f-106">Při zobrazení hodnot pomocí **DataRowView** <xref:System.Data.DataView.RowStateFilter%2A> , vlastnost **DataView** určuje, která verze řádku podkladového **DataRow** je vystavena.</span><span class="sxs-lookup"><span data-stu-id="e991f-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="e991f-107">Informace o přístupu k různým verzím řádků pomocí **datarow**, naleznete v [tématu Stavy řádků a Verze řádků](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="e991f-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="e991f-108">Následující příklad kódu zobrazuje všechny aktuální a původní hodnoty v tabulce.</span><span class="sxs-lookup"><span data-stu-id="e991f-108">The following code example displays all the current and original values in a table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e991f-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e991f-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="e991f-110">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="e991f-110">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="e991f-111">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e991f-111">ADO.NET Overview</span></span>](../ado-net-overview.md)
