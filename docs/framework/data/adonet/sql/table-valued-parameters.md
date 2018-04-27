---
title: Parametry s hodnotou tabulky
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 01b19d49ee82a884247e4eb260f659f19f124cee
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="table-valued-parameters"></a>Parametry s hodnotou tabulky
Parametry s hodnotou tabulky představují snadný způsob, jak zařazování bez nutnosti více odezev nebo speciální logiku na straně serveru pro zpracování dat více řádků dat z klientské aplikace do systému SQL Server. Parametry s hodnotou tabulky můžete použít k zapouzdření řádky dat v aplikaci klienta a odesílání dat na server v jedné parametrizovaného příkazu. Příchozí data řádky jsou uložené v proměnné tabulky, která lze poté ho zpracovat. pomocí [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].  
  
 Hodnoty ve sloupcích v parametry s hodnotou tabulky lze přistupovat pomocí standardní [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazů SELECT. Parametry s hodnotou tabulky jsou silného typu a jejich struktura je automaticky ověřit. Velikost parametry s hodnotou tabulky je omezena pouze paměti serveru.  
  
> [!NOTE]
>  Parametr s hodnotou tabulky nelze vrátit data. Parametry s hodnotou tabulky jsou jenom vstupní; klíčové slovo výstup není podporováno.  
  
 Další informace o parametry s hodnotou tabulky najdete v následujících materiálech.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Parametry s hodnotou tabulky (databázový stroj)](http://go.microsoft.com/fwlink/?LinkId=98363) v Online knihách serveru SQL|Popisuje, jak vytvořit a používat parametry s hodnotou tabulky.|  
|[Uživatelem definované typy tabulky](http://go.microsoft.com/fwlink/?LinkId=98364) v Online knihách serveru SQL|Popisuje typy uživatelem definovaná tabulka, které se používá k deklaraci parametry s hodnotou tabulky.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Předávání více řádků v předchozích verzích systému SQL Server  
 Před parametry s hodnotou tabulky byly zavedeny na SQL Server 2008, byly omezené možnosti pro předání více řádků dat do uložené procedury nebo parametrizované příkaz SQL. Vývojář může zvolit z následujících možností pro předávání více řádků k serveru:  
  
-   K reprezentaci hodnoty ve více sloupců a řádků dat použijte řadu jednotlivé parametry. Množství dat, který může být předán pomocí této metody je omezen počet parametrů, které jsou povoleny. Postupy systému SQL Server může mít maximálně 2100 parametry. Je potřeba sestavte tyto jednotlivé hodnoty do proměnné tabulky nebo dočasné tabulky pro zpracování logiky na straně serveru.  
  
-   Sady více hodnot dat do odděleného řetězce nebo dokumentů XML a pak předejte tyto hodnoty text do procedury nebo příkaz. To vyžaduje procedura nebo údajů přidat logiku, která je potřebná pro ověření datové struktury a zpřístupnění hodnoty.  
  
-   Vytvořit řadu jednotlivé příkazy SQL pro změny dat, které ovlivňují více řádků, jako jsou ty vytvořená voláním `Update` metodu <xref:System.Data.SqlClient.SqlDataAdapter>. Změny může být odeslána na server individuálně nebo v dávce do skupin. Ale i v případě, že odeslání v dávkách, které obsahují více příkazů, každý se spustit příkaz samostatně na serveru.  
  
-   Použití `bcp` nástroj program nebo <xref:System.Data.SqlClient.SqlBulkCopy> objekt, který chcete načíst počet řádků dat do tabulky. I když tato technika je velmi efektivní, nejsou podporovány serverové zpracování, pokud je načíst data do dočasné tabulky nebo proměnná tabulky.  
  
## <a name="creating-table-valued-parameter-types"></a>Vytváření parametr s hodnotou tabulky typů  
 Parametry s hodnotou tabulky jsou založené na struktury silného typu tabulky, které jsou definované za použití [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy CREATE TYPE. Budete muset vytvořit typ tabulky a definovat strukturu v systému SQL Server, abyste mohli používat parametry s hodnotou tabulky v klientských aplikacích. Další informace o vytváření typů tabulek najdete v tématu [uživatelem definovaných typů tabulek](http://go.microsoft.com/fwlink/?LinkID=98364) v SQL Server Books Online.  
  
 Následující příkaz vytvoří typ tabulky s názvem CategoryTableType, která se skládá z CategoryID a CategoryName sloupce:  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 Jakmile vytvoříte typ tabulky, je možné deklarovat parametry s hodnotou tabulky na základě tohoto typu. Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment ukazuje, jak lze deklarovat parametr s hodnotou tabulky v definici uložené procedury. Všimněte si, že READONLY – klíčové slovo je vyžadována pro deklarování parametr s hodnotou tabulky.  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Úprava dat s parametry s hodnotou tabulky (Transact-SQL)  
 Parametry s hodnotou tabulky lze použít v změny na základě sady dat, které ovlivňují více řádků spuštěním jeden příkaz. Například můžete vybrat všechny řádky v parametru s hodnotou tabulky a vložte je do databázové tabulky, nebo můžete vytvořit příkazu update připojení parametr s hodnotou tabulky do tabulky, kterou chcete aktualizovat.  
  
 Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazu UPDATE ukazuje, jak použít parametr s hodnotou tabulky s připojením k tabulce kategorie. Pokud použijete parametr s hodnotou tabulky s spojení v klauzuli FROM, musíte také alias, jak je vidět tady, kde parametr s hodnotou tabulky je alias jako "ES":  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 To [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příklad ukazuje, jak vybírat parametr s hodnotou tabulky k provedení typu vložení v rámci jedné operace založené na sadě řádků.  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Omezení parametrů s hodnotou tabulky  
 Existuje několik omezení pro parametry s hodnotou tabulky:  
  
-   Nelze předat parametry s hodnotou tabulky [uživatelsky definované funkce CLR](http://msdn.microsoft.com/library/ms131077.aspx).  
  
-   Parametry s hodnotou tabulky lze indexovat pouze pro podporu omezení JEDINEČNÝ nebo primární klíč. SQL Server neudržuje statistiky na parametry s hodnotou tabulky.  
  
-   Parametry s hodnotou tabulky jsou jen pro čtení v [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kódu. Hodnoty ve sloupcích v řádcích parametr s hodnotou tabulky nelze aktualizovat, a nelze vložit nebo odstranit řádky. Chcete-li upravit data, která je předaný uložené proceduře nebo příkaz v parametru s hodnotou tabulky s parametry, je nutné vložit data do dočasné tabulky nebo do proměnné tabulky.  
  
-   Pomocí příkazů ALTER TABLE nelze použít k úpravě návrh parametry s hodnotou tabulky.  
  
## <a name="configuring-a-sqlparameter-example"></a>Konfigurace SqlParameter příklad  
 <xref:System.Data.SqlClient> podporuje naplnění parametry s hodnotou tabulky z <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> nebo <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> objekty. Musíte zadat název typu pro parametr s hodnotou tabulky s použitím <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter>. `TypeName` Musí odpovídat názvu kompatibilní typ vytvořili na serveru. Následující fragment kódu ukazuje, jak nakonfigurovat <xref:System.Data.SqlClient.SqlParameter> vložit data.  
  
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
  
 Můžete také použít libovolného objektu odvozeného z <xref:System.Data.Common.DbDataReader> na datový proud řádky dat do parametr s hodnotou tabulky, jak je uvedené v tomto fragmentu:  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a>Předání parametru s hodnotou tabulky uložené procedury  
 Tento příklad ukazuje, jak k předávání dat parametr s hodnotou tabulky uložené procedury. Vyextrahuje přidání řádků do nového <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.GetChanges%2A> metoda. Kód pak definuje <xref:System.Data.SqlClient.SqlCommand>, nastavení <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> vlastnost <xref:System.Data.CommandType.StoredProcedure>. <xref:System.Data.SqlClient.SqlParameter> Je vyplněný pomocí <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> metoda a <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> je nastaven na `Structured`. <xref:System.Data.SqlClient.SqlCommand> Se pak spustí pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metoda.  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Předání parametru s hodnotou tabulky příkazu parametrizované SQL  
 Následující příklad ukazuje, jak pro vložení dat do vlastníka. Kategorie tabulky pomocí příkazu INSERT vyberte poddotazu, která má jako zdroj dat pro parametr s hodnotou tabulky. Při předávání parametr s hodnotou tabulky parametrizované příkazu jazyka SQL, musíte zadat název typu pro parametr s hodnotou tabulky pomocí nové <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter>. To `TypeName` musí odpovídat názvu kompatibilní typ vytvořili na serveru. Kód v tomto příkladu používá `TypeName` vlastnost tak, aby odkazovaly strukturou typů, které jsou definované v dbo. CategoryTableType.  
  
> [!NOTE]
>  Pokud zadáte hodnotu pro sloupec identity parametr s hodnotou tabulky, musíte vydat příkaz nastavit možnost identity_insert nastavena pro relaci.  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a>Streamování řádky s DataReader –  
 Můžete také použít libovolného objektu odvozeného z <xref:System.Data.Common.DbDataReader> na datový proud řádky dat do parametr s hodnotou tabulky. Následující fragment kódu ukazuje načítání dat z databáze Oracle pomocí <xref:System.Data.OracleClient.OracleCommand> a <xref:System.Data.OracleClient.OracleDataReader>. Kód, nakonfiguruje <xref:System.Data.SqlClient.SqlCommand> k vyvolání uložená procedura s jeden vstupní parametr. <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Vlastnost <xref:System.Data.SqlClient.SqlParameter> je nastaven na `Structured`. <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Předá `OracleDataReader` sady výsledků uložené procedury jako parametr s hodnotou tabulky.  
  
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
 [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Příkazy a parametry](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Parametry adaptéru dat](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Operace dat na SQL Serveru v ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
