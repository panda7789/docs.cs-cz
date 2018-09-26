---
title: Provádění dávkových operací pomocí adaptérů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: cfc77ff3b030ffebf52feab0190f81fc4e581cf9
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231135"
---
# <a name="performing-batch-operations-using-dataadapters"></a>Provádění dávkových operací pomocí adaptérů dat
Umožňuje podporu služby batch v ADO.NET <xref:System.Data.Common.DataAdapter> pro operace INSERT, UPDATE a DELETE ze skupin <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> na server, místo abyste odesílali jednu operaci najednou. Snížení počet zpátečních cest k serveru se obvykle vytváří nárůstu výkonu. Pro zprostředkovatele dat .NET pro SQL Server jsou podporovány dávkové aktualizace (<xref:System.Data.SqlClient>) a Oracle (<xref:System.Data.OracleClient>).  
  
 Při aktualizaci databáze se změní z <xref:System.Data.DataSet> v předchozích verzích technologie ADO.NET, `Update` metodu `DataAdapter` provést aktualizace databáze pro jeden řádek. Jak provést iteraci přes řádky v zadané <xref:System.Data.DataTable>, přezkoumání všech <xref:System.Data.DataRow> zobrazíte, pokud má byla změněna. Pokud řádek měl byl upraven, a volat odpovídající `UpdateCommand`, `InsertCommand`, nebo `DeleteCommand`, v závislosti na hodnotě <xref:System.Data.DataRow.RowState%2A> vlastnost pro tento řádek. Každá aktualizace řádku podílejí síťové cesty k databázi.  
  
 Spouštění pomocí technologie ADO.NET 2.0 <xref:System.Data.Common.DbDataAdapter> zpřístupňuje <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> vlastnost. Nastavení `UpdateBatchSize` na kladné celé číslo hodnoty způsobí, že aktualizace databáze, kterou chcete odeslat jako dávek zadané velikosti. Například nastavení `UpdateBatchSize` 10 se skupině 10 samostatných příkazů a odeslat jako jedné dávce. Nastavení `UpdateBatchSize` na hodnotu 0 způsobí, že <xref:System.Data.Common.DataAdapter> použít největší velikost dávky, který dokáže pracovat na serveru. Nastavení na 1 zakáže dávkové aktualizace s odesíláním řádky jsou postupně po jednom.  
  
 Provádění velmi velký batch může snížit výkon. Proto byste měli testovat pro nastavení velikosti dávky optimální před implementací vaší aplikace.  
  
## <a name="using-the-updatebatchsize-property"></a>Pomocí vlastnosti UpdateBatchSize  
 Pokud se povolí aktualizace služby batch, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> hodnotou vlastnosti Vlastnost DataAdapter `UpdateCommand`, `InsertCommand`, a `DeleteCommand` by mělo být nastavené <xref:System.Data.UpdateRowSource.None> nebo <xref:System.Data.UpdateRowSource.OutputParameters>. Při provádění dávky aktualizací, příkaz <xref:System.Data.IDbCommand.UpdatedRowSource%2A> hodnotou vlastnosti <xref:System.Data.UpdateRowSource.FirstReturnedRecord> nebo <xref:System.Data.UpdateRowSource.Both> je neplatný.  
  
 Následující postup demonstruje použití `UpdateBatchSize` vlastnost. Podle postupu přebírá dva argumenty <xref:System.Data.DataSet> objekt, který má sloupce představující **ProductCategoryID** a **název** pole v **Production.ProductCategory**tabulky a celé číslo představující velikost dávky (počet řádků v dávce). Kód vytvoří novou <xref:System.Data.SqlClient.SqlDataAdapter> objekt nastavení jeho <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, a <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> vlastnosti. Kód předpokládá, <xref:System.Data.DataSet> objekt má upravit řádky. Nastaví `UpdateBatchSize` vlastnost a provede aktualizaci.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Zpracování dávkové aktualizace související události a chyby  
 **DataAdapter** má dvě události související s aktualizace: **RowUpdating** a **RowUpdated**. V předchozích verzích technologie ADO.NET Pokud dávkové zpracování je zakázané, každá z těchto událostí se vygeneruje jednou pro každý řádek zpracování. **RowUpdating** je generovaná, než dojde k aktualizaci, a **RowUpdated** se vygeneruje po dokončení aktualizace databáze.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Událost změny chování s aktualizacemi služby Batch  
 Pokud je povoleno dávkové zpracování, více řádků se aktualizují v rámci operace izolované databáze. Proto pouze jeden `RowUpdated` dojde k události pro jednotlivé dávky, zatímco `RowUpdating` pro každý řádek zpracování dojde k události. Při zpracování dávky je zakázaná, jsou vyvolávány dvě události s 1: 1 prokládání, pokud jeden `RowUpdating` událost a jedna `RowUpdated` fire události pro řádek a potom na jeden `RowUpdating` a jeden `RowUpdated` fire události pro další řádek, dokud se všechny řádky jsou zpracovávány.  
  
### <a name="accessing-updated-rows"></a>Přístup k aktualizované řádky  
 Pokud je zakázáno dávkové zpracování, řádek aktualizuje lze přistupovat pomocí <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> vlastnost <xref:System.Data.Common.RowUpdatedEventArgs> třídy.  
  
 Pokud je povolená dávkové zpracování, jeden `RowUpdated` vygenerování události pro více řádků. Proto se hodnota `Row` vlastnost pro každý řádek má hodnotu null. `RowUpdating` události jsou i nadále vygenerována pro každý řádek. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metodu <xref:System.Data.Common.RowUpdatedEventArgs> třída umožňuje přístup k zpracovaných řádků zkopírováním odkazy na řádky do pole. Pokud jsou zpracovávány žádné řádky, `CopyToRows` vyvolá <xref:System.ArgumentNullException>. Použití <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> vlastnost vrátí počet zpracovaných před voláním řádků <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> metody.  
  
### <a name="handling-data-errors"></a>Chyby zpracování dat  
 Spuštění dávky má stejný účinek jako spuštění všech jednotlivých příkazů. Příkazy jsou spouštěny v pořadí, příkazy byly přidány do služby batch. Zpracování chyb v dávkovém režimu stejným způsobem jako při dávkovém režimu je zakázané. Každý řádek se zpracovávají odděleně. Pouze řádky, které byly úspěšně zpracovány v databázi budou aktualizovány v odpovídající <xref:System.Data.DataRow> v rámci <xref:System.Data.DataTable>.  
  
 Zprostředkovatel dat a serveru back-end databáze určují, které konstrukce SQL jsou podporovány pro spuštění dávky. Pokud příkazu není podporováno se odešle ke spuštění může být vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
