---
title: Parametry s hodnotami v tabulkách
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: d1d52e048ee54ce967215ad134d5bcff2983103e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113617"
---
# <a name="table-valued-parameters"></a>Parametry s hodnotami v tabulkách
Parametry s hodnotou tabulky poskytují snadný způsob, jak zařadit více řádků dat z klientské aplikace k SQL serveru bez nutnosti více výměn nebo zvláštní logiku na straně serveru pro zpracování dat. Parametry table-valued můžete použít k zapouzdření řádky dat v aplikaci klienta a odesílání dat na server v jedné parametrizovaného příkazu. Řádky příchozích dat jsou uložené v proměnné tabulky, který může pak být provozována pomocí [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].  
  
 Hodnoty sloupců v parametrů table-valued lze přistupovat pomocí standardní [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazů SELECT. Parametry Table-valued jsou silného typu a jejich strukturu se automaticky ověří. Velikost parametrů table-valued je omezena pouze paměť serveru.  
  
> [!NOTE]
>  Nelze vrátit data v parametru s hodnotou tabulky. Parametry Table-valued jsou výhradně; VÝSTUP – klíčové slovo se nepodporuje.  
  
 Další informace o parametry table-valued najdete v následující prostředky.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Parametry Table-Valued (databázový stroj)](https://go.microsoft.com/fwlink/?LinkId=98363) v Online knihách serveru SQL|Popisuje, jak vytvořit a používat parametry s hodnotou tabulky.|  
|[Uživatelem definované typy tabulek](https://go.microsoft.com/fwlink/?LinkId=98364) v Online knihách serveru SQL|Popisuje uživatele definovaných typů tabulek, které se používají k deklarování parametrů table-valued.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Předání více řádků v předchozích verzích systému SQL Server  
 Předtím, než se seznámili s parametry table-valued systému SQL Server 2008, byly omezené možnosti pro předání více řádků dat uložené procedury nebo parametrizovaného příkazu SQL. Vývojář může zvolit jednu z následujících možností pro předání více řádků na server:  
  
-   K reprezentaci hodnoty do více sloupců a řádků dat použijte řadu jednotlivé parametry. Množství dat, které mohou být předány tímto způsobem je omezen počet povolených parametrů. Postupy pro SQL Server může mít maximálně 2100 parametry. Je potřeba sestavit tyto jednotlivé hodnoty do proměnné tabulky nebo dočasná tabulka pro zpracování logiky na straně serveru.  
  
-   Vytvoření balíčku více hodnot dat do řetězce s oddělovači nebo dokumentů XML a předat tyto hodnoty text do procedury nebo příkaz. To vyžaduje procedury nebo prohlášení přidat logiku potřebnou pro ověření datových struktur a zpřístupnění hodnoty.  
  
-   Vytvořte řadu jednotlivých příkazů SQL pro změny dat, které ovlivňují více řádků, jako jsou ty voláním `Update` metodu <xref:System.Data.SqlClient.SqlDataAdapter>. Změny můžete odeslat na server samostatně nebo v dávce do skupin. Ale i v případě, že odešle v dávkách, které obsahují více příkazů, každý příkaz je proveden odděleně na serveru.  
  
-   Použití `bcp` nástroj nebo <xref:System.Data.SqlClient.SqlBulkCopy> objektu, který chcete načíst počet řádků dat do tabulky. I když tato technika je velmi efektivní, nepodporuje zpracování na straně serveru, pokud načtení dat do dočasné tabulky nebo proměnné tabulky.  
  
## <a name="creating-table-valued-parameter-types"></a>Vytváření typů Table-Valued Parameter  
 Parametry Table-valued jsou založené na tabulce silného typu struktury, které jsou definovány pomocí [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy CREATE TYPE. Budete muset vytvořit tabulku typu a definují strukturu v systému SQL Server, abyste mohli používat parametry table-valued v klientských aplikacích. Další informace o vytváření typů tabulek, naleznete v tématu [uživatelem definované typy tabulek](https://go.microsoft.com/fwlink/?LinkID=98364) v SQL Server Books Online.  
  
 Následující příkaz vytvoří typ tabulky s názvem CategoryTableType, který se skládá z ID kategorie a CategoryName sloupce:  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Jakmile vytvoříte typ tabulky, je možné deklarovat parametry s hodnotou tabulky na základě tohoto typu. Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment ukazuje, jak deklarovat parametr s hodnotou tabulky v definici uloženou proceduru. Všimněte si, že READONLY – klíčové slovo je vyžadována pro deklarování parametr s hodnotou tabulky.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Úpravy dat s parametry Table-Valued (Transact-SQL)  
 Parametry s hodnotou tabulky je možné v změny založeným na set dat, které ovlivňují více řádků pomocí provádí jeden příkaz. Například můžete vybrat všechny řádky v parametru s hodnotou tabulky a vložení do tabulky databáze, nebo vytvoříte příkazu update spojením parametr s hodnotou tabulky do tabulky, kterou chcete aktualizovat.  
  
 Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazu UPDATE ukazuje, jak se pomocí připojení k tabulce kategorie parametr s hodnotou tabulky. Pokud použijete parametr s hodnotou tabulky s spojení v klauzuli FROM, musíte mít také alias, jak je znázorněno zde, kde parametr s hodnotou tabulky je alias jako "ES":  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 To [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příklad ukazuje, jak pro výběr řádků z parametru s hodnotou tabulky provést vložení v rámci jedné operace založeným na set.  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Omezení parametrů Table-Valued  
 Existují některá omezení pro parametry s hodnotou tabulky:  
  
-   Nelze předat parametry s hodnotou tabulky [uživatelem definované funkce CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).  
  
-   Parametry s hodnotou tabulky je možné indexovat pouze pro podporu omezení UNIQUE a PRIMARY KEY. SQL Server nespravuje statistiky pro parametry s hodnotou tabulky.  
  
-   Parametry Table-valued jsou jen pro čtení v [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kódu. Hodnoty sloupce na řádky parametr s hodnotou tabulky nelze aktualizovat, a nelze vložit nebo odstranit řádky. Pokud chcete upravit data, která je předána uloženou proceduru nebo příkaz v parametr s hodnotou tabulky s parametry, je nutné vložit data do dočasné tabulky nebo do proměnné tabulky.  
  
-   Pomocí příkazů ALTER TABLE nelze použít k úpravě návrhu parametrů table-valued.  
  
## <a name="configuring-a-sqlparameter-example"></a>Konfigurace příklad SqlParameter  
 <xref:System.Data.SqlClient> podporuje sestavování parametrů table-valued z <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> nebo <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> objekty. Musíte zadat název typu pro parametr s hodnotou tabulky s použitím <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter>. `TypeName` Musí odpovídat názvu kompatibilního typu dříve vytvořené na serveru. Následující fragment kódu ukazuje, jak nakonfigurovat <xref:System.Data.SqlClient.SqlParameter> vložit data.  
 
V následujícím příkladu `addedCategories` obsahuje proměnnou <xref:System.Data.DataTable>. Pokud chcete zjistit, jak se vyplní proměnnou, podívejte se na příklady v další části [předávání parametru Table-Valued uložená procedura](#passing).

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
  
 Můžete také použít jakéhokoli objektu odvozeného od <xref:System.Data.Common.DbDataReader> pro datový proud řádky dat na parametr s hodnotou tabulky, jak je znázorněno v tomto fragmentu:  
  
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
  
## <a name="passing"></a> Předání parametru s hodnotou tabulky uložené procedury  
 Tento příklad ukazuje, jak předat parametr s hodnotou tabulky data pro uloženou proceduru. Kód extrahuje přidání řádků do nového <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.GetChanges%2A> metody. Kód poté definuje <xref:System.Data.SqlClient.SqlCommand>a nastavte <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> vlastnost <xref:System.Data.CommandType.StoredProcedure>. <xref:System.Data.SqlClient.SqlParameter> Naplněn pomocí <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> metoda a <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> je nastavena na `Structured`. <xref:System.Data.SqlClient.SqlCommand> Je pak provést pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Předávání Table-Valued Parameter parametrizovaného dotazu SQL příkaz  
 Následující příklad ukazuje, jak vložit data do vlastníka. Tabulky kategorií pomocí příkazu INSERT SELECT poddotazu, která má parametr s hodnotou tabulky jako zdroje dat Při předávání parametru s hodnotou tabulky parametrizovaného příkazu SQL, musíte zadat název typu pro parametr s hodnotou tabulky s použitím nového <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter>. To `TypeName` musí odpovídat názvu kompatibilního typu dříve vytvořené na serveru. Kód v tomto příkladu používá `TypeName` vlastnost odkazovat na typ struktury definované v dbo. CategoryTableType.  
  
> [!NOTE]
>  Pokud zadáte hodnotu pro sloupec identity v parametru s hodnotou tabulky, musíte vydat příkaz IDENTITY_INSERT NASTAVENA pro relaci.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>Streamování řádků pomocí čtečky dat  
 Můžete také použít jakéhokoli objektu odvozeného od <xref:System.Data.Common.DbDataReader> pro datový proud řádky dat na parametr s hodnotou tabulky. Následující fragment kódu ukazuje, načítání dat z databáze Oracle pomocí <xref:System.Data.OracleClient.OracleCommand> a <xref:System.Data.OracleClient.OracleDataReader>. Kód poté konfiguruje <xref:System.Data.SqlClient.SqlCommand> vyvolat uloženou proceduru s jeden vstupní parametr. <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Vlastnost <xref:System.Data.SqlClient.SqlParameter> je nastavena na `Structured`. <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Předává `OracleDataReader` sadu výsledků pro uloženou proceduru jako parametr s hodnotou tabulky.  
  
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

- [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Příkazy a parametry](../../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Parametry adaptéru dat](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- [Operace dat na SQL Serveru v ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
