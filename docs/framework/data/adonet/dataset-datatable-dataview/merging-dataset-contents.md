---
title: "Slučování obsah datové sady"
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
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 44d171cab4099436d7daea26def831f149b75b13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="merging-dataset-contents"></a>Slučování obsah datové sady
Můžete použít <xref:System.Data.DataSet.Merge%2A> metoda sloučit obsah <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow> pole do existující `DataSet`. Několik možnosti a faktory ovlivňují jak nová data sloučí existující `DataSet`.  
  
## <a name="primary-keys"></a>Primární klíče  
 Pokud v tabulce příjem nových dat a schéma z sloučení má primární klíč, nové řádky z příchozích dat jsou přiřazeny stávající řádky, které mají stejnou <xref:System.Data.DataRowVersion.Original> primární klíč hodnoty jako v příchozí data. Pokud sloupce z příchozí schématu odpovídají existující schéma, data v existujících řádků je upravit. Sloupce, které neodpovídají žádné existující schématu jsou ignorovány nebo přidány na základě <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> parametr. Nové záznamy s hodnotami primárního klíče, které neodpovídají žádné existující řádky jsou připojena k existující tabulce.  
  
 Pokud příchozí nebo stávající řádky mají stavu řádek <xref:System.Data.DataRowState.Added>, jejich hodnot primárního klíče se splní použitím <xref:System.Data.DataRowVersion.Current> hodnota primárního klíče `Added` řádek, protože žádné `Original` verze řádku existuje.  
  
 Pokud příchozí tabulky a existující tabulky obsahují sloupec se stejným názvem, ale s různými datovými typy, je vyvolána výjimka a <xref:System.Data.DataSet.MergeFailed> události `DataSet` je vyvolána. Pokud příchozí tabulky a existující tabulky definovaly klíče, ale primární klíče, které jsou pro různé sloupce, je vyvolána výjimka a `MergeFailed` události `DataSet` je vyvolána.  
  
 Pokud v tabulce přijímá nová data od sloučení nemá primární klíč, nové řádky z příchozích dat nelze namapovat na existující řádky v tabulce a místo toho se připojí k existující tabulce.  
  
## <a name="table-names-and-namespaces"></a>Názvy tabulek a obory názvů  
 <xref:System.Data.DataTable>objekty lze volitelně přiřadit <xref:System.Data.DataTable.Namespace%2A> hodnotu vlastnosti. Když <xref:System.Data.DataTable.Namespace%2A> přiřazené hodnoty, <xref:System.Data.DataSet> může obsahovat více <xref:System.Data.DataTable> objektů se stejným <xref:System.Data.DataTable.TableName%2A> hodnotu. Během operace sloučení obě <xref:System.Data.DataTable.TableName%2A> a <xref:System.Data.DataTable.Namespace%2A> slouží k identifikaci cílové sloučení. Pokud žádné <xref:System.Data.DataTable.Namespace%2A> byl přiřazen, jenom <xref:System.Data.DataTable.TableName%2A> se používá k identifikaci cílové sloučení.  
  
> [!NOTE]
>  Toto chování změnit v rozhraní .NET Framework verze 2.0. Obory názvů v verze 1.1, byly podporovány ale během operace sloučení byly ignorovány. Z tohoto důvodu <xref:System.Data.DataSet> používající <xref:System.Data.DataTable.Namespace%2A> hodnoty vlastností bude mít různé chování v závislosti na tom, kterou verzi rozhraní .NET Framework, kterou používáte. Předpokládejme například, máte dva `DataSets` obsahující `DataTables` se stejným <xref:System.Data.DataTable.TableName%2A> hodnoty vlastnosti, ale odlišným <xref:System.Data.DataTable.Namespace%2A> hodnot vlastností. V rozhraní .NET Framework různé verze 1.1 <xref:System.Data.DataTable.Namespace%2A> názvy budou ignorovány, při sloučení dvou <xref:System.Data.DataSet> objekty. Však od verze 2.0, slučování příčiny dva nové `DataTables` mají být vytvořeny v cílové <xref:System.Data.DataSet>. Původní `DataTables` bude mít vliv na sloučení.  
  
