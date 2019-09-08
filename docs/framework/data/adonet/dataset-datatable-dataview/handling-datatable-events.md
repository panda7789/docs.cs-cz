---
title: Zpracování událostí datové tabulky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: 3edafa6c6a1bc3da2abc0598f329caf0e2f21e8b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786260"
---
# <a name="handling-datatable-events"></a>Zpracování událostí datové tabulky
<xref:System.Data.DataTable> Objekt poskytuje řadu událostí, které mohou být zpracovány aplikací. Následující tabulka popisuje `DataTable` události.  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|Nastane po <xref:System.Data.DataTable.EndInit%2A> volání metody a `DataTable` . Tato událost je určená primárně pro podporu scénářů návrhu.|  
|<xref:System.Data.DataTable.ColumnChanged>|Vyvolá se po úspěšné změně hodnoty v <xref:System.Data.DataColumn>.|  
|<xref:System.Data.DataTable.ColumnChanging>|Vyvolá se v případě, že byla odeslána hodnota `DataColumn`pro.|  
|<xref:System.Data.DataTable.RowChanged>|Vyvolá se po `DataColumn` úspěšné změně hodnoty <xref:System.Data.DataRow.RowState%2A> nebo z <xref:System.Data.DataRow> v `DataTable` .|  
|<xref:System.Data.DataTable.RowChanging>|Nastane, pokud byla odeslána Změna `DataColumn` pro hodnotu `RowState` nebo z a `DataRow` v `DataTable`.|  
|<xref:System.Data.DataTable.RowDeleted>|Nastane po `DataRow` `DataTable` označení jako .`Deleted`|  
|<xref:System.Data.DataTable.RowDeleting>|Vyvolá se před `DataRow` znakem `DataTable` v, který `Deleted`je označen jako.|  
|<xref:System.Data.DataTable.TableCleared>|Nastane po volání <xref:System.Data.DataTable.Clear%2A> metody, která se úspěšně vymazala každé `DataTable` `DataRow`z nich.|  
|<xref:System.Data.DataTable.TableClearing>|Nastane po volání `Clear` metody, ale `Clear` před začátkem operace.|  
|<xref:System.Data.DataTable.TableNewRow>|Nastane po vytvoření nového `DataRow` voláním `NewRow` metody `DataTable`.|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|Vyvolá se v `DataTable` případě `Disposed`, že je. Zděděno <xref:System.ComponentModel.MarshalByValueComponent>z.|  
  
> [!NOTE]
> Většina operací, které přidávají nebo odstraňují řádky, `ColumnChanged` nevyvolají události a `ColumnChanging` . `ColumnChanged` `ColumnChanging` `DiffGram`Metoda však vyvolá události `DiffGram` `Auto` a, pokud není nastavena na nebo je nastavena na hodnotu, když je dokument XML čten. `XmlReadMode` `ReadXml`  
  
> [!WARNING]
> Poškození dat může nastat, pokud jsou změněna data v `DataSet` , z `RowChanged` nichž je událost vyvolána. Pokud dojde k poškození dat, nebude vyvolána žádná výjimka.  
  
## <a name="additional-related-events"></a>Další související události  
 <xref:System.Data.DataTable.Constraints%2A> Vlastnost<xref:System.Data.ConstraintCollection> obsahuje instanci. <xref:System.Data.ConstraintCollection> Třída zpřístupňuje událost. <xref:System.Data.ConstraintCollection.CollectionChanged> Tato událost se aktivuje při přidání, úpravě nebo odebrání omezení z `ConstraintCollection`.  
  
 <xref:System.Data.DataTable.Columns%2A> Vlastnost<xref:System.Data.DataColumnCollection> obsahuje instanci. `DataColumnCollection` Třída zpřístupňuje událost. <xref:System.Data.DataColumnCollection.CollectionChanged> Tato událost je aktivována, `DataColumn` když dojde k přidání, změně nebo odebrání `DataColumnCollection`z. Úpravy, které způsobují, že událost vyvolá změny, obsahují změny názvu, typu, výrazu nebo pořadí sloupce.  
  
 <xref:System.Data.DataSet.Tables%2A> Vlastnost<xref:System.Data.DataSet> obsahuje instanci<xref:System.Data.DataTableCollection> . Třída zpřístupňuje `CollectionChanged` a a `CollectionChanging` událost. `DataTableCollection` Tyto události `DataTable` se aktivují, když dojde k přidání nebo odebrání `DataSet`z.  
  
 Změny, `DataRows` které mohou také aktivovat události pro související <xref:System.Data.DataView>. `DataView` Třída zveřejňuje`DataColumn` událost, která se aktivuje, když se změní hodnota nebo když se změní kompozice nebo pořadí řazení zobrazení. <xref:System.Data.DataView.ListChanged> Třída zveřejňuje událost, která se aktivuje, `DataColumn` když se změní přidružená hodnota. <xref:System.Data.DataRowView.PropertyChanged> <xref:System.Data.DataRowView>  
  
## <a name="sequence-of-operations"></a>Posloupnost operací  
 Zde je posloupnost operací, ke kterým dochází při `DataRow` přidání, úpravě nebo odstranění:  
  
1. Vytvoří navržený záznam a použije změny.  
  
2. Ověřte omezení pro sloupce bez výrazu.  
  
3. Vyvolejte události `RowDeleting`nebopodle potřeby. `RowChanging`  
  
4. Nastavte navrhovaný záznam jako aktuální záznam.  
  
5. Aktualizujte všechny přidružené indexy.  
  
6. Vyvolat `ListChanged` události pro přidružené `DataView` objekty a `PropertyChanged` události pro přidružené `DataRowView` objekty.  
  
7. Vyhodnotit všechny sloupce výrazu, ale odložit kontrolu omezení pro tyto sloupce.  
  
8. Vyvolat `ListChanged` události pro přidružené `DataView` objekty a `PropertyChanged` události pro přidružené `DataRowView` objekty ovlivněné hodnoceními sloupce výrazu.  
  
9. Vyvolat `RowChanged` události `RowDeleted` nebo podle potřeby.  
  
10. Kontroluje omezení pro sloupce výrazu.  
  
> [!NOTE]
> Změny sloupců výrazů nikdy nevyvolávají `DataTable` události. Změny ve sloupcích výrazu jsou pouze `DataView` vyvolání `DataRowView` a události. Sloupce výrazů mohou mít závislosti na více dalších sloupcích a lze je vyhodnotit několikrát během jedné `DataRow` operace. Každé vyhodnocení výrazu vyvolá události a jediná `DataRow` operace může vyvolat vícenásobné `ListChanged` události a `PropertyChanged` , pokud jsou ovlivněny sloupce výrazu, případně včetně více událostí pro stejný sloupec výrazu.  
  
> [!WARNING]
> <xref:System.NullReferenceException> Nevolejte`RowChanged` v rámci obslužné rutiny události. Pokud je vyvolána `RowChanged` v rámci události a `DataTable`, pak `DataTable` bude poškozen. <xref:System.NullReferenceException>  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit obslužné rutiny událostí pro `RowChanged`události `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, a `TableClearing` . Každá obslužná rutina události zobrazuje výstup v okně konzoly při jeho vyvolání.  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Manipulace s daty v datové tabulce](manipulating-data-in-a-datatable.md)
- [Zpracování událostí adaptéru dat](../handling-dataadapter-events.md)
- [Zpracování událostí datové sady](handling-dataset-events.md)
- [Přehled ADO.NET](../ado-net-overview.md)
