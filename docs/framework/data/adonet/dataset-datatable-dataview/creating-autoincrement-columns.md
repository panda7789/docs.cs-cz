---
title: "Vytváření AutoIncrement sloupců"
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
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4c9c7e321ac5749aedf7168afaef9d6a7119de62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-autoincrement-columns"></a>Vytváření AutoIncrement sloupců
Aby jedinečný sloupec hodnoty, můžete nastavit hodnoty ve sloupcích se zvýší automaticky při přidávání řádků do tabulky. Chcete-li vytvořit automaticky rostoucí <xref:System.Data.DataColumn>, nastavte <xref:System.Data.DataColumn.AutoIncrement%2A> vlastnost sloupce, který se **true**. <xref:System.Data.DataColumn> Pak začíná hodnota definovaná v <xref:System.Data.DataColumn.AutoIncrementSeed%2A> vlastnost a s každým řádkem přidat hodnotu **AutoIncrement** sloupec zvyšuje úroveň hodnota definovaná v <xref:System.Data.DataColumn.AutoIncrementStep%2A> vlastnost sloupce.  
  
 Pro **AutoIncrement** sloupců, doporučujeme, aby <xref:System.Data.DataColumn.ReadOnly%2A> vlastnost **DataColumn** nastavit na **true**.  
  
 Následující příklad ukazuje, jak vytvořit sloupec, který začíná hodnota 200 a přidá postupně v krocích 3.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataColumn>  
 [Definice schématu datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
