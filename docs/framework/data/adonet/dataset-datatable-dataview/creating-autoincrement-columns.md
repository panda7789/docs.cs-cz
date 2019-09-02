---
title: Vytváření sloupců s automatickým navyšováním
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 2548ad9382b406978dac0a3d366207626278f501
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205128"
---
# <a name="creating-autoincrement-columns"></a>Vytváření sloupců s automatickým navyšováním
Chcete-li zajistit jedinečné hodnoty sloupce, můžete nastavit hodnoty sloupce tak, aby byly automaticky zvyšovány při přidání nových řádků do tabulky. Chcete-li vytvořit automatické přičítání <xref:System.Data.DataColumn>, <xref:System.Data.DataColumn.AutoIncrement%2A> nastavte vlastnost sloupce na **hodnotu true**. Pak začíná <xref:System.Data.DataColumn.AutoIncrementSeed%2A> hodnotou definovanou ve vlastnosti a každým řádkem přidaným do sloupce <xref:System.Data.DataColumn.AutoIncrementStep%2A> autoincrements se zvyšuje hodnota definovaná ve vlastnosti sloupce. <xref:System.Data.DataColumn>  
  
 Pro sloupce AutoIncrement doporučujeme, aby <xref:System.Data.DataColumn.ReadOnly%2A> vlastnost DataColumn byla nastavena na **hodnotu true**.  
  
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
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
