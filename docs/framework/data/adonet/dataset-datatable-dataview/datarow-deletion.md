---
title: Odstranění datového řádku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 3f48339539f08bbc1c2c15035741375bd9ade553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784719"
---
# <a name="datarow-deletion"></a>Odstranění datového řádku
Existují dvě metody, které <xref:System.Data.DataRow> lze použít k odstranění objektu <xref:System.Data.DataTable> z objektu: <xref:System.Data.DataRow.Delete%2A> metodu <xref:System.Data.DataRowCollection> **Remove** objektu a metodu objektu **DataRow** . Zatímco metoda odstraní **objekt DataRow** z **kolekci DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> metoda označí řádek pouze pro odstranění. <xref:System.Data.DataRowCollection.Remove%2A> Ke skutečnému odebrání dojde, když aplikace zavolá metodu **AcceptChanges** . Pomocí nástroje <xref:System.Data.DataRow.Delete%2A>můžete programově ověřit, které řádky jsou označené k odstranění, než je skutečně odeberete. Když je řádek označený k odstranění, jeho <xref:System.Data.DataRow.RowState%2A> vlastnost je nastavena na. <xref:System.Data.DataRow.Delete%2A>  
  
 Ani ani <xref:System.Data.DataRowCollection.Remove%2A> by neměl být volán ve <xref:System.Data.DataRowCollection> smyčce foreach při iteraci objektu. <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow.Delete%2A>ani <xref:System.Data.DataRowCollection.Remove%2A> nezmění stav kolekce.  
  
 <xref:System.Data.DataSet> Při použití objektu nebo **DataTable** ve spojení s **metodou DataAdapter** a relačním zdrojem dat odeberte řádek pomocí metody **Delete** objektu **DataRow** . Metoda **Delete** označí řádek jako **Odstraněný** v **datové sadě** nebo **DataTable** , ale neodebere jej. Místo toho, když modul **DataAdapter** nalezne řádek označený jako **Odstraněný**, provede jeho metodu **DeleteCommand** k odstranění řádku ve zdroji dat. Řádek je pak možné trvale odebrat pomocí metody **AcceptChanges** . Použijete-li příkaz **Remove** k odstranění řádku, řádek bude z tabulky zcela odebrán, ale objekt **DataAdapter** neodstraní řádek ze zdroje dat.  
  
 Metoda **Remove** **kolekci DataRowCollection** přebírá **objekt DataRow** jako argument a odebírá jej z kolekce, jak je znázorněno v následujícím příkladu.  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 Naopak následující příklad ukazuje, jak zavolat metodu **Delete** na **objekt DataRow** , aby změnila její **RowState** na hodnotu **Deleted**.  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 Pokud je řádek označen pro odstranění a zavoláte metodu **AcceptChanges** objektu **DataTable** , řádek je odebrán z **objektu DataTable**. Naopak pokud voláte **RejectChanges**, **RowState** řádku se vrátí k tomu, co bylo předtím označeno jako **odstraněné**.  
  
> [!NOTE]
> Pokud se **přidá** **RowState** objektu **DataRow** , znamená to, že se právě přidal do tabulky a pak je označený jako **Odstraněný**, odebere se z tabulky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [Přehled ADO.NET](../ado-net-overview.md)
