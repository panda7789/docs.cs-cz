---
title: Vytváření výraz sloupce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 11bacf436daf2a77a9cf46b4883d282143572e27
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="creating-expression-columns"></a>Vytváření výraz sloupce
Můžete definovat výraz pro sloupec, mu umožní obsahovat hodnotu vypočítat z jiné hodnoty sloupců na stejném řádku nebo z hodnoty ve sloupcích více řádků v tabulce. Chcete-li definovat výraz, který se vyhodnotí, použijte <xref:System.Data.DataColumn.Expression%2A> vlastnost cílového sloupce použijte <xref:System.Data.DataColumn.ColumnName%2A> vlastnost, která má odkazovat na jiné sloupce ve výrazu. <xref:System.Data.DataColumn.DataType%2A> Sloupec musí být výraz odpovídající hodnotu, která vrací výraz.  
  
 Následující tabulka uvádí několik možných používá pro výraz sloupce v tabulce.  
  
|Typ výrazu|Příklad|  
|---------------------|-------------|  
|Srovnání|"Celkový > = 500"|  
|Výpočet|"UnitPrice * množství"|  
|Agregace|Výraz sum(price)|  
  
 Můžete nastavit **výraz** vlastnost na existujícím **DataColumn** objekt, nebo můžete zahrnout vlastnost jako třetí argument předaný <xref:System.Data.DataColumn> konstruktoru, jak je znázorněno v následujícím příkladu.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 Výrazy mohou odkazovat na jiné výrazu sloupce; Cyklický odkaz, ve kterém dvou výrazů odkazovat na sebe, ale vygeneruje výjimku. Pravidla o zapisují se výrazy, najdete v článku <xref:System.Data.DataColumn.Expression%2A> vlastnost **DataColumn** třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [Definice schématu datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
