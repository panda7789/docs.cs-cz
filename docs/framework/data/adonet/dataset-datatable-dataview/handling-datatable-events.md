---
title: Zpracování událostí datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: ef9fcd31253283248dfe773ac4dde4fcbb358a2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660980"
---
# <a name="handling-datatable-events"></a>Zpracování událostí datové tabulky
<xref:System.Data.DataTable> Objekt, který poskytuje řadu událostí, které mohou být zpracovány aplikací. Následující tabulka popisuje `DataTable` události.  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Nastane po <xref:System.Data.DataTable.EndInit%2A> metodu `DataTable` je volána. Tato událost je určený primárně pro zajištění podpory scénářů návrhu.|  
|<xref:System.Data.DataTable.ColumnChanged>|Vyvolá se po hodnotu po úspěšném provedení změny v <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Nastane, pokud hodnota byla odeslána k `DataColumn`.|  
|<xref:System.Data.DataTable.RowChanged>|Nastane po `DataColumn` hodnotu nebo <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRow> v `DataTable` byl úspěšně změněn.|  
|<xref:System.Data.DataTable.RowChanging>|Nastane, pokud se odeslal změnu `DataColumn` hodnotu nebo `RowState` z `DataRow` v `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Nastane po `DataRow` v `DataTable` byl označen jako `Deleted`.|  
|<xref:System.Data.DataTable.RowDeleting>|Vyvolá se před `DataRow` v `DataTable` je označen jako `Deleted`.|  
|<xref:System.Data.DataTable.TableCleared>|Vyvolá se po volání <xref:System.Data.DataTable.Clear%2A> metodu `DataTable` úspěšně vymazala každý `DataRow`.|  
|<xref:System.Data.DataTable.TableClearing>|Nastane po `Clear` metoda je volána, ale předtím, než `Clear` zahájení operace.|  
|<xref:System.Data.DataTable.TableNewRow>|Dojde poté, co je nového `DataRow` je vytvořen voláním `NewRow` metodu `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Nastane, když `DataTable` je `Disposed`. Zděděno z <xref:System.ComponentModel.MarshalByValueComponent>.|  
  
> [!NOTE]
>  Většinu operací, které přidávat a odstraňovat řádky nevyvolávejte `ColumnChanged` a `ColumnChanging` události. Ale `ReadXml` vyvolat metodu `ColumnChanged` a `ColumnChanging` události, není-li `XmlReadMode` je nastavena na `DiffGram` nebo je nastaven na `Auto` po dokumentu XML, který je čten `DiffGram`.  
  
> [!WARNING]
>  Poškození dat může dojít, pokud se při změně dat `DataSet` ze kterého `RowChanged` událost se vyvolá. Pokud dojde k poškození těchto dat, bude vyvolána žádná výjimka.  
  
## <a name="additional-related-events"></a>Další související události  
 <xref:System.Data.DataTable.Constraints%2A> Obsahuje vlastnost <xref:System.Data.ConstraintCollection> instance. <xref:System.Data.ConstraintCollection> Třídy zpřístupňuje <xref:System.Data.ConstraintCollection.CollectionChanged> událostí. Tato událost se aktivuje při přidání, změnit nebo odebrat z omezení `ConstraintCollection`.  
  
 <xref:System.Data.DataTable.Columns%2A> Obsahuje vlastnost <xref:System.Data.DataColumnCollection> instance. `DataColumnCollection` Třídy zpřístupňuje <xref:System.Data.DataColumnCollection.CollectionChanged> událostí. Tato událost aktivuje, když `DataColumn` je přidat, upravit nebo odebrat z `DataColumnCollection`. Změny, které způsobují na aktivaci události zahrnují změny názvu, typu, výraz nebo pořadí sloupce.  
  
 <xref:System.Data.DataSet.Tables%2A> Vlastnost <xref:System.Data.DataSet> obsahuje <xref:System.Data.DataTableCollection> instance. `DataTableCollection` Třídy vystaví oba `CollectionChanged` a `CollectionChanging` událostí. Vyvolat tyto události, kdy `DataTable` je přidán či odebrán z `DataSet`.  
  
 Změny `DataRows` také mohou aktivovat události pro přidružené <xref:System.Data.DataView>. `DataView` Třídy zpřístupňuje <xref:System.Data.DataView.ListChanged> událost, která se spustí při `DataColumn` změny hodnot nebo když se změní složení nebo pořadí řazení zobrazení. <xref:System.Data.DataRowView> Třídy zpřístupňuje <xref:System.Data.DataRowView.PropertyChanged> událost, která je vyvoláno, když je přiřazený `DataColumn` hodnota se mění.  
  
## <a name="sequence-of-operations"></a>Posloupnost operací  
 Tady je posloupnost operací, ke kterým dochází při `DataRow` je přidat, upravit nebo odstranit:  
  
1.  Vytváření navrhovaná záznam a použity všechny změny.  
  
2.  Kontrola omezení u sloupců bez výrazu.  
  
3.  Vyvolat `RowChanging` nebo `RowDeleting` události podle potřeby.  
  
4.  Nastavte navrhovaných záznam na aktuální záznam.  
  
5.  Aktualizujte všechny přidružené indexy.  
  
6.  Vyvolat `ListChanged` související události pro `DataView` objekty a `PropertyChanged` související události pro `DataRowView` objekty.  
  
7.  Vyhodnoťte všechny sloupce výrazu, ale zpoždění kontroly jakákoliv omezení u těchto sloupců.  
  
8.  Vyvolat `ListChanged` související události pro `DataView` objekty a `PropertyChanged` související události pro `DataRowView` objekty ovlivněné vyhodnocení výrazu sloupce.  
  
9. Vyvolat `RowChanged` nebo `RowDeleted` události podle potřeby.  
  
10. Kontrola omezení na sloupec.  
  
> [!NOTE]
>  Změny výrazu sloupce nikdy vyvolat `DataTable` události. Změny výrazu sloupce pouze zvýšit `DataView` a `DataRowView` události. Výraz sloupce mohou mít závislosti na několik dalších sloupců a může být vyhodnocen více než jednou během jediné `DataRow` operace. Každé vyhodnocení výrazu vyvolává události a jediného `DataRow` může operace vyvolat více `ListChanged` a `PropertyChanged` události, kdy výrazu sloupce ovlivňuje, včetně více událostí pro stejný sloupec výrazu.  
  
> [!WARNING]
>  Nevyvolají výjimku <xref:System.NullReferenceException> v rámci `RowChanged` obslužné rutiny události. Pokud <xref:System.NullReferenceException> je vyvolána v rámci `RowChanged` události `DataTable`, pak bude `DataTable` poškozen.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit obslužné rutiny událostí pro `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, a `TableClearing` události. Když se aktivuje Každá obslužná rutina události zobrazí výstup v okně konzoly.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Manipulace s daty v datové tabulce](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [Zpracování událostí adaptéru dat](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md)
- [Zpracování událostí datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
