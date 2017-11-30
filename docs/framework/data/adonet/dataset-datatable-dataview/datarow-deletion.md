---
title: "Odstranění DataRow"
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
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f9eb89d711cbf66f3b6816e597c14359be1f3639
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datarow-deletion"></a>Odstranění DataRow
Existují dvě metody, které můžete použít k odstranění <xref:System.Data.DataRow> objektu z <xref:System.Data.DataTable> objektu: **odebrat** metodu <xref:System.Data.DataRowCollection> objekt a <xref:System.Data.DataRow.Delete%2A> metodu **DataRow**objektu. Zatímco <xref:System.Data.DataRowCollection.Remove%2A> metoda odstranění **DataRow** z **kolekci DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> metoda pouze označí řádek pro odstranění. Skutečné odebrání nastane, když aplikace volá **metoda AcceptChanges** metoda. Pomocí <xref:System.Data.DataRow.Delete%2A>, můžete programově zkontrolovat řádky jsou označena pro odstranění před skutečného odstranění. Když řádek je označena pro odstranění, jeho <xref:System.Data.DataRow.RowState%2A> je nastavena na <xref:System.Data.DataRow.Delete%2A>.  
  
 Ani <xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> by měla být volána v smyčka typu foreach při iterace v rámci <xref:System.Data.DataRowCollection> objektu. <xref:System.Data.DataRow.Delete%2A>ani <xref:System.Data.DataRowCollection.Remove%2A> změnit stav kolekce.  
  
 Při použití <xref:System.Data.DataSet> nebo **DataTable** ve spojení s **DataAdapter** a zdroje relačních dat, použijte **odstranit** metodu  **DataRow** odebrat řádek. **Odstranit** metoda řádek označí jako **odstraněné** v **datovou sadu** nebo **DataTable** ale nedojde k jeho odebrání. Místo toho, když **DataAdapter** zaznamená řádek označený jako **odstraněné**, se provede jeho **DeleteCommand** metoda k odstranění řádku ve zdroji dat. Řádek se dá pak trvale odebrat pomocí **metoda AcceptChanges** metoda. Pokud používáte **odebrat** k odstranění řádku, řádku je zcela odeberou z tabulky, ale **DataAdapter** řádek ve zdroji dat se neodstraní.  
  
 **Odebrat** metodu **kolekci DataRowCollection** trvá **DataRow** jako argument a odebere ji z kolekce, jak je znázorněno v následujícím příkladu.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Naproti tomu následující příklad ukazuje, jak volat **odstranit** metodu **DataRow** změnit jeho **RowState** k **odstraněné** .  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Pokud řádek je označena pro odstranění a volání **metoda AcceptChanges** metodu **DataTable** objektu řádek je odebrán z **DataTable**. Naproti tomu při volání **RejectChanges**, **RowState** řádku přejde do stavu, který byl před označit jako **odstraněné**.  
  
> [!NOTE]
>  Pokud **RowState** z **DataRow** je **Added**, znamená ho právě byl přidán do tabulky, a pak je označen jako **odstraněné**, je Odebere z tabulky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [Manipulace s daty v DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