## <a name="preservechanges"></a>PreserveChanges  
 Pokud předáte `DataSet`, `DataTable`, nebo `DataRow` pole na `Merge` metodu, můžete zahrnout volitelné parametry, které určují, zda chcete zachovat změny v existující `DataSet`a jak zpracovat nové prvky schématu nalezen v příchozí data. První z těchto parametrů po příchozích dat je logický příznak <xref:System.Data.LoadOption.PreserveChanges>, která určuje, zda chcete zachovat změny v existující `DataSet`. Pokud `PreserveChanges` je příznak nastaven na `true`, hodnoty příchozích Nepřepisovat stávající hodnoty v `Current` řádek verzi stávající řádek. Pokud `PreserveChanges` je příznak nastaven na `false`, hodnoty příchozích přepsat existující hodnoty `Current` řádek verzi stávající řádek. Pokud `PreserveChanges` příznak není zadán, je nastaven na hodnotu `false` ve výchozím nastavení. Další informace o verzích řádek najdete v tématu [stavy řádků a verze řádku](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Při `PreserveChanges` je `true`, data z existující řádek se udržuje v <xref:System.Data.DataRowVersion.Current> verze řádku existující řádku při data z <xref:System.Data.DataRowVersion.Original> řádek verzi stávající řádek se přepíše daty z `Original` řádek verze příchozí řádku. <xref:System.Data.DataRow.RowState%2A> Existující řádku je nastaven na <xref:System.Data.DataRowState.Modified>. Se vztahují tyto výjimky:  
  
-   Pokud stávající řádek má `RowState` z `Deleted`tento `RowState` zůstává `Deleted` a není nastavený na `Modified`. V takovém případě data z příchozí řádek stále se uloží v `Original` řádek verzi stávající řádek přepsal `Original` řádek verzi stávající řádek (Pokud má příchozí řádek `RowState` z `Added`).  
  
-   Pokud má příchozí řádek `RowState` z `Added`, data z `Original` řádek verzi stávající řádek nedojde k přepsání s daty z příchozí řádek, protože příchozí řádek nemá `Original` verze řádku.  
  
 Při `PreserveChanges` je `false`, i `Current` a `Original` budou přepsána verze řádek ve stávající řádek s daty z příchozí řádku a `RowState` existující řádku je nastaven na `RowState` příchozí řádku. Se vztahují tyto výjimky:  
  
-   Pokud má příchozí řádek `RowState` z `Unchanged` a stávající řádek má `RowState` z `Modified`, `Deleted`, nebo `Added`, `RowState` existující řádku je nastaven na `Modified`.  
  
-   Pokud má příchozí řádek `RowState` z `Added`, a stávající řádek má `RowState` z `Unchanged`, `Modified`, nebo `Deleted`, `RowState` existující řádku je nastaven na `Modified`. Také data z `Original` řádek verzi stávající řádek není přepsán pomocí dat z příchozí řádek, protože příchozí řádek nemá `Original` verze řádku.  
  
## <a name="missingschemaaction"></a>MissingSchemaAction  
 Můžete použít nepovinný <xref:System.Data.MissingSchemaAction> parametr `Merge` metody určíte, jak `Merge` zpracuje elementů schématu v příchozích dat, které nejsou součástí existující `DataSet`.  
  
 Následující tabulka popisuje možnosti `MissingSchemaAction`.  
  
|Možnost MissingSchemaAction|Popis|  
|--------------------------------|-----------------|  
|<xref:System.Data.MissingSchemaAction.Add>|Přidat nové informace o schématu pro `DataSet` a naplnit nové sloupce příchozí hodnotami. Toto nastavení je výchozí.|  
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Přidejte nové schéma a primární klíče informace, které `DataSet` a naplnit nové sloupce příchozí hodnotami.|  
|<xref:System.Data.MissingSchemaAction.Error>|Způsobí výjimku, pokud je zjištěna neshoda schématu informace.|  
|<xref:System.Data.MissingSchemaAction.Ignore>|Ignorujte nové informace o schématu.|  
  
## <a name="constraints"></a>Omezení  
 Pomocí `Merge` metody omezení nejsou zkontrolován, dokud všechny nové data byla přidána ke stávající `DataSet`. Po přidání dat, jsou na aktuální hodnoty v vynucena omezení `DataSet`. Je nutné zajistit, že váš kód zpracovává všechny výjimky, které mohou být vyvolány kvůli narušení omezení.  
  
 Představte si případ, kde stávající řádek v `DataSet` je `Unchanged` řádek s hodnotu primárního klíče 1. Během operace sloučení s `Modified` příchozí řádek s `Original` hodnotu primárního klíče 2 a `Current` hodnotu primárního klíče 1, stávající řádek a příchozí řádek nejsou považovány za shodují, protože `Original` hodnot primárního klíče lišit. Však při dokončení sloučení a omezení jsou zaškrtnutá políčka, bude vyvolána výjimka protože `Current` hodnot primárního klíče porušují jedinečné omezení pro sloupec primárního klíče.  
  
> [!NOTE]
>  Když řádky jsou vloženy do tabulky databáze obsahující zvyšování sloupec jako sloupec identity automaticky, hodnota sloupce identity vrácený úlohy insert nemusí odpovídat hodnotě v `DataSet`, způsobuje vrácený řádky, které se připojí místo sloučit. Další informace najdete v tématu [načítání Identity nebo automatické číslování hodnoty](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
 Následující příklad kódu Sloučí dvě `DataSet` objekty s differents schématy do jednoho `DataSet` s kombinované schémata dva příchozí `DataSet` objekty.  
  
 [!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]  
  
 Následující příklad kódu trvá existující `DataSet` s aktualizacemi a předává ty aktualizace `DataAdapter` mají být zpracovány ve zdroji dat. Výsledky jsou pak sloučeny do původní `DataSet`. Po odmítat změny, které vedly k chybě, jsou sloučené změny potvrzeny s `AcceptChanges`.  
  
 [!code-csharp[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#1)]  
  
 [!code-csharp[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#2)]
 [!code-vb[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [Adaptéry a čtečky dat](../../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Načítání a úpravy dat v ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Načítání hodnot identity nebo automatického číslování](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
