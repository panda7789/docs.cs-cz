---
title: "Zpracování událostí DataTable"
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
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 30425680333bfebddcd7a34ac1cd2a07b1556d91
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="handling-datatable-events"></a>Zpracování událostí DataTable
<xref:System.Data.DataTable> Objekt poskytuje řadu událostí, které může zpracovat aplikace. Následující tabulka popisuje `DataTable` události.  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Nastane po <xref:System.Data.DataTable.EndInit%2A> metodu `DataTable` je volána. Tato událost je určená hlavně pro podporu scénáře návrhu.|  
|<xref:System.Data.DataTable.ColumnChanged>|Vyskytne se po hodnotu po úspěšném provedení změny v <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Nastane, když byla odeslána hodnotu pro `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Nastane po `DataColumn` hodnotu nebo <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRow> v `DataTable` úspěšně změnil.|  
|<xref:System.Data.DataTable.RowChanging>|Nastane, když byla odeslána pro změnu `DataColumn` hodnotu nebo `RowState` z `DataRow` v `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Nastane po `DataRow` v `DataTable` byl označen jako `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Dojde před `DataRow` v `DataTable` je označena jako `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Nastane po volání <xref:System.Data.DataTable.Clear%2A> metodu `DataTable` má úspěšně vymazán každých `DataRow`.|  
|<xref:System.Data.DataTable.TableClearing>|Nastane po `Clear` metoda je volána ale předtím, než `Clear` začíná operace.|  
|<xref:System.Data.DataTable.TableNewRow>|Nastane po novou `DataRow` byla vytvořena ve volání `NewRow` metodu `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Nastane při `DataTable` je `Disposed`. Zděděno z <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
>  Většinu operací, které přidání nebo odstranění řádků není vyvolat `ColumnChanged` a `ColumnChanging` události. Však `ReadXml` vyvolat metodu `ColumnChanged` a `ColumnChanging` událostí, pokud `XmlReadMode` je nastaven na `DiffGram` nebo je nastaven na `Auto` po dokument XML, který je čten `DiffGram`.  
  
> [!WARNING]
>  Poškození dat může dojít, pokud je při změně dat `DataSet` ze kterého `RowChanged` událost se vyvolá. Pokud dojde k poškození těchto dat, bude vyvolána žádná výjimka.  
  
## <a name="additional-related-events"></a>Další související události  
 <xref:System.Data.DataTable.Constraints%2A> Vlastnost blokování <xref:System.Data.ConstraintCollection> instance. <xref:System.Data.ConstraintCollection> Třídy zpřístupňuje <xref:System.Data.ConstraintCollection.CollectionChanged> událostí. Tato událost aktivuje se v případě omezení je přidat, upravit nebo odebrat z `ConstraintCollection`.  
  
 <xref:System.Data.DataTable.Columns%2A> Vlastnost blokování <xref:System.Data.DataColumnCollection> instance. `DataColumnCollection` Třídy zpřístupňuje <xref:System.Data.DataColumnCollection.CollectionChanged> událostí. Tato událost aktivuje, když `DataColumn` je přidat, upravit nebo odebrat z `DataColumnCollection`. Úpravy, které způsobí na aktivaci události zahrnují změny název, typ, výraz nebo pořadové číslo pozice sloupce.  
  
 <xref:System.Data.DataSet.Tables%2A> Vlastnost <xref:System.Data.DataSet> obsahuje <xref:System.Data.DataTableCollection> instance. `DataTableCollection` Třída zpřístupňuje jak `CollectionChanged` a `CollectionChanging` událostí. Tyto události provést, když `DataTable` je přidat nebo odebrat z `DataSet`.  
  
 Změny `DataRows` můžou taky aktivovat události pro přidružené <xref:System.Data.DataView>. `DataView` Třídy zpřístupňuje <xref:System.Data.DataView.ListChanged> událost, která se spustí při `DataColumn` změny hodnot nebo při změně složení nebo řazení pořadí zobrazení. <xref:System.Data.DataRowView> Třídy zpřístupňuje <xref:System.Data.DataRowView.PropertyChanged> událost, která aktivuje se v případě přiřazený `DataColumn` hodnotu změny.  
  
## <a name="sequence-of-operations"></a>Posloupnost operací  
 Tady je pořadí operací, ke kterým dochází při `DataRow` je přidat, upravit nebo odstranit:  
  
1.  Navrhované záznam vytvořit a použít všechny změny.  
  
2.  Zkontrolujte omezení pro výraz sloupce.  
  
3.  Vyvolat `RowChanging` nebo `RowDeleting` události podle vhodnosti.  
  
4.  Nastavte navrhované záznam na aktuální záznam.  
  
5.  Aktualizujte všechny přidružené indexy.  
  
6.  Vyvolat `ListChanged` související události pro `DataView` objekty a `PropertyChanged` související události pro `DataRowView` objekty.  
  
7.  Vyhodnocení výrazu všechny sloupce, ale zpoždění kontroly žádná omezení pro tyto sloupce.  
  
8.  Vyvolat `ListChanged` související události pro `DataView` objekty a `PropertyChanged` související události pro `DataRowView` objekty vliv hodnocení sloupec výrazu.  
  
9. Vyvolat `RowChanged` nebo `RowDeleted` události podle vhodnosti.  
  
10. Zkontrolujte omezení výrazu sloupce.  
  
> [!NOTE]
>  Změny na výrazu sloupce nikdy vyvolat `DataTable` události. Změny na výrazu sloupce pouze vyvolat `DataView` a `DataRowView` události. Výraz sloupce může mít závislosti na více jiných sloupců a může být vyhodnocen vícekrát během jedné `DataRow` operaci. Každé vyhodnocení výrazu vyvolá události a jedinou `DataRow` operace může být spojeno víc `ListChanged` a `PropertyChanged` událostí v případě, že výraz sloupce jsou ovlivněni, včetně více událostí pro stejný výraz na sloupec.  
  
> [!WARNING]
>  Nevyvolá výjimku <xref:System.NullReferenceException> v rámci `RowChanged` obslužné rutiny události. Pokud <xref:System.NullReferenceException> je vyvolána v rámci `RowChanged` události `DataTable`, pak se `DataTable` poškozen.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit obslužné rutiny pro `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, a `TableClearing` události. Každý obslužná rutina události zobrazí výstup v okně konzoly, když je aktivována.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [Zpracování událostí adaptéru dat](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [Zpracování událostí datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
