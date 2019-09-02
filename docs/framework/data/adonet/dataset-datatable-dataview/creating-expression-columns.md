---
title: Vytváření sloupců výrazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: 8ae8c8e020a3d8ada5bdcd5037187e6f3abd33a4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203848"
---
# <a name="creating-expression-columns"></a>Vytváření sloupců výrazů
Můžete definovat výraz pro sloupec, který umožňuje, aby obsahoval hodnotu vypočítanou z jiných hodnot sloupce ve stejném řádku nebo z hodnot sloupců s více řádky v tabulce. Chcete-li definovat výraz, který má být vyhodnocen, použijte <xref:System.Data.DataColumn.Expression%2A> vlastnost cílového sloupce a <xref:System.Data.DataColumn.ColumnName%2A> použijte vlastnost pro odkaz na jiné sloupce ve výrazu. <xref:System.Data.DataColumn.DataType%2A> Hodnota sloupce Expression musí být vhodná pro hodnotu, kterou výraz vrátí.  
  
 Následující tabulka uvádí několik možných použití pro sloupce výrazů v tabulce.  
  
|Typ výrazu|Příklad|  
|---------------------|-------------|  
|Srovnání|"Total > = 500"|  
|Běhu|"JednotkováCena * množství"|  
|Agregace|Sum (price)|  
  
 Můžete nastavit vlastnost **Expression** pro existující objekt DataColumn nebo můžete vlastnost zahrnout jako třetí argument <xref:System.Data.DataColumn> předaný konstruktoru, jak je znázorněno v následujícím příkladu.  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 Výrazy můžou odkazovat na jiné sloupce výrazu; Nicméně cyklický odkaz, ve kterém dva výrazy odkazují na sebe navzájem, vygenerují výjimku. Pravidla týkající se psaní výrazů naleznete v tématu <xref:System.Data.DataColumn.Expression%2A> vlastnost třídy DataColumn.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [Definice schématu datové tabulky](datatable-schema-definition.md)
- [Datové tabulky](datatables.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
