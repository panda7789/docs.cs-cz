---
title: Generování příkazů s CommandBuilders
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: 76c2a6cb0661a0e39fc3a0dd599fcbb3c046f382
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149609"
---
# <a name="generating-commands-with-commandbuilders"></a>Generování příkazů s CommandBuilders
Pokud `SelectCommand` je vlastnost dynamicky zadána za běhu, například prostřednictvím nástroje pro dotaz, který přebírá textový `InsertCommand`příkaz `UpdateCommand`od `DeleteCommand` uživatele, nemusí být možné zadat příslušnou , nebo v době návrhu. Pokud <xref:System.Data.DataTable> mapujete nebo je generována z jedné tabulky databáze, můžete využít `DeleteCommand` `InsertCommand`výhod `UpdateCommand` objektu <xref:System.Data.Common.DbDataAdapter> <xref:System.Data.Common.DbCommandBuilder> automaticky generovat , a .  
  
 Jako minimální požadavek je `SelectCommand` nutné nastavit vlastnost, aby automatické generování příkazů fungovalo. Schéma tabulky načtené `SelectCommand` vlastností určuje syntaxi automaticky generovaných příkazů INSERT, UPDATE a DELETE.  
  
 Musí <xref:System.Data.Common.DbCommandBuilder> `SelectCommand` provést, aby bylo možné vrátit metadata potřebná k vytvoření příkazů INSERT, UPDATE a DELETE SQL. V důsledku toho je nutná další cesta ke zdroji dat, což může bránit výkonu. Chcete-li dosáhnout optimálního výkonu, zadejte <xref:System.Data.Common.DbCommandBuilder>příkazy explicitně, nikoli pomocí .  
  
 Musí `SelectCommand` také vrátit alespoň jeden primární klíč nebo jedinečný sloupec. Pokud žádné nejsou `InvalidOperation` k dispozici, je generována výjimka a příkazy nejsou generovány.  
  
 Pokud jsou `DataAdapter`přidruženy <xref:System.Data.Common.DbCommandBuilder> k , `InsertCommand` `UpdateCommand`automaticky `DeleteCommand` generuje , `DataAdapter` a vlastnosti, pokud jsou nulové odkazy. Pokud `Command` již existuje pro vlastnost, `Command` existující se používá.  
  
 Zobrazení databáze, které jsou vytvořeny spojením dvou nebo více tabulek dohromady nejsou považovány za jednu databázovou tabulku. V tomto případě nelze <xref:System.Data.Common.DbCommandBuilder> použít k automatickému generování příkazů; je nutné zadat příkazy explicitně. Informace o explicitním nastavení příkazů pro `DataSet` překlad aktualizací zpět ke zdroji dat naleznete v [tématu Aktualizace zdrojů dat pomocí datových adaptérů](updating-data-sources-with-dataadapters.md).  
  
 Můžete chtít mapovat výstupní parametry zpět na `DataSet`aktualizovaný řádek . Jednou z běžných úloh by bylo načtení hodnoty automaticky generovaného pole identity nebo časového razítka ze zdroje dat. Ve <xref:System.Data.Common.DbCommandBuilder> výchozím nastavení nebude mapovat výstupní parametry na sloupce v aktualizovaném řádku. V tomto případě je nutné zadat příkaz explicitně. Příklad mapování automaticky generovaného pole identity zpět do sloupce vloženého řádku naleznete v [tématu Načítání hodnot identity nebo automatického čísla](retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Pravidla pro automaticky generované příkazy  
 V následující tabulce jsou uvedena pravidla pro generování automaticky generovaných příkazů.  
  
|Příkaz|Pravidlo|  
|-------------|----------|  
|`InsertCommand`|Vloží řádek ve zdroji dat pro všechny řádky <xref:System.Data.DataRow.RowState%2A> v <xref:System.Data.DataRowState.Added>tabulce s a . Vloží hodnoty pro všechny sloupce, které jsou aktualizovatelné (ale ne sloupce, jako jsou identity, výrazy nebo časová razítka).|  
|`UpdateCommand`|Aktualizuje řádky ve zdroji dat pro všechny `RowState` řádky <xref:System.Data.DataRowState.Modified>v tabulce pomocí aplikace a . Aktualizuje hodnoty všech sloupců s výjimkou sloupců, které nelze aktualizovat, například identity nebo výrazy. Aktualizuje všechny řádky, ve kterých hodnoty sloupců ve zdroji dat odpovídají hodnotám sloupce primárního klíče řádku a kde zbývající sloupce ve zdroji dat odpovídají původním hodnotám řádku. Další informace naleznete v tématu "Optimistický model souběžnosti pro aktualizace a odstranění", dále v tomto tématu.|  
|`DeleteCommand`|Odstraní řádky ve zdroji dat pro všechny řádky `RowState` <xref:System.Data.DataRowState.Deleted>v tabulce s a . Odstraní všechny řádky, ve kterých hodnoty sloupců odpovídají hodnotám sloupce primárního klíče řádku a kde zbývající sloupce ve zdroji dat odpovídají původním hodnotám řádku. Další informace naleznete v tématu "Optimistický model souběžnosti pro aktualizace a odstranění", dále v tomto tématu.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Optimistický model souběžnosti pro aktualizace a odstranění  
 Logika pro automatické generování příkazů pro příkazy UPDATE a DELETE je založena na *optimistické souběžnosti*-- to znamená, že záznamy nejsou uzamčeny pro úpravy a mohou být kdykoli změněny jinými uživateli nebo procesy. Vzhledem k tomu, že záznam mohl být změněn poté, co byl vrácen z příkazu SELECT, ale před vydáním příkazu UPDATE nebo DELETE, automaticky generovaný příkaz UPDATE nebo DELETE obsahuje klauzuli WHERE, která specifikuje, že řádek je aktualizován pouze v případě, že obsahuje všechny původní hodnoty a nebyl odstraněn ze zdroje dat. To se provádí, aby se zabránilo přepsání nových dat. Pokud se automaticky generovaná aktualizace pokusí aktualizovat řádek, který byl odstraněn nebo <xref:System.Data.DataSet>který neobsahuje původní hodnoty nalezené <xref:System.Data.DBConcurrencyException> v aplikaci , příkaz neovlivní žádné záznamy a je vyvolán.  
  
 Pokud chcete update nebo DELETE dokončit bez ohledu na původní `UpdateCommand` hodnoty, `DataAdapter` je nutné explicitně nastavit pro a nespoléhat na automatické generování příkazů.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Omezení logiky generování automatického příkazu  
 Následující omezení platí pro automatické generování příkazů.  
  
### <a name="unrelated-tables-only"></a>Pouze nesouvisející tabulky  
 Logika generování automatického příkazu generuje příkazy INSERT, UPDATE nebo DELETE pro samostatné tabulky bez přihlédnutí k jakýmkoli vztahům s jinými tabulkami ve zdroji dat. V důsledku toho může dojít k `Update` selhání při volání odeslat změny pro sloupec, který se účastní omezení cizího klíče v databázi. Chcete-li se této výjimce vyhnout, nepoužívejte <xref:System.Data.Common.DbCommandBuilder> pro aktualizaci sloupců zapojených do omezení cizího klíče; místo toho explicitně zadejte příkazy použité k provedení operace.  
  
### <a name="table-and-column-names"></a>Názvy tabulek a sloupců  
 Logika generování automatických příkazů může selhat, pokud názvy sloupců nebo tabulek obsahují speciální znaky, například mezery, tečky, uvozovky nebo jiné nealfanumerické znaky, i když jsou odděleny závorkami. V závislosti na zprostředkovateli nastavení QuotePrefix a QuoteSuffix parametry mohou povolit logiku generování pro zpracování mezer, ale nemůže uniknout speciální znaky. Plně kvalifikované názvy tabulek ve formě *catalog.schema.table* jsou podporovány.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Automatické generování příkazu k automatickému generování příkazu SQL  
 Chcete-li automaticky generovat `DataAdapter`příkazy `SelectCommand` SQL pro `DataAdapter`, nejprve nastavte vlastnost aplikace , pak vytvořte `CommandBuilder` objekt a určete jako argument, `DataAdapter` pro který `CommandBuilder` bude automaticky generovat příkazy SQL.  
  
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
  
## <a name="modifying-the-selectcommand"></a>Úprava příkazu SelectCommand  
 Pokud změníte `CommandText` `SelectCommand` příkazy po vložení, aktualizace nebo odstranění byly automaticky generovány, může dojít k výjimce. Pokud `SelectCommand.CommandText` změněno obsahuje informace o `SelectCommand.CommandText` schématu, které není konzistentní s použité při vložení, aktualizace nebo odstranění `DataAdapter.Update` příkazy byly automaticky generovány, budoucí volání metody `SelectCommand`může pokusit o přístup ke sloupcům, které již neexistují v aktuální tabulce odkazuje , a výjimka bude vyvolána.  
  
 Informace o schématu, které aplikace `CommandBuilder` používá k automatickému generování `RefreshSchema` příkazů, `CommandBuilder`můžete aktualizovat voláním metody .  
  
 Chcete-li vědět, jaký příkaz byl automaticky vygenerován, můžete získat odkaz na `GetInsertCommand` `GetUpdateCommand`automaticky `GetDeleteCommand` generované příkazy pomocí metody , a metody objektu `CommandBuilder` a kontrolou `CommandText` vlastnosti přidruženého příkazu.  
  
 Následující příklad kódu zapíše do konzoly příkaz aktualizace, který byl automaticky vygenerován.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 Následující příklad znovu `Customers` vytvoří tabulku `custDS` v datové sadě. **Metoda RefreshSchema** je volána k aktualizaci automaticky generovaných příkazů s tímto novým sloupcem informací.  
  
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
  
## <a name="see-also"></a>Viz také

- [Příkazy a parametry](commands-and-parameters.md)
- [Spuštění příkazu](executing-a-command.md)
- [DbConnection, DbCommand a DbException](dbconnection-dbcommand-and-dbexception.md)
- [Přehled ADO.NET](ado-net-overview.md)
