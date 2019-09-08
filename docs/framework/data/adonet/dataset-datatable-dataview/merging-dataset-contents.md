---
title: Slučování obsahu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
ms.openlocfilehash: abc9183666602a7ef369e690e3ae499f8c7b8b11
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784395"
---
# <a name="merging-dataset-contents"></a>Slučování obsahu datové sady

Můžete použít <xref:System.Data.DataSet.Merge%2A> metodu pro sloučení obsahu <xref:System.Data.DataSet>, <xref:System.Data.DataTable>nebo <xref:System.Data.DataRow> pole do existující `DataSet`. Několik faktorů a možností má vliv na to, jak se nová data `DataSet`sloučí do existující.

## <a name="primary-keys"></a>Primární klíče

Pokud tabulka přijímající nová data a schéma ze sloučení má primární klíč, budou nové řádky z příchozích dat spárovány se stávajícími řádky, které mají stejné <xref:System.Data.DataRowVersion.Original> hodnoty primárního klíče jako v příchozích datech. Pokud se sloupce z příchozího schématu shodují s hodnotami stávajícího schématu, data ve stávajících řádcích se upraví. Sloupce, které neodpovídají existujícímu schématu, se buď ignorují, nebo přidají na základě <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> parametru. Nové řádky s hodnotami primárního klíče, které se neshodují s žádnými existujícími řádky, se připojí k existující tabulce.

Pokud příchozí nebo existující řádky mají <xref:System.Data.DataRowState.Added>stav řádku, jsou jejich primární hodnoty porovnány <xref:System.Data.DataRowVersion.Current> pomocí hodnoty `Added` primárního klíče řádku, protože neexistuje žádná `Original` verze řádku.

Pokud příchozí tabulka a stávající tabulka obsahují sloupec se stejným názvem, ale s různými datovými typy, je vyvolána výjimka a <xref:System.Data.DataSet.MergeFailed> událost `DataSet` je vyvolána. Pokud má v příchozí tabulce a existující tabulce definované klíče, ale primární klíče jsou pro různé sloupce, je vyvolána výjimka a `MergeFailed` událost `DataSet` je vyvolána.

Pokud tabulka přijímající nová data ze sloučení nemá primární klíč, nové řádky z příchozích dat nelze spárovat s existujícími řádky v tabulce a jsou místo toho připojeny k existující tabulce.

## <a name="table-names-and-namespaces"></a>Názvy tabulek a obory názvů

<xref:System.Data.DataTable>objektům lze volitelně přiřadit <xref:System.Data.DataTable.Namespace%2A> hodnotu vlastnosti. Při <xref:System.Data.DataTable.Namespace%2A> přiřazení <xref:System.Data.DataTable> <xref:System.Data.DataTable.TableName%2A> hodnot může obsahovat více objektů se stejnou hodnotou. <xref:System.Data.DataSet> Během slučovacích operací <xref:System.Data.DataTable.TableName%2A> a <xref:System.Data.DataTable.Namespace%2A> slouží k identifikaci cíle sloučení. Pokud není přiřazeno, použije se k <xref:System.Data.DataTable.TableName%2A> identifikaci cíle sloučení jenom. <xref:System.Data.DataTable.Namespace%2A>

> [!NOTE]
> Toto chování se změnilo ve verzi 2,0 .NET Framework. Ve verzi 1,1 byly podporovány obory názvů, ale byly ignorovány během slučovacích operací. Z <xref:System.Data.DataSet> tohoto důvodu bude mít použití <xref:System.Data.DataTable.Namespace%2A> hodnot vlastností různé chování v závislosti na tom, kterou verzi .NET Framework používáte. Předpokládejme například, že máte `DataSets` dvě obsahující `DataTables` stejné <xref:System.Data.DataTable.TableName%2A> hodnoty vlastností, ale jiné <xref:System.Data.DataTable.Namespace%2A> hodnoty vlastností. Ve verzi 1,1 .NET Framework budou při slučování těchto dvou <xref:System.Data.DataTable.Namespace%2A> <xref:System.Data.DataSet> objektů ignorovány různé názvy. Počínaje verzí 2,0 ale sloučení způsobí, že se v cíli `DataTables` <xref:System.Data.DataSet>vytvoří dva nové. Původní `DataTables` akce sloučení nebude ovlivněna.

## <a name="preservechanges"></a>PreserveChanges

Pokud předáte `DataSet`do `DataTable` metodypole`Merge` , `DataRow` nebo, můžete zahrnout volitelné parametry, které určují, zda se mají zachovat změny v existujících `DataSet`a jak zpracovat nové prvky schématu, které byly nalezeny v příchozích datech. První z těchto parametrů po příchozích datech je logický příznak, <xref:System.Data.LoadOption.PreserveChanges>který určuje, jestli se mají změny v existujícím `DataSet`případě zachovat. Pokud je `true`příznak nastaven na hodnotu, příchozí hodnoty `Current` nepřepisují existující hodnoty v existujícím řádku ve verzi. `PreserveChanges` Pokud je `false`příznak nastaven na hodnotu, příchozí hodnoty přepíší existující hodnoty v existujícím `Current` řádku ve verzi. `PreserveChanges` Pokud příznak není zadán, je `false` nastaven jako výchozí. `PreserveChanges` Další informace o verzích řádků najdete v tématu [stavy řádků a verze řádků](row-states-and-row-versions.md).

