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
# <a name="datarows-and-datarowviews"></a>DataRows a DataRowViews
A <xref:System.Data.DataView> zpřístupňuje výčtu <xref:System.Data.DataRowView> kolekce objektů. Objekty **DataRowView** zveřejňují hodnoty jako pole objektů, které jsou indexovány názvem nebo ordinálním odkazem na sloupec v podkladové tabulce. Můžete <xref:System.Data.DataRow> přistupovat, který je vystaven **DataRowView** pomocí <xref:System.Data.DataRowView.Row%2A> **vlastnosti DataRowView**.  
  
 Při zobrazení hodnot pomocí **DataRowView** <xref:System.Data.DataView.RowStateFilter%2A> , vlastnost **DataView** určuje, která verze řádku podkladového **DataRow** je vystavena. Informace o přístupu k různým verzím řádků pomocí **datarow**, naleznete v [tématu Stavy řádků a Verze řádků](row-states-and-row-versions.md).  
  
 Následující příklad kódu zobrazuje všechny aktuální a původní hodnoty v tabulce.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [Zobrazení dat](dataviews.md)
- [Přehled ADO.NET](../ado-net-overview.md)
