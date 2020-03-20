---
title: Parametry s hodnotami v tabulkách
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 2917a8d9b42d831566855271a2f2110637db586f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174469"
---
# <a name="table-valued-parameters"></a>Parametry s hodnotami v tabulkách
Parametry s hodnotou tabulky poskytují snadný způsob, jak zařadit více řádků dat z klientské aplikace na SQL Server bez nutnosti více zpátečních cest nebo speciální logiky na straně serveru pro zpracování dat. Parametry s hodnotou tabulky můžete použít k zapouzdření řádků dat v klientské aplikaci a k odeslání dat na server v jediném parametrizovaném příkazu. Řádky příchozích dat jsou uloženy v proměnné tabulky, které pak lze provozovat pomocí Transact-SQL.  
  
 Hodnoty sloupců v parametrech s hodnotou tabulky lze přistupovat pomocí standardních příkazů Transact-SQL SELECT. Parametry s hodnotou tabulky jsou silně zadávány a jejich struktura je automaticky ověřena. Velikost parametrů s hodnotou tabulky je omezena pouze pamětí serveru.  
  
> [!NOTE]
> Data nelze vrátit v parametru s hodnotou tabulky. Parametry s hodnotou tabulky jsou pouze pro vstup; klíčové slovo VÝSTUP není podporováno.  
  
 Další informace o parametrech s hodnotou tabulky naleznete v následujících zdrojích.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Použití parametrů s hodnotou tabulky (databázový stroj)](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|Popisuje, jak vytvořit a používat parametry s hodnotou tabulky.|  
|[Uživatelem definované typy tabulek](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))|Popisuje uživatelem definované typy tabulek, které se používají k deklarování parametrů s hodnotou tabulky.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Předání více řádků v předchozích verzích serveru SQL Server  
 Před parametry s hodnotou tabulky byly zavedeny sql server 2008, možnosti pro předávání více řádků dat do uložené procedury nebo parametrizovaný příkaz SQL byly omezené. Vývojář si může vybrat z následujících možností pro předávání více řádků na server:  
  
- Pomocí řady jednotlivých parametrů rekonpresitujte hodnoty ve více sloupcích a řádcích dat. Množství dat, která mohou být předány pomocí této metody je omezen počet povolených parametrů. Sql Server procedury může mít maximálně 2100 parametry. Logika na straně serveru je vyžadována k sestavení těchto jednotlivých hodnot do proměnné tabulky nebo dočasné tabulky pro zpracování.  
  
- Sloňte více datových hodnot do oddělených řetězců nebo dokumentů XML a pak je předavte do procedury nebo příkazu. To vyžaduje, aby postup nebo příkaz zahrnoval logiku nezbytnou pro ověření datových struktur a oddělení hodnot.  
  
- Vytvořte řadu jednotlivých příkazů SQL pro změny dat, které ovlivňují `Update` více řádků, například ty, které byly vytvořeny voláním metody <xref:System.Data.SqlClient.SqlDataAdapter>. Změny lze odeslat na server jednotlivě nebo dávkově do skupin. Však i v případě, že jsou odeslány v dávkách, které obsahují více příkazů, každý příkaz je proveden samostatně na serveru.  
  
- Pomocí `bcp` nástroje program <xref:System.Data.SqlClient.SqlBulkCopy> nebo objekt načíst mnoho řádků dat do tabulky. Přestože je tato technika velmi efektivní, nepodporuje zpracování na straně serveru, pokud nejsou data načtena do dočasné proměnné tabulky nebo tabulky.  
  
## <a name="creating-table-valued-parameter-types"></a>Vytváření typů parametrů s hodnotou tabulky  
 Parametry s hodnotou tabulky jsou založeny na strukturách tabulek silného typu, které jsou definovány pomocí příkazů Transact-SQL CREATE TYPE. Musíte vytvořit typ tabulky a definovat strukturu v SQL Server před použitím parametrů s hodnotou tabulky v klientských aplikacích. Další informace o vytváření typů tabulek naleznete v [tématu User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).  
  
 Následující příkaz vytvoří typ tabulky s názvem CategoryTableType, který se skládá ze sloupců CategoryID a CategoryName:  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Po vytvoření typu tabulky můžete deklarovat parametry s hodnotou tabulky na základě tohoto typu. Následující fragment Transact-SQL ukazuje, jak deklarovat parametr s hodnotou tabulky v definici uložené procedury. Všimněte si, že readonly klíčové slovo je vyžadováno pro deklarování parametru s hodnotou tabulky.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Úprava dat s parametry s hodnotou tabulky (Transact-SQL)  
 Parametry s hodnotou tabulky lze použít v úpravách dat založených na sadě, které ovlivňují více řádků provedením jednoho příkazu. Můžete například vybrat všechny řádky v parametru s hodnotou tabulky a vložit je do databázové tabulky, nebo můžete vytvořit příkaz aktualizace spojením parametru s hodnotou tabulky k tabulce, kterou chcete aktualizovat.  
  
 Následující příkaz Transact-SQL UPDATE ukazuje, jak použít parametr s hodnotou tabulky spojením s tabulkou Kategorie. Při použití parametru s hodnotou tabulky s JOIN v klauzuli FROM, musíte jej také aliasovat, jak je znázorněno zde, kde je parametr s hodnotou tabulky aliasován jako "ec":  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 Tento příklad Transact-SQL ukazuje, jak vybrat řádky z parametru s hodnotou tabulky k provedení INSERT v operaci založené na jedné sadě.  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Omezení parametrů s hodnotou tabulky  
 Existují několik omezení parametrů s hodnotou tabulky:  
  