`PreserveChanges` <xref:System.Data.DataRowVersion.Current> <xref:System.Data.DataRowVersion.Original> `Original` V takovém případě jsou data z existujícího řádku udržována ve verzi řádku stávajícího řádku, zatímco data z verze stávajícího řádku jsou přepsána daty z řádku `true` verze příchozího řádku Existující řádek je nastaven na <xref:System.Data.DataRowState.Modified>hodnotu. <xref:System.Data.DataRow.RowState%2A> Platí následující výjimky:

- Pokud existující `RowState` řádek má `Deleted`, `RowState` `Modified`zůstává `Deleted` a není nastaven na. V takovém případě se data z příchozího řádku budou `Original` ukládat i ve verzi řádku existujícího řádku, `Original` která přepíše verzi stávajícího řádku (Pokud `Added`vstupní řádek neobsahuje `RowState` ).

- Pokud `RowState` má vstupní řádek hodnotu `Added` `Original` , data z verze stávajícího řádku nebudou přepsána daty z příchozího řádku, `Original` protože příchozí řádek neobsahuje verzi řádku.

`PreserveChanges` `RowState` V případě `RowState` , verze řádku a`Original`ve stávajícím řádku jsou přepsány daty z příchozího řádku a stávající řádek je nastaven na vstupní řádek. `Current` `false` Platí následující výjimky:

- Pokud `RowState` má vstupní řádek `Unchanged` a a `Deleted` `Added` `Modified`stávající řádek má `RowState` , nebo ,`RowState` je existující řádek nastaven na hodnotu. `Modified`

- `RowState` Pokud má `Modified` `RowState` `RowState` `Modified`vstupní řádek a a `Deleted`stávající řádek má ,,nebo,jeexistujícířádeknastavennahodnotu.`Unchanged` `Added` Také data z `Original` verze stávajícího řádku nejsou přepsána daty z příchozího řádku, protože příchozí řádek `Original` neobsahuje verzi řádku.

## <a name="missingschemaaction"></a>MissingSchemaAction

Můžete použít volitelný <xref:System.Data.MissingSchemaAction> parametr `Merge` metody k určení, jak `Merge` bude zpracovávat prvky schématu v příchozích datech, které nejsou součástí existující `DataSet`.

Následující tabulka popisuje možnosti pro `MissingSchemaAction`.

|MissingSchemaAction – možnost|Popis|
|--------------------------------|-----------------|
|<xref:System.Data.MissingSchemaAction.Add>|Přidejte nové informace o schématu do `DataSet` a naplňte nové sloupce vstupními hodnotami. Toto nastavení je výchozí.|
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Přidejte informace o novém schématu a primárním klíči do `DataSet` a naplňte nové sloupce vstupními hodnotami.|
|<xref:System.Data.MissingSchemaAction.Error>|Vyvolejte výjimku, pokud se zjistily neshodné informace o schématu.|
|<xref:System.Data.MissingSchemaAction.Ignore>|Ignorujte nové informace o schématu.|

## <a name="constraints"></a>Omezení

U metody nejsou kontrolována omezení, dokud nebudou do stávajících `DataSet`dat přidána všechna nová data. `Merge` Po přidání dat jsou omezení uplatněna na aktuální hodnoty v `DataSet`. Je nutné zajistit, že váš kód zpracovává všechny výjimky, které mohou být vyvolány z důvodu porušení omezení.

Vezměte v úvahu případ, kdy existující řádek v `DataSet` `Unchanged` je řádek s hodnotou primárního klíče 1. Během `Modified` operace sloučení se vstupním řádkem `Original` s `Current` hodnotou primárního klíče na hodnotě 2 a hodnotou primárního klíče 1 se existující řádek a `Original` vstupní řádek nepovažují za shodu, protože hodnoty primárního klíče jednotlivých. Když je však dokončeno sloučení a jsou kontrolována omezení, bude vyvolána výjimka, protože `Current` hodnoty primárního klíče narušují omezení UNIQUE pro sloupec primárního klíče.

> [!NOTE]
> Když jsou řádky vloženy do tabulky databáze obsahující automatické zvyšování sloupce, jako je například sloupec identity, hodnota sloupce identity vrácená vložením nesmí odpovídat hodnotě v `DataSet`objektu, což způsobí, že vracené řádky budou namísto sloučení sloučeny. Další informace najdete v tématu [načtení hodnot identity nebo hodnot typu AutoNumber](../retrieving-identity-or-autonumber-values.md).

Následující příklad kódu sloučí dva `DataSet` objekty s různými schématy do jednoho `DataSet` s kombinovanými schématy dvou příchozích `DataSet` objektů.

[!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]

Následující příklad kódu používá existující `DataSet` s aktualizacemi a předá tyto aktualizace `DataAdapter` ke zpracování ve zdroji dat. Výsledky se pak sloučí do původní `DataSet`. Po zamítnutí změn, které vedly k chybě, se sloučené změny potvrdí pomocí `AcceptChanges`.

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#1)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#1)]

[!code-csharp[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/CS/source.cs#2)]
[!code-vb[DataWorks DataSet.MergeAcceptChanges#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.MergeAcceptChanges/VB/source.vb#2)]

## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Stavy řádků a verze řádků](row-states-and-row-versions.md)
- [Adaptéry a čtečky dat](../dataadapters-and-datareaders.md)
- [Načítání a úpravy dat v ADO.NET](../retrieving-and-modifying-data.md)
- [Načítání hodnot identity nebo automatického číslování](../retrieving-identity-or-autonumber-values.md)
- [Přehled ADO.NET](../ado-net-overview.md)
