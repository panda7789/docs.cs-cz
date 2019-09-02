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
# <a name="datarows-and-datarowviews"></a>DataRows a DataRowViews
Zpřístupňuje vyčíslitelné <xref:System.Data.DataRowView> kolekce objektů. <xref:System.Data.DataView> Objekty **DataRowView** zpřístupňují hodnoty jako pole objektů, která jsou indexována buď názvem, nebo odkazem na pořadové číslo sloupce v podkladové tabulce. Přístup k <xref:System.Data.DataRow> , který je zpřístupněn **DataRowView** , můžete získat pomocí <xref:System.Data.DataRowView.Row%2A> vlastnosti **DataRowView**.  
  
 Při zobrazení hodnot pomocí **DataRowView** <xref:System.Data.DataView.RowStateFilter%2A> vlastnost **DataView** určuje, která verze řádku podkladového objektu **DataRow** je vystavena. Informace o přístupu k různým verzím řádků pomocí objektu **DataRow**naleznete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).  
  
 Následující příklad kódu zobrazí všechny aktuální a původní hodnoty v tabulce.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [Zobrazení dat](dataviews.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
