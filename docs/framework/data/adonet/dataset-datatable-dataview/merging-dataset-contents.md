---
title: Slučování obsahu datové sady
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e9309a-3ebb-4a9c-9d78-21c4e2bafc5b
ms.openlocfilehash: 38d716552c4a52e01ef803ce197e4d588ed562c3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872416"
---
# <a name="merging-dataset-contents"></a>Slučování obsahu datové sady
Můžete použít <xref:System.Data.DataSet.Merge%2A> metoda sloučit obsah <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow> pole do existujícího `DataSet`. Několik faktorů a možnosti ovlivnit jak nová data se sloučí do existujícího `DataSet`.  
  
## <a name="primary-keys"></a>Primární klíče  
 Pokud v tabulce přijímat nová data a schéma z sloučení nemá primární klíč, nové řádky z příchozích dat jsou porovnány s existující řádky, které mají stejný <xref:System.Data.DataRowVersion.Original> hodnoty primárního klíče jako ty v příchozích datech. Pokud sloupce z příchozího schématu odpovídají existujícím schématu, se mění data v existující řádky. Sloupce, které se neshodují s existujícím schématu jsou ignorována nebo přidávat na základě <xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> parametru. Nové řádky s hodnoty primárního klíče, které se neshodují žádné existující řádky jsou připojena k existující tabulce.  
  
 Pokud příchozí nebo existující řádky mají stav řádku <xref:System.Data.DataRowState.Added>, jejich hodnoty primárního klíče jsou porovnány pomocí <xref:System.Data.DataRowVersion.Current> hodnota primárního klíče `Added` řádek, protože žádné `Original` existuje verze řádku.  
  
 Pokud příchozí tabulky a existující tabulky obsahují sloupec se stejným názvem, ale různé datové typy, je vyvolána výjimka a <xref:System.Data.DataSet.MergeFailed> událost `DataSet` je vyvolána. Pokud příchozí tabulky a existující tabulku definovali klíče, ale primární klíče jsou pro různé sloupce, je vyvolána výjimka a `MergeFailed` událost `DataSet` je vyvolána.  
  
 Pokud v tabulce příjem nových dat z sloučení nemá primární klíč, nové řádky z příchozích dat nejde spárovat existující řádky v tabulce a místo toho jsou připojeny k existující tabulce.  
  
## <a name="table-names-and-namespaces"></a>Názvy tabulek a obory názvů  
 <xref:System.Data.DataTable> Volitelně je možné přiřadit objekty <xref:System.Data.DataTable.Namespace%2A> hodnotu vlastnosti. Když <xref:System.Data.DataTable.Namespace%2A> hodnoty jsou přiřazeny, <xref:System.Data.DataSet> může obsahovat více <xref:System.Data.DataTable> objektů se stejným <xref:System.Data.DataTable.TableName%2A> hodnotu. Během operace sloučení obou <xref:System.Data.DataTable.TableName%2A> a <xref:System.Data.DataTable.Namespace%2A> slouží k identifikaci cílové sloučení. Pokud ne <xref:System.Data.DataTable.Namespace%2A> byla přiřazena, pouze <xref:System.Data.DataTable.TableName%2A> se používá k identifikaci cílové sloučení.  
  
> [!NOTE]
>  Toto chování změnit ve verzi 2.0 rozhraní .NET Framework. Ve verzi 1.1 obory názvů byly podporovány, ale během operace sloučení byly ignorovány. Z tohoto důvodu <xref:System.Data.DataSet> , která používá <xref:System.Data.DataTable.Namespace%2A> hodnoty vlastností budou mít různé chování v závislosti na tom, kterou verzi rozhraní .NET Framework, kterou používáte. Předpokládejme například, že máte dva `DataSets` obsahující `DataTables` se stejným <xref:System.Data.DataTable.TableName%2A> hodnoty vlastnosti, ale odlišným <xref:System.Data.DataTable.Namespace%2A> hodnot vlastností. Ve verzi 1.1 rozhraní .NET Framework, různých <xref:System.Data.DataTable.Namespace%2A> názvy se bude ignorovat při slučování dvou <xref:System.Data.DataSet> objekty. Nicméně od verze 2.0, slučování způsobí, že dvě nové `DataTables` byly vytvořeny v cílové <xref:System.Data.DataSet>. Původní `DataTables` nebude mít sloučení.  
  
