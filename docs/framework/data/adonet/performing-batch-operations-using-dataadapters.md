---
title: "Provádění operací Batch pomocí DataAdapters"
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
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e5c584bcd825e390b24da6c95ecb159a8280c639
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="performing-batch-operations-using-dataadapters"></a>Provádění operací Batch pomocí DataAdapters
Umožňuje podporu batch v ADO.NET <xref:System.Data.Common.DataAdapter> k seskupení operace INSERT, UPDATE a DELETE z <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> k serveru, místo abyste odesílali jednu operaci najednou. Snížení počet zpátečních cest k serveru se obvykle výsledkem výrazné zvýšení výkonu. Dávková aktualizace jsou podporované pro zprostředkovatele dat .NET pro SQL Server (<xref:System.Data.SqlClient>) a Oracle (<xref:System.Data.OracleClient>).  
  
 Až se aktualizace databáze se změní z <xref:System.Data.DataSet> v předchozích verzích technologie ADO.NET, `Update` metodu `DataAdapter` v daném okamžiku provádět aktualizace databáze pro jeden řádek. Jak ho vstupní prostřednictvím řádky v zadané <xref:System.Data.DataTable>, je zkontrolován každý <xref:System.Data.DataRow> chcete zobrazit, pokud byl změněn. Pokud řádek měl byl upraven, názvem odpovídající `UpdateCommand`, `InsertCommand`, nebo `DeleteCommand`, v závislosti na hodnotě <xref:System.Data.DataRow.RowState%2A> vlastnost pro tento řádek. Každá aktualizace řádku podílejí round-trip sítě do databáze.  
  
 Od verze ADO.NET 2.0 <xref:System.Data.Common.DbDataAdapter> zpřístupní <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> vlastnost. Nastavení `UpdateBatchSize` kladné celé číslo hodnoty způsobí, že aktualizace databáze, která se budou odesílat jako dávky po zadanou velikost. Například nastavení `UpdateBatchSize` na 10 bude skupina 10 samostatných příkazů a odesílat je jako jeden batch. Nastavení `UpdateBatchSize` na hodnotu 0 způsobí, že <xref:System.Data.Common.DataAdapter> používat největší velikost dávky, který server může zpracovat. Nastavení se na 1 zakáže dávková aktualizace, protože řádky jsou odesílány jeden po druhém.  
  
 Provádění velmi velký batch může snížit výkon. Proto byste měli otestovat pro nastavení velikosti optimální batch před implementací vaší aplikace.  
  
## <a name="using-the-updatebatchsize-property"></a>Pomocí vlastnosti UpdateBatchSize  
 Pokud jsou povoleny aktualizace batch, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> hodnota vlastnosti Vlastnost DataAdapter `UpdateCommand`, `InsertCommand`, a `DeleteCommand` musí být nastavena na <xref:System.Data.UpdateRowSource.None> nebo <xref:System.Data.UpdateRowSource.OutputParameters>. Při provádění dávky aktualizovat, příkaz <xref:System.Data.IDbCommand.UpdatedRowSource%2A> hodnota vlastnosti <xref:System.Data.UpdateRowSource.FirstReturnedRecord> nebo <xref:System.Data.UpdateRowSource.Both> je neplatný.  
  
 Následující postup ukazuje použití `UpdateBatchSize` vlastnost. Dva argumenty, které procedura používá <xref:System.Data.DataSet> objekt, který má sloupců představujícího **ProductCategoryID** a **název** polí v **Production.ProductCategory**tabulky a celé číslo představující velikost dávky (počet řádků v dávce). Kód vytvoří novou <xref:System.Data.SqlClient.SqlDataAdapter> objektu, nastavení jeho <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, a <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> vlastnosti. Kód předpokládá, že <xref:System.Data.DataSet> objekt změnil řádků. Nastaví `UpdateBatchSize` vlastnost a provede aktualizace.  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new   
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",   
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",   
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",   
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",   
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",   
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",   
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a>Zpracování dávky aktualizace související události a chyby  
 **DataAdapter** má dvě události související s aktualizace: **RowUpdating** a **RowUpdated**. V předchozích verzích technologie ADO.NET při zpracování dávky je zakázaná, každá z těchto událostí se generuje jednou pro každý řádek zpracovat. **RowUpdating** se vygeneruje, než dojde k aktualizaci, a **RowUpdated** se generuje po dokončení aktualizace databáze.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Změny chování událostí s dávková aktualizace  
 Pokud je povoleno zpracování dávky, více řádků se aktualizují v rámci jedné databáze operace. Proto pouze jeden `RowUpdated` vyskytne událost pro každou dávku, zatímco `RowUpdating` pro každý řádek zpracování dojde k události. Při zpracování dávky je zakázaná, při vyvolání dvou událostí s prokládání 1: 1, pokud jeden `RowUpdating` událost a jedna `RowUpdated` ještě efektivněji událostí pro řádek a pak jeden `RowUpdating` a jeden `RowUpdated` ještě efektivněji událostí pro další řádek, dokud všechny řádky jsou zpracovávány.  
  
### <a name="accessing-updated-rows"></a>Přístup k aktualizované řádky  
 Při zpracování dávky je zakázaná, řádek aktualizované lze přistupovat pomocí <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> vlastnost <xref:System.Data.Common.RowUpdatedEventArgs> třídy.  
  
 Pokud je povolená dávkové zpracování, jeden `RowUpdated` vygenerování události pro více řádků. Proto hodnotu `Row` vlastnost pro každý řádek má hodnotu null. `RowUpdating`události se generují stále pro každý řádek. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metodu <xref:System.Data.Common.RowUpdatedEventArgs> třída umožňuje přístup k Zpracované řádky zkopírováním odkazy na řádky do pole. Pokud žádné řádky jsou zpracovávány, `CopyToRows` vyvolá <xref:System.ArgumentNullException>. Použití <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> vlastnost vrátí počet řádků, které zpracují dříve, než volání <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> metoda.  
  
### <a name="handling-data-errors"></a>Zpracování chyb dat  
 Spuštění dávky má stejný účinek jako provádění každé jednotlivé příkaz. Příkazy jsou spouštěny v pořadí, příkazy byly přidány do dávky. Chyby jsou zpracovávány stejným způsobem jako v dávkovém režimu, protože se jedná o, když je zakázáno dávkovém režimu. Každý řádek se zpracovávají odděleně. Pouze řádky, které byly úspěšně zpracovány v databázi budou aktualizovány v odpovídající <xref:System.Data.DataRow> v rámci <xref:System.Data.DataTable>.  
  
 Zprostředkovatel dat a databázi back-end serveru určují, které konstrukce SQL jsou podporovány pro spuštění dávky. Může být vyvolána výjimka, pokud odeslání příkazu není podporován pro provedení.  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