- Parametry s hodnotou tabulky nelze předat [uživatelům definovaným funkcím CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).  
  
- Parametry s hodnotou tabulky lze indexovat pouze pro podporu omezení jedinečných nebo primárních klíčů. SQL Server neudržuje statistiky parametrů s hodnotou tabulky.  
  
- Parametry s hodnotou tabulky jsou jen pro čtení v kódu Transact-SQL. Hodnoty sloupců nelze aktualizovat v řádcích parametru s hodnotou tabulky a nelze je vložit ani odstranit. Chcete-li upravit data předávaná uložené proceduře nebo parametrizovanému příkazu v parametru s hodnotou tabulky, je nutné je vložit do dočasné tabulky nebo do proměnné tabulky.  
  
- Příkazy ALTER TABLE nelze použít k úpravě návrhu parametrů s hodnotou tabulky.  
  
## <a name="configuring-a-sqlparameter-example"></a>Konfigurace příkladu parametrů SqlParameter  
 <xref:System.Data.SqlClient>podporuje vyplnění parametrů s hodnotou <xref:System.Data.DataTable>tabulky <xref:System.Data.Common.DbDataReader> <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> z objektu nebo objektů. Je nutné zadat název typu parametru s <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> hodnotou <xref:System.Data.SqlClient.SqlParameter>tabulky pomocí vlastnosti . Musí `TypeName` odpovídat názvu kompatibilního typu, který byl dříve vytvořen na serveru. Následující fragment kódu ukazuje, <xref:System.Data.SqlClient.SqlParameter> jak nakonfigurovat vkládání dat.  

V následujícím příkladu `addedCategories` proměnná <xref:System.Data.DataTable>obsahuje . Chcete-li zjistit, jak je proměnná naplněna, podívejte se na příklady v další části [Předání parametru s hodnotou tabulky uložené proceduře](#passing).

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
  
 Můžete také použít libovolný objekt <xref:System.Data.Common.DbDataReader> odvozený z streamovat řádky dat do parametru s hodnotou tabulky, jak je znázorněno v tomto fragmentu:  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a>Předání parametru s hodnotou tabulky uložené procedurě  
 Tento příklad ukazuje, jak předat data parametrů s hodnotou tabulky do uložené procedury. Kód extrahuje přidané řádky <xref:System.Data.DataTable> do <xref:System.Data.DataTable.GetChanges%2A> nového pomocí metody. Kód pak definuje <xref:System.Data.SqlClient.SqlCommand>, nastavení <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> vlastnosti . <xref:System.Data.CommandType.StoredProcedure> Je <xref:System.Data.SqlClient.SqlParameter> naplněn pomocí <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> metody a <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> je nastavena na `Structured`. Potom <xref:System.Data.SqlClient.SqlCommand> je proveden pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Předání parametru s hodnotou tabulky parametrizovanému příkazu SQL  
 Následující příklad ukazuje, jak vložit data do dbo. Kategorie tabulky pomocí příkazu INSERT s poddotazem SELECT, který má jako zdroj dat parametr s hodnotou tabulky. Při předávání parametru s hodnotou tabulky parametrizovanému příkazu SQL je nutné zadat název <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> typu <xref:System.Data.SqlClient.SqlParameter>parametru s hodnotou tabulky pomocí nové vlastnosti . To `TypeName` se musí shodovat s názvem kompatibilního typu, který byl dříve vytvořen na serveru. Kód v tomto příkladu `TypeName` používá vlastnost odkazovat na strukturu typu definovanou v dbo. CategoryTableType.  
  
> [!NOTE]
> Pokud zadáte hodnotu pro sloupec identity v parametru s hodnotou tabulky, musíte vydat příkaz SET IDENTITY_INSERT pro relaci.  
  
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
 Můžete také použít libovolný objekt <xref:System.Data.Common.DbDataReader> odvozený z datového proudu řádků dat do parametru s hodnotou tabulky. Následující fragment kódu ukazuje načítání dat z databáze <xref:System.Data.OracleClient.OracleCommand> Oracle <xref:System.Data.OracleClient.OracleDataReader>pomocí a . Kód pak nakonfiguruje a <xref:System.Data.SqlClient.SqlCommand> vyvolat uloženou proceduru s jedním vstupním parametrem. Vlastnost <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> je <xref:System.Data.SqlClient.SqlParameter> nastavena `Structured`na . Předá <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> `OracleDataReader` sadu výsledků uložené prouce jako parametr s hodnotou tabulky.  
  
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
  
## <a name="see-also"></a>Viz také

- [Konfigurace parametrů a datové typy parametrů](../configuring-parameters-and-parameter-data-types.md)
- [Příkazy a parametry](../commands-and-parameters.md)
- [Parametry adaptéru dat](../dataadapter-parameters.md)
- [Operace dat na SQL Serveru v ADO.NET](sql-server-data-operations.md)
- [Přehled ADO.NET](../ado-net-overview.md)
