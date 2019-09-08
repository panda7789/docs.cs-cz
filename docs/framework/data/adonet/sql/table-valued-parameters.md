---
title: Parametry s hodnotami v tabulkách
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 316ccb19ca9e384be97a83e992af46934702aa0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780686"
---
# <a name="table-valued-parameters"></a>Parametry s hodnotami v tabulkách
Parametry s hodnotou tabulky poskytují snadný způsob, jak zařadit více řádků dat z klientské aplikace do SQL Server bez vyžadování více zpátečních cest nebo speciální logiky na straně serveru pro zpracování dat. K zapouzdření řádků dat v klientské aplikaci a posílání dat na server v jednom parametrizovaném příkazu můžete použít parametry s hodnotou tabulky. Příchozí datové řádky jsou uloženy v proměnné tabulky, které lze následně provozovat pomocí jazyka Transact-SQL.  
  
 Hodnoty sloupce v parametrech s hodnotou tabulky lze použít jako standardní příkazy SELECT jazyka Transact-SQL. Parametry s hodnotou tabulky jsou silného typu a jejich struktura je automaticky ověřena. Velikost parametrů s hodnotou tabulky je omezená jenom na paměť serveru.  
  
> [!NOTE]
> Nelze vrátit data v parametru s hodnotou tabulky. Parametry s hodnotou tabulky jsou pouze vstupní; klíčové slovo OUTPUT není podporováno.  
  
 Další informace o parametrech s hodnotou tabulky najdete v následujících zdrojích informací.  
  
