---
title: DataRows a DataRowViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: 8a98dc44eda9ebda09235193c58bd831fc52d04d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205087"
---
# <a name="datarows-and-datarowviews"></a><span data-ttu-id="cc3ee-102">DataRows a DataRowViews</span><span class="sxs-lookup"><span data-stu-id="cc3ee-102">DataRows and DataRowViews</span></span>
<span data-ttu-id="cc3ee-103">Zpřístupňuje vyčíslitelné <xref:System.Data.DataRowView> kolekce objektů. <xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="cc3ee-103">A <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="cc3ee-104">Objekty **DataRowView** zpřístupňují hodnoty jako pole objektů, která jsou indexována buď názvem, nebo odkazem na pořadové číslo sloupce v podkladové tabulce.</span><span class="sxs-lookup"><span data-stu-id="cc3ee-104">The **DataRowView** objects expose values as object arrays that are indexed by either the name or the ordinal reference of the column in the underlying table.</span></span> <span data-ttu-id="cc3ee-105">Přístup k <xref:System.Data.DataRow> , který je zpřístupněn **DataRowView** , můžete získat pomocí <xref:System.Data.DataRowView.Row%2A> vlastnosti **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="cc3ee-105">You can access the <xref:System.Data.DataRow> that is exposed by the **DataRowView** by using the <xref:System.Data.DataRowView.Row%2A> property of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="cc3ee-106">Při zobrazení hodnot pomocí **DataRowView** <xref:System.Data.DataView.RowStateFilter%2A> vlastnost **DataView** určuje, která verze řádku podkladového objektu **DataRow** je vystavena.</span><span class="sxs-lookup"><span data-stu-id="cc3ee-106">When you view values by using a **DataRowView**, the <xref:System.Data.DataView.RowStateFilter%2A> property of the **DataView** determines which row version of the underlying **DataRow** is exposed.</span></span> <span data-ttu-id="cc3ee-107">Informace o přístupu k různým verzím řádků pomocí objektu **DataRow**naleznete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="cc3ee-107">For information about accessing different row versions using a **DataRow**, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="cc3ee-108">Následující příklad kódu zobrazí všechny aktuální a původní hodnoty v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cc3ee-108">The following code example displays all the current and original values in a table.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc3ee-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc3ee-109">See also</span></span>

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="cc3ee-110">Zobrazení dat</span><span class="sxs-lookup"><span data-stu-id="cc3ee-110">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="cc3ee-111">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="cc3ee-111">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