## <a name="preservechanges"></a>PreserveChanges  
 Při předání `DataSet`, `DataTable`, nebo `DataRow` pole na `Merge` metodu, můžete zahrnout volitelné parametry, které určují, jestli chcete zachovat změny v existujícím `DataSet`a způsob zpracování nových elementů schématu nalezeno v příchozích datech. První z těchto parametrů po příchozích dat je logický příznak <xref:System.Data.LoadOption.PreserveChanges>, která určuje, jestli chcete zachovat změny v existujícím `DataSet`. Pokud `PreserveChanges` příznak je nastaven na `true`, příchozí hodnoty Nepřepisovat existující hodnoty `Current` řádek verzi existující řádek. Pokud `PreserveChanges` příznak je nastaven na `false`, příchozí hodnoty přepsat existující hodnoty `Current` řádek verzi existující řádek. Pokud `PreserveChanges` příznak není zadán, je nastavena na `false` ve výchozím nastavení. Další informace o verzích řádku, naleznete v tématu [stavy řádků a verze řádků](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 Když `PreserveChanges` je `true`, data z existující řádek je udržována v <xref:System.Data.DataRowVersion.Current> řádek verzi existující řádek dat z <xref:System.Data.DataRowVersion.Original> řádek verzi existující řádek je přepsán pomocí dat z `Original` řádek verze z příchozího řádku. <xref:System.Data.DataRow.RowState%2A> Existující řádek se nastaví na <xref:System.Data.DataRowState.Modified>. Vztahují se tyto výjimky:  
  
-   Pokud stávající řádek má `RowState` z `Deleted`tento `RowState` zůstává `Deleted` a není nastavená na `Modified`. V takovém případě data z příchozího řádku stále se uloží do `Original` řádek verzi existující řádek přepsání `Original` řádek verzi existující řádek (Pokud má příchozího řádku `RowState` z `Added`).  
  
-   Pokud má příchozího řádku `RowState` z `Added`, data z `Original` řádek verzi existující řádek nedojde k přepsání s daty z příchozího řádku, protože nemá příchozího řádku `Original` verze řádku.  
  
 Když `PreserveChanges` je `false`, i `Current` a `Original` verze řádků v existující řádek jsou přepsány s daty z příchozího řádku a `RowState` existující řádek se nastaví na `RowState` z příchozího řádku. Vztahují se tyto výjimky:  
  
-   Pokud má příchozího řádku `RowState` z `Unchanged` a stávající řádek má `RowState` z `Modified`, `Deleted`, nebo `Added`, `RowState` existující řádek se nastaví na `Modified`.  
  
-   Pokud má příchozího řádku `RowState` z `Added`, a stávající řádek má `RowState` z `Unchanged`, `Modified`, nebo `Deleted`, `RowState` existující řádek se nastaví na `Modified`. Kromě toho data z `Original` řádek verzi existující řádek není přepsán pomocí dat z příchozího řádku, protože příchozího řádku nemá `Original` verze řádku.  
  
## <a name="missingschemaaction"></a>MissingSchemaAction  
 Můžete použít nepovinnou <xref:System.Data.MissingSchemaAction> parametr `Merge` metody určíte, jak `Merge` zpracuje schéma elementů v příchozí data, která nejsou součástí existující `DataSet`.  
  
 Následující tabulka popisuje možnosti pro `MissingSchemaAction`.  
  
|Možnost MissingSchemaAction|Popis|  
|--------------------------------|-----------------|  
|<xref:System.Data.MissingSchemaAction.Add>|Přidat nové informace o schématu `DataSet` a naplňte jimi nové sloupce s příchozí hodnoty. Toto nastavení je výchozí.|  
|<xref:System.Data.MissingSchemaAction.AddWithKey>|Přidat nové schéma a informacemi o primárním klíči pro `DataSet` a naplňte jimi nové sloupce s příchozí hodnoty.|  
|<xref:System.Data.MissingSchemaAction.Error>|Vyvolejte výjimku, pokud informace o neodpovídající schématu dochází.|  
|<xref:System.Data.MissingSchemaAction.Ignore>|Ignorujte nové informace o schématu.|  
  
## <a name="constraints"></a>Omezení  
 S `Merge` metody omezení nejsou zkontrolován, dokud všechna nová data je přidaný do stávající `DataSet`. Po přidání data na aktuální hodnoty v jsou vynucena omezení `DataSet`. Ujistěte se, že váš kód zpracovává všechny výjimky, které mohou být vyvolány z důvodu narušení omezení.  
  
 Představte si případ, kdy existující řádek v `DataSet` je `Unchanged` řádek s hodnotu primárního klíče 1. Během operace merge s `Modified` příchozího řádku s `Original` hodnotu primárního klíče 2 a `Current` hodnotu primárního klíče 1, stávající řádek a příchozího řádku nejsou považovány za odpovídající, protože `Original` hodnoty primárního klíče se liší. Však při dokončení sloučení a omezení jsou ověřeny, bude vyvolána výjimka vzhledem k tomu, `Current` hodnoty primárního klíče porušení omezení unique pro sloupec primárního klíče.  
  
> [!NOTE]
>  Když se řádky vložily do tabulky databáze obsahující automatické zvyšování hodnoty sloupce jako je například sloupec identity, identity sloupce hodnotu vrácenou příkazem insert nemusí odpovídat hodnotě v `DataSet`, způsobí vrácené řádky, které se mají připojit místo sloučeny. Další informace najdete v tématu [načítání Identity nebo automatického číslování hodnoty](../../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
 Následující příklad kódu Sloučí dvě `DataSet` objekty se schématy differents do jedné `DataSet` kombinované schémata dvě příchozí `DataSet` objekty.  
  
 [!code-csharp[DataWorks DataSet.Merge#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/CS/source.cs#1)]
 [!code-vb[DataWorks DataSet.Merge#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataSet.Merge/VB/source.vb#1)]  
  
 Následující příklad kódu používá existující `DataSet` s aktualizacemi a předá tyto aktualizace se mají `DataAdapter` ke zpracování ve zdroji dat. Výsledky se pak sloučit do původního `DataSet`. Po zamítnutí změn, které vedly k chybě, sloučené změny jsou potvrzeny s `AcceptChanges`.  
  
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
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
