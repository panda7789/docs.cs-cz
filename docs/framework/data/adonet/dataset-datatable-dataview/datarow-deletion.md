---
title: Odstranění datového řádku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: e7e687dfa6af47161be9d26054eb58f319a5099d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425593"
---
# <a name="datarow-deletion"></a>Odstranění datového řádku
Existují dvě metody, které slouží k odstranění <xref:System.Data.DataRow> objektu z <xref:System.Data.DataTable> objektu: **odebrat** metodu <xref:System.Data.DataRowCollection> objektu a <xref:System.Data.DataRow.Delete%2A> metodu **DataRow**objektu. Vzhledem k tomu <xref:System.Data.DataRowCollection.Remove%2A> metoda odstraní **DataRow** z **kolekci DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> metoda pouze označuje řádek pro odstranění. Skutečné odebrání dochází, když aplikace volá **metoda AcceptChanges** metody. S použitím <xref:System.Data.DataRow.Delete%2A>, můžete prostřednictvím kódu programu zkontrolovat, které řádky jsou označená k odstranění předtím než je ve skutečnosti odeberete. Pokud je řádek označený k odstranění, jeho <xref:System.Data.DataRow.RowState%2A> je nastavena na <xref:System.Data.DataRow.Delete%2A>.  
  
 Ani <xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> by měla být volána ve smyčce foreach během iterace <xref:System.Data.DataRowCollection> objektu. <xref:System.Data.DataRow.Delete%2A> ani <xref:System.Data.DataRowCollection.Remove%2A> upravují stav kolekce.  
  
 Při použití <xref:System.Data.DataSet> nebo **DataTable** ve spojení s **DataAdapter** a zdroje relačních dat, použijte **odstranit** metodu  **Objekt DataRow** odebrat řádek. **Odstranit** metoda řádek bude označen jako **odstraněné** v **datovou sadu** nebo **DataTable** , ale neodstraní ho. Místo toho, když **DataAdapter** zaznamená řádek označený jako **odstraněné**, se provede jeho **událost DeleteCommand** metoda odstraňte řádek ve zdroji dat. Na řádku můžete poté trvale odebrány **metoda AcceptChanges** metody. Pokud používáte **odebrat** odstranění řádku, řádku je zcela odeberou z tabulky, ale **DataAdapter** nedojde k odstranění řádků ve zdroji dat.  
  
 **Odebrat** metodu **kolekci DataRowCollection** přijímá **DataRow** jako argument a odebere ji z kolekce, jak je znázorněno v následujícím příkladu.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Naproti tomu následující příklad ukazuje, jak volat **odstranit** metodu na **DataRow** změnit jeho **RowState** k **odstraněné** .  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Pokud je řádek označený k odstranění a zavoláte **metoda AcceptChanges** metodu **DataTable** objekt řádku je odebrán z **DataTable**. Naopak pokud zavoláte **RejectChanges**, **RowState** řádku, který se vrátí do byl před jako **odstraněné**.  
  
> [!NOTE]
>  Pokud **RowState** z **DataRow** je **přidané**, znamená to zrovna došlo k přidání do tabulky a pak je označen jako **odstraněné**, je odebrat z tabulky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
