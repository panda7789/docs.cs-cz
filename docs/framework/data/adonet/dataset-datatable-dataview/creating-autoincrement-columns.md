---
title: Vytváření sloupců s automatickým navyšováním
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 5e4a36829107480a44980c7210b39c21231c67f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786451"
---
# <a name="creating-autoincrement-columns"></a>Vytváření sloupců s automatickým navyšováním
Chcete-li zajistit jedinečné hodnoty sloupce, můžete nastavit hodnoty sloupce tak, aby byly automaticky zvyšovány při přidání nových řádků do tabulky. Chcete-li vytvořit automatické přičítání <xref:System.Data.DataColumn>, <xref:System.Data.DataColumn.AutoIncrement%2A> nastavte vlastnost sloupce na **hodnotu true**. Pak začíná hodnotou definovanou <xref:System.Data.DataColumn.AutoIncrementSeed%2A> ve vlastnosti a každým řádkem přidaným do sloupce **autoincrements** se <xref:System.Data.DataColumn.AutoIncrementStep%2A> zvyšuje hodnota definovaná ve vlastnosti sloupce. <xref:System.Data.DataColumn>  
  
 Pro sloupce **AutoIncrement** doporučujeme, aby <xref:System.Data.DataColumn.ReadOnly%2A> vlastnost **DataColumn** byla nastavena na **hodnotu true**.  
  
 Následující příklad ukazuje, jak vytvořit sloupec, který začíná hodnotou 200 a postupně se přidá do kroků 3.  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataColumn>
- [Definice schématu datové tabulky](datatable-schema-definition.md)
- [Datové tabulky](datatables.md)
- [Přehled ADO.NET](../ado-net-overview.md)
