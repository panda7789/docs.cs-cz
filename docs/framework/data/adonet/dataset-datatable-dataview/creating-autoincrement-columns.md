---
title: Vytváření sloupců s automatickým navyšováním
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: b4beffb3c5072e9eaa398e7433b363babadbb9eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528638"
---
# <a name="creating-autoincrement-columns"></a>Vytváření sloupců s automatickým navyšováním
Aby se zajistilo jedinečný sloupec hodnot, můžete nastavit hodnoty ve sloupcích se zvýší automaticky při přidání nových řádků do tabulky. Vytvoření automatickým přírůstkem <xref:System.Data.DataColumn>, nastavte <xref:System.Data.DataColumn.AutoIncrement%2A> vlastnost sloupec, který se **true**. <xref:System.Data.DataColumn> Pak začíná hodnota definovaná v <xref:System.Data.DataColumn.AutoIncrementSeed%2A> vlastnost a u každého řádku přidat hodnotu **AutoIncrement** sloupec zvýší o hodnotu definovanou v <xref:System.Data.DataColumn.AutoIncrementStep%2A> vlastnost sloupce.  
  
 Pro **AutoIncrement** sloupce, doporučujeme, aby <xref:System.Data.DataColumn.ReadOnly%2A> vlastnost **DataColumn** nastavit na **true**.  
  
 Následující příklad ukazuje, jak vytvořit sloupec, který se spustí s hodnotou 200 a přidá postupně v krocích 3.  
  
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
- [Definice schématu datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
