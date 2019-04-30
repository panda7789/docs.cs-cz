---
title: Generování příkazů s CommandBuilders
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: 42463249a6636e625729f90fc31fa7589ef7ef74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878784"
---
# <a name="generating-commands-with-commandbuilders"></a>Generování příkazů s CommandBuilders
Když `SelectCommand` vlastnost dynamicky určena v době běhu, jako je přes nástroj pro dotaz, který přijímá textový příkaz od uživatele, nemusí být schopen zadejte odpovídající `InsertCommand`, `UpdateCommand`, nebo `DeleteCommand` v době návrhu. Pokud vaše <xref:System.Data.DataTable> mapuje nebo je generován z jedné tabulky databáze, které můžete využít <xref:System.Data.Common.DbCommandBuilder> objektu automaticky generuje `DeleteCommand`, `InsertCommand`, a `UpdateCommand` z <xref:System.Data.Common.DbDataAdapter>.  
  
 Jako minimální požadavek, je nutné nastavit `SelectCommand` vlastnost, aby pro příkaz Automatické generování pracovat. Načte schéma tabulky `SelectCommand` vlastnost určuje syntaxi automaticky generované příkazy INSERT, UPDATE a DELETE.  
  
 <xref:System.Data.Common.DbCommandBuilder> Musí být spuštěn `SelectCommand` cílem vrátit metadata potřebná k sestavení příkazů INSERT, UPDATE a DELETE SQL. V důsledku toho navíc cesty ke zdroji dat je nezbytné, a to může bránit výkonu. Pro zajištění optimálního výkonu, explicitně určete příkazům spíš než <xref:System.Data.Common.DbCommandBuilder>.  
  
 `SelectCommand` Musí také vracet alespoň jednu primární klíč nebo jedinečné sloupce. Pokud nejsou k dispozici, `InvalidOperation` vygenerována výjimka, a příkazy nejsou vygenerovány.  
  
 Při přidružené `DataAdapter`, <xref:System.Data.Common.DbCommandBuilder> automaticky generuje `InsertCommand`, `UpdateCommand`, a `DeleteCommand` vlastnosti `DataAdapter` případě, že jsou odkazy s hodnotou null. Pokud `Command` již existuje vlastnost existující `Command` se používá.  
  
 Zobrazení databáze, které vytváří spojení dvou nebo více tabulek nejsou považovány za jeden databázové tabulky. V tomto případě nelze použít <xref:System.Data.Common.DbCommandBuilder> budou automaticky generovány příkazy; je nutné explicitně zadat příkazům. Informace o explicitním nastavením příkazy řešení aktualizace `DataSet` zpět do zdroje dat, naleznete v tématu [aktualizace zdroje dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Můžete chtít mapovat výstupní parametry zpátky na aktualizovaný řádek `DataSet`. Jednou z běžných úloh by být načítání hodnoty pole automaticky vygenerované identity nebo časové razítko ze zdroje dat. <xref:System.Data.Common.DbCommandBuilder> Nebude výstupní parametry mapovat na sloupce v aktualizovaný řádek ve výchozím nastavení. V tomto případě je nutné explicitně zadat svých rukou. Příklad mapování pole automaticky vygenerované identity zpět ke sloupci vloženého řádku najdete v tématu [načítání Identity nebo automatického číslování hodnoty](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Pravidla pro automaticky generovány příkazy  
 Následující tabulka ukazuje pravidla pro způsob automaticky generované, že jsou generovány příkazy.  
  
|Příkaz|Pravidlo|  
|-------------|----------|  
|`InsertCommand`|Vloží řádek ve zdroji dat pro všechny řádky v tabulce s <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Added>. Vloží hodnoty pro všechny sloupce, které jsou aktualizovatelného (ale ne sloupce identity, výrazy nebo časová razítka).|  
|`UpdateCommand`|Aktualizace řádků ve zdroji dat pro všechny řádky v tabulce s `RowState` z <xref:System.Data.DataRowState.Modified>. Aktualizuje hodnoty všechny sloupce kromě sloupce, které nejsou aktualizovatelné, jako je například identity nebo výrazy. Aktualizuje všechny řádky hodnoty sloupce ve zdroji dat shodují s hodnotami sloupec primárního klíče řádku a zbývající sloupce ve zdroji dat odpovídá původní hodnoty v řádku. Další informace najdete v tématu "Optimistického řízení souběžnosti Model pro aktualizace a odstraní," dále v tomto tématu.|  
|`DeleteCommand`|Řádků ve zdroji dat pro všechny řádky v tabulce se odstraní `RowState` z <xref:System.Data.DataRowState.Deleted>. Odstraní všechny řádky, sloupce hodnoty shodují s hodnotami sloupec primárního klíče řádku a zbývající sloupce ve zdroji dat odpovídá původní hodnoty v řádku. Další informace najdete v tématu "Optimistického řízení souběžnosti Model pro aktualizace a odstraní," dále v tomto tématu.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Model optimistického řízení souběžnosti pro aktualizace a odstranění  
 Logika pro generování příkazy automaticky pro příkazy UPDATE a DELETE je založená na *optimistického řízení souběžnosti*– to znamená, že záznamy nejsou uzamčená pro úpravy a můžete kdykoli změnit jiné uživatelé nebo procesy. Vzhledem k tomu, že záznam mohl změnit poté, co byla vrácena z příkazu SELECT, ale před vydáním příkazu UPDATE nebo DELETE, automaticky vytvořen příkaz UPDATE nebo DELETE obsahuje klauzuli WHERE, určení, že řádek jenom aktualizovat, pokud ji obsahuje všechny původní hodnoty a nebyl odstraněn z datového zdroje. To se provádí, aby nedošlo k přepsání nová data. Kde se pokusí automaticky generované aktualizace aktualizace řádku, který je odstraněný nebo, který neobsahuje původní hodnoty nalezené v <xref:System.Data.DataSet>, příkaz nemá vliv na všechny záznamy a <xref:System.Data.DBConcurrencyException> je vyvolána výjimka.  
  
 Pokud chcete, UPDATE nebo DELETE pro dokončení bez ohledu na původní hodnoty, je nutné explicitně nastavit `UpdateCommand` pro `DataAdapter` a nespoléhala se na generování automatických příkazu.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Omezení generování logiky automatické příkaz  
 Následující omezení platí pro generování automatických příkazu.  
  
### <a name="unrelated-tables-only"></a>Pouze nesouvisejících tabulek  
 Generování automatických příkaz generuje logiku vložení, aktualizace a odstranění příkazů pro samostatné tabulky bez ohledu na případné relace s jinými tabulkami ve zdroji dat. V důsledku toho může dojít k chybě při volání `Update` odesílání pro sloupec, který je součástí omezení cizího klíče v databázi. Chcete-li předejít této výjimce, nepoužívejte <xref:System.Data.Common.DbCommandBuilder> pro aktualizaci sloupce používané v omezení cizího klíče; místo toho explicitně zadat příkazy používá k provedení této operace.  
  
### <a name="table-and-column-names"></a>Názvech tabulek a sloupců  
 Příkaz Automatické generování logiky může selhat, pokud názvy sloupců nebo názvy tabulek obsahovat žádné speciální znaky, jako jsou mezery, tečky, uvozovky nebo jiné nealfanumerické znaky, i v případě, že oddělen složenými závorkami. V závislosti na poskytovateli nastavení parametrů QuotePrefix a QuoteSuffix může povolit generování logiku pro proces mezery, ale jeho nemůžou opustit speciální znaky. Plně kvalifikované názvy tabulek ve formě *catalog.schema.table* jsou podporovány.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Použití CommandBuilder automaticky vygenerovat příkaz SQL  
 Budou automaticky generovány příkazy SQL `DataAdapter`, nejdřív nastavit `SelectCommand` vlastnost `DataAdapter`, vytvořte `CommandBuilder` objektu a zadat jako argument `DataAdapter` pro kterou `CommandBuilder` automaticky vytvořit příkazy SQL.  
  
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
 Pokud změníte `CommandText` z `SelectCommand` po byly automaticky generovány příkazy INSERT, UPDATE nebo DELETE, může dojít k výjimce. Pokud upravené `SelectCommand.CommandText` obsahuje informace o schématu, které nejsou konzistentní `SelectCommand.CommandText` použít při vložení, aktualizace nebo odstranění příkazy byly automaticky vygenerovaný, budoucí volání `DataAdapter.Update` metoda může pokus o přístup k sloupce, který už existuje v aktuální tabulce odkazuje `SelectCommand`, a bude vyvolána výjimka.  
  
 Můžete aktualizovat informace o schématu používané `CommandBuilder` voláním budou automaticky generovány příkazy `RefreshSchema` metodu `CommandBuilder`.  
  
 Pokud chcete vědět, jaké příkazu byla automaticky vygenerována, lze získat odkaz na automaticky generovaný příkazy pomocí `GetInsertCommand`, `GetUpdateCommand`, a `GetDeleteCommand` metody `CommandBuilder` objekt a zkontrolujete `CommandText`vlastnost přidružený příkaz.  
  
 Následující příklad kódu zapíše do konzoly pro příkaz update, která byla automaticky vygenerována.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 Znovu vytvoří v následujícím příkladu `Customers` v tabulku `custDS` datové sady. **RefreshSchema** metoda je volána k aktualizaci automaticky generované příkazy pomocí této nové informace o sloupci.  
  
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

- [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Spuštění příkazu](../../../../docs/framework/data/adonet/executing-a-command.md)
- [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
