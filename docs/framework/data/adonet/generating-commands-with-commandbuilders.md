---
title: "Generování příkazů s CommandBuilders"
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
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5f250f74303fb3f2835781318e655b435e748153
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="generating-commands-with-commandbuilders"></a>Generování příkazů s CommandBuilders
Když `SelectCommand` dynamicky zadána vlastnost za běhu, například pomocí nástroje dotazu, který přebírá textový příkaz od uživatele, nemusí být možné zadat příslušné `InsertCommand`, `UpdateCommand`, nebo `DeleteCommand` v době návrhu. Pokud vaše <xref:System.Data.DataTable> mapuje nebo se vygeneruje z jedné tabulky databáze, můžete využít výhod <xref:System.Data.Common.DbCommandBuilder> objekt, který má automaticky generovat `DeleteCommand`, `InsertCommand`, a `UpdateCommand` z <xref:System.Data.Common.DbDataAdapter>.  
  
 Jako minimální požadavek, je nutné nastavit `SelectCommand` vlastnost v pořadí pro příkaz Automatické generování pracovat. Načíst schéma tabulky `SelectCommand` vlastnost určuje syntaxe automaticky generované příkazy INSERT, UPDATE a DELETE.  
  
 <xref:System.Data.Common.DbCommandBuilder> Musí být spuštěn `SelectCommand` cílem vrátit metadata potřebná k vytvoření příkazy INSERT, UPDATE a odstranit SQL. V důsledku toho je nezbytné další cesty ke zdroji dat, a to může bránit ve výkonu. K dosažení optimálního výkonu, zadejte příkazech explicitně spíše než <xref:System.Data.Common.DbCommandBuilder>.  
  
 `SelectCommand` Musí vracet také alespoň jeden primární klíč nebo jedinečné sloupec. Pokud žádný není přítomný, `InvalidOperation` se vygeneruje výjimka, a nejsou generované příkazy.  
  
 Pokud jsou přidruženy `DataAdapter`, <xref:System.Data.Common.DbCommandBuilder> automaticky vygeneruje `InsertCommand`, `UpdateCommand`, a `DeleteCommand` vlastnosti `DataAdapter` Pokud jsou odkazy s hodnotou null. Pokud `Command` již existuje pro vlastnost, existující `Command` se používá.  
  
 Zobrazení databáze, které jsou vytvořené pomocí spojení dvou nebo více tabulek nejsou považovány za jedné tabulky databáze. V této instanci nelze použít <xref:System.Data.Common.DbCommandBuilder> k automatickému generování příkazy; je nutné explicitně zadat příkazech. Informace o nastavení explicitně příkazy vyřešit aktualizací `DataSet` zpět do zdroje dat, najdete v části [aktualizace zdroje dat s DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Můžete chtít mapování výstupní parametry zpátky na aktualizovaný řádek `DataSet`. Běžných úloh by být načítání hodnotu pole automaticky generované identity nebo časové razítko z datového zdroje. <xref:System.Data.Common.DbCommandBuilder> Nebude namapovat výstupní parametry sloupce v aktualizované řádek ve výchozím nastavení. V této instanci je nutné explicitně zadat příkazu. Příklad mapování pole automaticky generované identity zpět ke sloupci vloženého řádku, naleznete v části [načítání Identity nebo automatické číslování hodnoty](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Pravidla pro automaticky generované příkazy  
 Následující tabulka uvádí pravidla pro jak automaticky vygenerovat, že jsou generovány příkazy.  
  
|Příkaz|Pravidlo|  
|-------------|----------|  
|`InsertCommand`|Vloží řádek ve zdroji dat pro všechny řádky v tabulce s <xref:System.Data.DataRow.RowState%2A> z <xref:System.Data.DataRowState.Added>. Vloží hodnoty pro všechny sloupce, které jsou v aktualizovatelné (ale ne sloupce například identit, výrazy nebo časová razítka).|  
|`UpdateCommand`|Aktualizace řádků ve zdroji dat pro všechny řádky v tabulce s `RowState` z <xref:System.Data.DataRowState.Modified>. Aktualizace hodnoty všechny sloupce kromě sloupce, které nejsou v aktualizovatelné, jako je například identity nebo výrazů. Aktualizuje všechny řádky hodnoty sloupce ve zdroji dat shodují s hodnotami sloupec primárního klíče řádku a zbývající sloupce ve zdroji dat se shodují původní hodnoty řádku. Další informace najdete v tématu "Optimistickou metodu souběžného zpracování modelu pro aktualizace a odstraní," dál v tomto tématu.|  
|`DeleteCommand`|Odstraní řádků ve zdroji dat pro všechny řádky v tabulce s `RowState` z <xref:System.Data.DataRowState.Deleted>. Odstraní všechny řádky, sloupce hodnoty shodují s hodnotami sloupec primárního klíče řádku a zbývající sloupce ve zdroji dat se shodují původní hodnoty řádku. Další informace najdete v tématu "Optimistickou metodu souběžného zpracování modelu pro aktualizace a odstraní," dál v tomto tématu.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Model optimistickou metodu souběžného pro aktualizace a odstranění  
 Logiku pro generování příkazy automaticky pro příkazy UPDATE a DELETE je založena na *optimistickou metodu souběžného*– to znamená, záznamy nejsou zamčené pro úpravy a mohou být upravena jiné uživatele nebo procesy v každém okamžiku. Vzhledem k tomu, že záznam mohl změnit po byla vrácena z příkaz SELECT, ale před vydáním příkazu UPDATE nebo DELETE, automaticky generovaný příkaz UPDATE nebo DELETE obsahuje klauzuli WHERE, určující, zda řádek hodnota aktualizuje jenom Pokud je obsahuje všechny původní hodnoty a ze zdroje dat nebyl odstraněn. Děje se tak aby nedošlo k přepsání nová data. Kde pokusí aktualizovat řádek, který byl odstraněn nebo neobsahuje původní hodnoty zjištěné v aktualizaci automaticky generovaný <xref:System.Data.DataSet>, příkaz nemá vliv na všechny záznamy a <xref:System.Data.DBConcurrencyException> je vyvolána výjimka.  
  
 Pokud chcete dokončit bez ohledu na původní hodnoty na aktualizaci nebo odstranění, musíte explicitně nastavit `UpdateCommand` pro `DataAdapter` a nespoléhala se na příkaz automatického generování.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Omezení příkaz Automatické generování logiky  
 Automatické příkaz generace platí následující omezení.  
  
### <a name="unrelated-tables-only"></a>Pouze nesouvisejících tabulek  
 Příkaz Automatické generování logiku generuje vložit, aktualizovat a odstraňovat příkazy pro samostatné tabulky bez ohledu na všechny vztahy s jinými tabulkami ve zdroji dat. V důsledku toho může dojde k chybě při volání metody `Update` k odeslání změn pro sloupec, který je součástí omezení cizího klíče v databázi. Chcete-li se vyhnout této výjimky, nepoužívejte <xref:System.Data.Common.DbCommandBuilder> pro aktualizace sloupců, které se účastní omezení cizího klíče; místo toho explicitně zadat příkazy, které používá k provedení operace.  
  
### <a name="table-and-column-names"></a>Tabulka a názvy sloupců  
 Příkaz Automatické generování logiku může selhat v případě, že názvy sloupců nebo názvy tabulek obsahovat žádné speciální znaky, jako je například mezery, tečky, uvozovek nebo jiných nealfanumerické znaky, i v případě, že oddělený závorkami. V závislosti na zprostředkovateli nastavení parametrů QuotePrefix a QuoteSuffix může povolit generování logika pro proces mezery, ale nelze použít uvozování speciální znaky. Plně kvalifikované názvy tabulek ve formě *catalog.schema.table* jsou podporovány.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Pomocí CommandBuilder k automatickému generování příkazu SQL  
 K automatickému generování příkazů SQL pro `DataAdapter`, nastavte nejprve `SelectCommand` vlastnost `DataAdapter`, pak vytvořte `CommandBuilder` objektu a zadat jako argument `DataAdapter` pro kterou `CommandBuilder` bude automaticky Generovat příkazů SQL.  
  
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
 Pokud změníte `CommandText` z `SelectCommand` po byly automaticky generovány příkazy INSERT, UPDATE nebo DELETE, může dojít k výjimce. Pokud upravený `SelectCommand.CommandText` obsahuje informace o schématu, který není konzistentní s `SelectCommand.CommandText` použít při vložení, aktualizaci nebo odstranění příkazy byly automaticky generované, budoucí volání `DataAdapter.Update` metoda může pokus o přístup sloupců, již existuje v aktuální tabulce odkazuje `SelectCommand`, a bude vyvolána výjimka.  
  
 Můžete obnovit informace o schématu používané `CommandBuilder` k automatickému generování příkazy voláním `RefreshSchema` metodu `CommandBuilder`.  
  
 Pokud chcete vědět, jaké příkaz byla automaticky vygenerována, můžete získat odkaz na automaticky generovaný příkazy pomocí `GetInsertCommand`, `GetUpdateCommand`, a `GetDeleteCommand` metody `CommandBuilder` objektu a kontrolu `CommandText`vlastnost přidružené příkazu.  
  
 Následující příklad kódu zapíše do konzoly aktualizace příkaz, který byl automaticky vygenerován.  
  
```  
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```  
  
 Následující příklad vytvoří `Customers` tabulky v `custDS` datovou sadu. **RefreshSchema** metoda je volána k aktualizaci automaticky generované příkazů pomocí této nové informace o sloupci.  
  
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
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Spuštění příkazu](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