|Resource|Popis|  
|--------------|-----------------|  
|[Parametry s hodnotou tabulky (databázový stroj)](https://go.microsoft.com/fwlink/?LinkId=98363) v SQL Server Knihy online|Popisuje, jak vytvořit a použít parametry s hodnotou tabulky.|  
|[Uživatelem definované typy tabulek](https://go.microsoft.com/fwlink/?LinkId=98364) v SQL Server Knihy online|Popisuje uživatelsky definované typy tabulek, které se používají k deklaraci parametrů s hodnotou tabulky.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Předávání více řádků v předchozích verzích SQL Server  
 Než byly zavedeny parametry s hodnotou tabulky SQL Server 2008, byly omezeny možnosti pro předávání více řádků dat do uložené procedury nebo parametrizovaný příkaz SQL. Vývojář se může rozhodnout z následujících možností pro předávání více řádků serveru:  
  
- Pro reprezentaci hodnot ve více sloupcích a řádcích dat použijte řadu jednotlivých parametrů. Množství dat, které lze předat pomocí této metody, je omezeno počtem povolených parametrů. SQL Server postupy může mít maximálně 2100 parametrů. Logika na straně serveru je nutná k sestavení těchto jednotlivých hodnot do proměnné tabulky nebo dočasné tabulky pro zpracování.  
  
- Seskupit více hodnot dat do řetězců s oddělovači nebo dokumentů XML a pak tyto textové hodnoty předat proceduře nebo příkazu. K tomu je potřeba, aby procedura nebo příkaz zahrnoval logiku potřebnou k ověřování datových struktur a odstavování hodnot.  
  
- Vytvořte řadu jednotlivých příkazů SQL pro úpravy dat, které ovlivňují více řádků, například ty, které byly `Update` vytvořeny voláním metody typu. <xref:System.Data.SqlClient.SqlDataAdapter> Změny je možné odeslat na server jednotlivě nebo do skupin v dávce. Nicméně i v případě odeslání v dávkách, které obsahují více příkazů, každý příkaz je proveden samostatně na serveru.  
  
- `bcp` Pomocí programu<xref:System.Data.SqlClient.SqlBulkCopy> nebo objektu můžete načíst mnoho řádků dat do tabulky. I když je tato technika velmi efektivní, nepodporuje zpracování na straně serveru, pokud nejsou data načtena do dočasné tabulky nebo proměnné tabulky.  
  
## <a name="creating-table-valued-parameter-types"></a>Vytváření typů parametrů s hodnotou tabulky  
 Parametry s hodnotou tabulky jsou založené na strukturách tabulek se silnými typy, které jsou definovány pomocí příkazů CREATE-SQL CREATE TYPE. Aby bylo možné v klientských aplikacích použít parametry s hodnotou tabulky, je třeba vytvořit typ tabulky a definovat strukturu v SQL Server. Další informace o vytváření typů tabulek najdete v tématu [uživatelsky definované typy tabulek](https://go.microsoft.com/fwlink/?LinkID=98364) v SQL Server Books Online.  
  
 Následující příkaz vytvoří typ tabulky s názvem CategoryTableType, který se skládá z sloupců KódKategorie a CategoryName:  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Po vytvoření typu tabulky můžete deklarovat parametry s hodnotou tabulky na základě tohoto typu. Následující fragment Transact-SQL ukazuje, jak deklarovat parametr s hodnotou tabulky v definici uložené procedury. Všimněte si, že klíčové slovo READONLY je vyžadováno pro deklaraci parametru s hodnotou tabulky.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Úprava dat pomocí parametrů s hodnotou tabulky (Transact-SQL)  
 Parametry s hodnotou tabulky lze použít v úpravách dat založených na sadě, které mají vliv na více řádků provedením jednoho příkazu. Můžete například vybrat všechny řádky v parametru s hodnotou tabulky a vložit je do tabulky databáze, nebo můžete vytvořit příkaz Update připojením parametru s hodnotou tabulky do tabulky, kterou chcete aktualizovat.  
  
 Následující příkaz UPDATE jazyka Transact-SQL ukazuje, jak použít parametr s hodnotou tabulky připojením k tabulce categories (kategorie). Když použijete parametr s hodnotou tabulky s SPOJENÍm v klauzuli FROM, musíte ho také aliasovat, jak je znázorněno zde, kde parametr s hodnotou tabulky má alias "ES":  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 Tento příklad Transact-SQL ukazuje, jak vybrat řádky z parametru s hodnotou tabulky k provedení vložení v rámci jedné operace založené na sadě.  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Omezení parametrů s hodnotou tabulky  
 Existují několik omezení pro parametry s hodnotou tabulky:  
  
- Do [uživatelsky definovaných funkcí CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)nelze předat parametry s hodnotou tabulky.  
  
- Parametry s hodnotou tabulky můžou být indexované jenom pro podporu omezení UNIQUE nebo PRIMARY KEY. SQL Server neudržuje statistiku pro parametry s hodnotou tabulky.  
  
- Parametry s hodnotou tabulky jsou jen pro čtení v kódu Transact-SQL. Hodnoty sloupce nelze aktualizovat v řádcích parametru s hodnotou tabulky a nelze vkládat ani odstraňovat řádky. Chcete-li upravit data předávaná do uložené procedury nebo parametrizovaného příkazu v parametru s hodnotou tabulky, je nutné vložit data do dočasné tabulky nebo do proměnné tabulky.  
  
- Pomocí příkazů ALTER TABLE nelze upravovat návrh parametrů s hodnotou tabulky.  
  
## <a name="configuring-a-sqlparameter-example"></a>Příklad konfigurace SqlParameter  
 <xref:System.Data.SqlClient>podporuje zaplňování parametrů s hodnotou tabulky <xref:System.Data.DataTable>z <xref:System.Data.Common.DbDataReader> nebo <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> objektů. Je nutné zadat název typu pro parametr s hodnotou tabulky pomocí <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnosti. <xref:System.Data.SqlClient.SqlParameter> Se `TypeName` musí shodovat s názvem kompatibilního typu, který byl dříve vytvořen na serveru. Následující fragment kódu ukazuje, jak konfigurovat <xref:System.Data.SqlClient.SqlParameter> pro vkládání dat.  
 
V následujícím příkladu `addedCategories` proměnná <xref:System.Data.DataTable>obsahuje. Chcete-li zjistit, jak je proměnná naplněna, přečtěte si příklady v následující části, [předáním parametru s hodnotou tabulky do uložené procedury](#passing).

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```  
  
```vb  
' Configure the command and parameter.  
Dim insertCommand As New SqlCommand(sqlInsert, connection)  
Dim tvpParam As SqlParameter = _  
   insertCommand.Parameters.AddWithValue( _  
  "@tvpNewCategories", addedCategories)  
tvpParam.SqlDbType = SqlDbType.Structured  
tvpParam.TypeName = "dbo.CategoryTableType"  
```  
  
 Můžete také použít libovolný objekt odvozený z <xref:System.Data.Common.DbDataReader> pro streamování řádků dat do parametru s hodnotou tabulky, jak je znázorněno v tomto fragmentu:  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
```vb  
' Configure the SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  dataReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
```  
  
## <a name="passing"></a>Předání parametru s hodnotou tabulky do uložené procedury  
 Tento příklad ukazuje, jak předat data parametrů s hodnotou tabulky do uložené procedury. Kód extrahuje přidané řádky do nového <xref:System.Data.DataTable> <xref:System.Data.DataTable.GetChanges%2A> pomocí metody. Kód pak definuje a <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> nastaví vlastnost na <xref:System.Data.CommandType.StoredProcedure>hodnotu. Hodnota je naplněna <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> pomocí metody a <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> je nastavena na `Structured`. <xref:System.Data.SqlClient.SqlParameter> Pak se spustí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>pomocímetody. <xref:System.Data.SqlClient.SqlCommand>  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection object.  
Using connection  
   '  Create a DataTable with the modified rows.  
   Dim addedCategories As DataTable = _  
     CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Configure the SqlCommand and SqlParameter.  
   Dim insertCommand As New SqlCommand( _  
     "usp_InsertCategories", connection)  
   insertCommand.CommandType = CommandType.StoredProcedure  
   Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
     "@tvpNewCategories", addedCategories)  
   tvpParam.SqlDbType = SqlDbType.Structured  
  
   '  Execute the command.  
   insertCommand.ExecuteNonQuery()  
End Using  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Předání parametru s hodnotou tabulky do parametrizovaného příkazu jazyka SQL  
 Následující příklad ukazuje, jak vložit data do databáze dbo. Tabulka kategorií pomocí příkazu INSERT s VÝBĚROVÝm poddotazem, který má parametr s hodnotou tabulky jako zdroj dat. Při předání parametru s hodnotou tabulky do parametrizovaného příkazu jazyka SQL je nutné zadat název typu pro parametr s hodnotou tabulky pomocí vlastnosti New <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> <xref:System.Data.SqlClient.SqlParameter>třídy. Ta `TypeName` se musí shodovat s názvem kompatibilního typu dříve vytvořeným na serveru. Kód v tomto příkladu používá `TypeName` vlastnost k odkazování na strukturu typu definovanou v dbo. CategoryTableType.  
  
> [!NOTE]
> Pokud zadáte hodnotu pro sloupec identity v parametru s hodnotou tabulky, je nutné vystavit příkaz SET IDENTITY_INSERT pro relaci.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
Using connection  
  ' Create a DataTable with the modified rows.  
  Dim addedCategories As DataTable = _  
    CategoriesDataTable.GetChanges(DataRowState.Added)  
  
  ' Define the INSERT-SELECT statement.  
  Dim sqlInsert As String = _  
  "INSERT INTO dbo.Categories (CategoryID, CategoryName)" _  
  & " SELECT nc.CategoryID, nc.CategoryName" _  
  & " FROM @tvpNewCategories AS nc;"  
  
  ' Configure the command and parameter.  
  Dim insertCommand As New SqlCommand(sqlInsert, connection)  
  Dim tvpParam As SqlParameter = _  
     insertCommand.Parameters.AddWithValue( _  
    "@tvpNewCategories", addedCategories)  
  tvpParam.SqlDbType = SqlDbType.Structured  
  tvpParam.TypeName = "dbo.CategoryTableType"  
  
  ' Execute the query  
  insertCommand.ExecuteNonQuery()  
End Using  
```  
  
## <a name="streaming-rows-with-a-datareader"></a>Streamování řádků pomocí objektu DataReader  
 Můžete také použít libovolný objekt odvozený z <xref:System.Data.Common.DbDataReader> pro streamování řádků dat do parametru s hodnotou tabulky. Následující fragment kódu ukazuje, jak načíst data z databáze Oracle pomocí <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader>a. Kód pak nakonfiguruje <xref:System.Data.SqlClient.SqlCommand> , aby vyvolal uloženou proceduru s jedním vstupním parametrem. Vlastnost je nastavena na`Structured`hodnotu. <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Nastavívýsledeksadyvýsledkůnauloženouprocedurujako`OracleDataReader` parametr s hodnotou tabulky.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
```vb  
' Assumes connection is an open SqlConnection.  
' Retrieve data from Oracle.  
Dim selectCommand As New OracleCommand( _  
  "Select CategoryID, CategoryName FROM Categories;", _  
  oracleConnection)  
Dim oracleReader As OracleDataReader = _  
  selectCommand.ExecuteReader(CommandBehavior.CloseConnection)  
  
' Configure SqlCommand and table-valued parameter.  
Dim insertCommand As New SqlCommand("usp_InsertCategories", connection)  
insertCommand.CommandType = CommandType.StoredProcedure  
Dim tvpParam As SqlParameter = _  
  insertCommand.Parameters.AddWithValue("@tvpNewCategories", _  
  oracleReader)  
tvpParam.SqlDbType = SqlDbType.Structured  
  
' Execute the command.  
insertCommand.ExecuteNonQuery()  
```  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace parametrů a datové typy parametrů](../configuring-parameters-and-parameter-data-types.md)
- [Příkazy a parametry](../commands-and-parameters.md)
- [Parametry adaptéru dat](../dataadapter-parameters.md)
- [Operace dat na SQL Serveru v ADO.NET](sql-server-data-operations.md)
- [Přehled ADO.NET](../ado-net-overview.md)
