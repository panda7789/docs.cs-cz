---
title: DataRows a DataRowViews
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
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37ba0d69eb7ab400e8cd0babdefdbe4a19459e82
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="datarows-and-datarowviews"></a>DataRows a DataRowViews
A <xref:System.Data.DataView> zpřístupní vyčíslitelná kolekce <xref:System.Data.DataRowView> objekty. **DataRowView** objekty vystavit hodnoty jako pole objektů, které jsou indexované podle názvu nebo odkaz na pořadovém místě sloupce v základní tabulce. Dostanete <xref:System.Data.DataRow> který je zveřejněný prostřednictvím **DataRowView** pomocí <xref:System.Data.DataRowView.Row%2A> vlastnost **DataRowView**.  
  
 Při zobrazení hodnoty pomocí **DataRowView**, <xref:System.Data.DataView.RowStateFilter%2A> vlastnost **DataView** Určuje, která verze řádku základní **DataRow** zpřístupněn. Informace o přístupu k jiné řádek verze, která používá **DataRow**, najdete v části [stavy řádků a verze řádku](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
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
 <xref:System.Data.DataRowVersion>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
