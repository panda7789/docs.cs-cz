---
title: Generování příkazů s CommandBuilders
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: 7cc8ff5391fca7c3315dda433785a182f476bca7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783873"
---
# <a name="generating-commands-with-commandbuilders"></a>Generování příkazů s CommandBuilders
Pokud je `InsertCommand` `UpdateCommand` `DeleteCommand` vlastnost dynamicky určena v době běhu, například prostřednictvím dotazovacího nástroje, který přebírá textový příkaz od uživatele, možná nebudete moci určit příslušné, nebo v době návrhu. `SelectCommand` Pokud vaše <xref:System.Data.DataTable> mapy nebo jsou vygenerovány z jedné tabulky databáze, můžete využít výhod `UpdateCommand` <xref:System.Data.Common.DbCommandBuilder> `DeleteCommand`objektu pro automatické generování, `InsertCommand`, a <xref:System.Data.Common.DbDataAdapter>.  
  
 Minimální požadavek vyžaduje, abyste `SelectCommand` vlastnost nastavili tak, aby fungovala automatická generace příkazů. Schéma tabulky načtené `SelectCommand` vlastností Určuje syntaxi automaticky generovaných příkazů INSERT, Update a DELETE.  
  
 Aby bylo možné vracet `SelectCommand` metadata potřebná k vytváření příkazů INSERT, Update a Delete SQL, musíbýtspuštěná.<xref:System.Data.Common.DbCommandBuilder> V důsledku toho je potřeba dodatečnou cestu ke zdroji dat a to může bránit ve výkonu. Chcete-li dosáhnout optimálního výkonu, zadejte příkazy explicitně namísto použití <xref:System.Data.Common.DbCommandBuilder>.  
  
 `SelectCommand` Musí taky vracet aspoň jeden primární klíč nebo jedinečný sloupec. Pokud žádný není, `InvalidOperation` je vygenerována výjimka a příkazy nejsou vygenerovány.  
  
 Při přidružení k a `DataAdapter` <xref:System.Data.Common.DbCommandBuilder> automaticky generuje `InsertCommand`vlastnosti `UpdateCommand` `DeleteCommand`,a , Pokudjsouodkazyshodnotounull.`DataAdapter` Pokud již pro vlastnost existuje, je použita stávající `Command`. `Command`  
  
 Databázová zobrazení, která jsou vytvořena spojením dvou nebo více tabulek, se nepovažují za jednu databázovou tabulku. V této instanci nemůžete použít <xref:System.Data.Common.DbCommandBuilder> k automatickému generování příkazů. musíte explicitně zadat příkazy. Informace o explicitním nastavení příkazů pro řešení aktualizací `DataSet` zpět do zdroje dat najdete v tématu [aktualizace zdrojů dat pomocí datových adaptérů](updating-data-sources-with-dataadapters.md).  
  
 Můžete chtít mapovat výstupní parametry zpět na aktualizovaný řádek `DataSet`. Jedna společná úloha by načítají hodnotu automaticky generovaného pole identity nebo časového razítka ze zdroje dat. Ve výchozím nastavení nebudou namapovány výstupní parametry na sloupce v aktualizovaném řádku. <xref:System.Data.Common.DbCommandBuilder> V této instanci musíte explicitně zadat příkaz. Příklad mapování automaticky generovaného pole identity zpět na sloupec vloženého řádku naleznete v tématu [načítání identity nebo hodnot AutoNumber](retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Pravidla pro automaticky generované příkazy  
 Následující tabulka uvádí pravidla, jak se generují automaticky generované příkazy.  
  
|Příkaz|Pravidlo|  
|-------------|----------|  
|`InsertCommand`|Vloží řádek ve zdroji dat pro všechny řádky v tabulce s <xref:System.Data.DataRow.RowState%2A>. <xref:System.Data.DataRowState.Added> Vloží hodnoty pro všechny sloupce, které jsou aktualizovatelné (ale ne sloupce, jako jsou identity, výrazy nebo časová razítka).|  
|`UpdateCommand`|Aktualizuje řádky ve zdroji dat pro všechny řádky v tabulce s `RowState`. <xref:System.Data.DataRowState.Modified> Aktualizuje hodnoty všech sloupců kromě sloupců, které nejsou aktualizovatelné, jako jsou identity nebo výrazy. Aktualizuje všechny řádky, ve kterých se hodnoty sloupce ve zdroji dat shodují s hodnotami sloupce primárního klíče řádku a kde zbývající sloupce ve zdroji dat odpovídají původním hodnotám řádku. Další informace najdete v části "optimistické modely souběžnosti pro aktualizace a odstraňování" dále v tomto tématu.|  
|`DeleteCommand`|Odstraní řádky ve zdroji dat pro všechny řádky v tabulce s `RowState`. <xref:System.Data.DataRowState.Deleted> Odstraní všechny řádky, ve kterých se hodnoty sloupců shodují s hodnotami sloupce primárního klíče řádku a kde zbývající sloupce ve zdroji dat odpovídají původním hodnotám řádku. Další informace najdete v části "optimistické modely souběžnosti pro aktualizace a odstraňování" dále v tomto tématu.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Optimistický model souběžnosti pro aktualizace a odstranění  
 Logika pro automatické generování příkazů pro příkazy UPDATE a DELETE je založena na *optimistické souběžnosti*– to znamená, že záznamy nejsou zamčeny pro úpravy a mohou být upravovány jinými uživateli nebo procesy kdykoli. Vzhledem k tomu, že záznam mohl být změněn po jeho vrácení z příkazu SELECT, ale před vydáním příkazu UPDATE nebo DELETE obsahuje příkaz automaticky generovaný UPDATE nebo DELETE klauzuli WHERE, která určuje, že řádek je aktualizován pouze v případě, že je obsahuje všechny původní hodnoty a nebyl odstraněn ze zdroje dat. To se provádí, aby se předešlo přepsání nových dat. Když se automaticky vygenerovaná aktualizace pokusí aktualizovat řádek, který byl odstraněn nebo který neobsahuje původní hodnoty nalezené v <xref:System.Data.DataSet>, příkaz nemá vliv na žádné záznamy <xref:System.Data.DBConcurrencyException> a vyvolá se.  
  
 Pokud chcete aktualizaci nebo odstranění dokončit bez ohledu na původní hodnoty, je nutné explicitně nastavit `UpdateCommand` `DataAdapter` pro a nespoléhat na automatické generování příkazů.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Omezení pro automatickou logiku generování příkazů  
 Následující omezení se vztahují na automatické generování příkazů.  
  
### <a name="unrelated-tables-only"></a>Pouze nesouvisející tabulky  
 Logika automatické generace příkazů generuje příkazy INSERT, UPDATE nebo DELETE pro samostatné tabulky, aniž by bylo nutné brát v úvahu žádné vztahy k ostatním tabulkám ve zdroji dat. V důsledku toho může dojít k selhání při volání `Update` k odeslání změn pro sloupec, který se účastní omezení cizího klíče v databázi. Chcete-li se této výjimce vyhnout, <xref:System.Data.Common.DbCommandBuilder> nepoužívejte příkaz pro aktualizaci sloupců obsažených v omezení cizího klíče. místo toho explicitně zadejte příkazy používané k provedení operace.  
  
### <a name="table-and-column-names"></a>Názvy tabulek a sloupců  
 Pokud názvy sloupců nebo názvy tabulek obsahují jakékoli speciální znaky, například mezery, tečky, uvozovky nebo jiné nealfanumerické znaky, může být logika automatického generování příkazů neúspěšná, a to i v případě, že jsou oddělené závorkami. V závislosti na poskytovateli může nastavení parametrů QuotePrefix a QuoteSuffix umožňovat, aby logika generování mohla zpracovávat mezery, ale nemůže uniknout speciální znaky. Plně kvalifikované názvy tabulek ve formátu *Catalog. Schema. Table* jsou podporovány.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Automatické generování příkazu SQL pomocí CommandBuilder  
 Chcete-li automaticky generovat příkazy SQL `DataAdapter`pro, nejprve `SelectCommand` nastavte `DataAdapter`vlastnost `CommandBuilder` `CommandBuilder` objektu, poté vytvořte objekt a jako argument, `DataAdapter` pro který bude automaticky nastavena, zadejte jako argument. Vygenerujte příkazy SQL.  
  
```vb  
' Assumes that connection is a valid SqlConnection object   
' inside of a Using block.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", connection)  
Dim builder As SqlCommandBuilder = New SqlCommandBuilder(adapter)  
builder.QuotePrefix = "["  
builder.QuoteSuffix = "]"  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object  
// inside of a using block.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", connection);  
SqlCommandBuilder builder = new SqlCommandBuilder(adapter);  
builder.QuotePrefix = "[";  
builder.QuoteSuffix = "]";  
```  
  
## <a name="modifying-the-selectcommand"></a>Úprava vlastnosti SelectCommand  
 `CommandText` Změníte`SelectCommand` -li příkazy po automatickém vygenerování příkazů INSERT, Update nebo DELETE, může dojít k výjimce. Pokud změněný `SelectCommand.CommandText` obsahuje informace o schématu, které nejsou konzistentní `SelectCommand.CommandText` s použitým při automatickém vygenerování příkazů INSERT, Update nebo DELETE `DataAdapter.Update` , budoucí volání metody se mohou pokusit získat přístup ke sloupcům, které již neexistuje v aktuální tabulce `SelectCommand`, na kterou odkazuje, a bude vyvolána výjimka.  
  
 Můžete aktualizovat informace o schématu používané v `CommandBuilder` pro automatické generování příkazů `RefreshSchema` voláním metody `CommandBuilder`.  
  
 Chcete-li zjistit, který příkaz byl automaticky vygenerován, můžete získat odkaz na automaticky generované `GetInsertCommand`příkazy pomocí metod `CommandBuilder` , `GetUpdateCommand`a `GetDeleteCommand` objektu a zaškrtnutím `CommandText`vlastnost přidruženého příkazu  
  
 Následující příklad kódu zapisuje do konzoly příkaz k aktualizaci, který byl automaticky vygenerován.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 V následujícím příkladu se znovu vytvoří `Customers` tabulka `custDS` v datové sadě. Volá se metoda **RefreshSchema** , která obnoví automaticky generované příkazy s informacemi o tomto novém sloupci.  
  
```vb  
' Assumes an open SqlConnection and SqlDataAdapter inside of a Using block.  
adapter.SelectCommand.CommandText = _  
  "SELECT CustomerID, ContactName FROM dbo.Customers"  
builder.RefreshSchema()  
  
custDS.Tables.Remove(custDS.Tables("Customers"))  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
// Assumes an open SqlConnection and SqlDataAdapter inside of a using block.  
adapter.SelectCommand.CommandText =   
  "SELECT CustomerID, ContactName FROM dbo.Customers";  
builder.RefreshSchema();  
  
custDS.Tables.Remove(custDS.Tables["Customers"]);  
adapter.Fill(custDS, "Customers");  
```  
  
## <a name="see-also"></a>Viz také:

- [Příkazy a parametry](commands-and-parameters.md)
- [Spuštění příkazu](executing-a-command.md)
- [DbConnection, DbCommand a DbException](dbconnection-dbcommand-and-dbexception.md)
- [Přehled ADO.NET](ado-net-overview.md)
