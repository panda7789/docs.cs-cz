---
title: Provádění dávkových operací pomocí adaptérů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 62a61051e5b9d896f8a89ed3d2745859fc07a7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149255"
---
# <a name="performing-batch-operations-using-dataadapters"></a>Provádění dávkových operací pomocí adaptérů dat
Dávková podpora v <xref:System.Data.Common.DataAdapter> ADO.NET umožňuje seskupit <xref:System.Data.DataSet> operace <xref:System.Data.DataTable> INSERT, UPDATE a DELETE z nebo na server namísto odesílání jedné operace najednou. Snížení počtu zpátečních cest na server obvykle vede k významnému zvýšení výkonu. Dávkové aktualizace jsou podporovány pro zprostředkovatele<xref:System.Data.SqlClient>dat .NET pro SQL Server ( ) a Oracle (<xref:System.Data.OracleClient>).  
  
 Při aktualizaci databáze se <xref:System.Data.DataSet> změnami z v `Update` předchozích `DataAdapter` verzích ADO.NET, metoda provedené aktualizace databáze jeden řádek najednou. Jak iteroval přes řádky v <xref:System.Data.DataTable>zadaném <xref:System.Data.DataRow> , zkoumal každý, zda byl změněn. Pokud byl řádek změněn, nazývá `UpdateCommand`se `InsertCommand`příslušná , nebo `DeleteCommand`, <xref:System.Data.DataRow.RowState%2A> v závislosti na hodnotě vlastnosti pro tento řádek. Každá aktualizace řádku zahrnovala síťovou odezvu do databáze.  
  
 Počínaje ADO.NET 2.0, <xref:System.Data.Common.DbDataAdapter> zpřístupňuje <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> vlastnost. `UpdateBatchSize` Nastavení kladné celé číslo hodnota způsobí, že aktualizace databáze, které mají být odeslány jako dávky zadané velikosti. Například nastavení `UpdateBatchSize` do 10 bude skupina 10 samostatné příkazy a odeslat jako jednu dávku. Nastavení `UpdateBatchSize` na 0 způsobí, <xref:System.Data.Common.DataAdapter> že použije největší velikost dávky, kterou může server zpracovat. Nastavení na 1 zakáže dávkové aktualizace, protože řádky jsou odesílány po jednom.  
  
 Spuštění extrémně velké dávky může snížit výkon. Proto byste měli před implementací aplikace otestovat optimální nastavení velikosti dávky.  
  
## <a name="using-the-updatebatchsize-property"></a>Použití vlastnosti UpdateBatchSize  
 Pokud jsou povoleny <xref:System.Data.IDbCommand.UpdatedRowSource%2A> dávkové aktualizace, hodnota `UpdateCommand`vlastnosti DataAdapter , `InsertCommand`, a `DeleteCommand` by měla být nastavena na <xref:System.Data.UpdateRowSource.None> nebo <xref:System.Data.UpdateRowSource.OutputParameters>. Při provádění dávkové aktualizace je <xref:System.Data.IDbCommand.UpdatedRowSource%2A> hodnota vlastnosti příkazu <xref:System.Data.UpdateRowSource.FirstReturnedRecord> nebo <xref:System.Data.UpdateRowSource.Both> je neplatná.  
  
 Následující postup ukazuje použití vlastnosti. `UpdateBatchSize` Postup trvá dva <xref:System.Data.DataSet> argumenty, objekt, který má sloupce představující **ProductCategoryID** a **Název** pole v tabulce **Production.ProductCategory** a celé číslo představující velikost dávky (počet řádků v dávce). Kód vytvoří nový <xref:System.Data.SqlClient.SqlDataAdapter> objekt, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>nastavení <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>jeho <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> , a vlastnosti. Kód předpokládá, že <xref:System.Data.DataSet> objekt má změněné řádky. Nastaví `UpdateBatchSize` vlastnost a provede aktualizaci.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Zpracování událostí a chyb souvisejících s dávkovou aktualizací  
 **DataAdapter** má dvě události související s aktualizací: **RowUpdating** a **RowUpdated**. V předchozích verzích ADO.NET, pokud je dávkové zpracování zakázáno, každá z těchto událostí je generována jednou pro každý řádek zpracován. **RowUpdating** je generována před dojde k aktualizaci a **RowUpdated** je generována po dokončení aktualizace databáze.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Změny chování událostí s dávkovými aktualizacemi  
 Pokud je povoleno dávkové zpracování, více řádků jsou aktualizovány v rámci operace jedné databáze. Proto pouze `RowUpdated` jedna událost nastane pro každou `RowUpdating` dávku, vzhledem k tomu, že k události dochází pro každý řádek zpracovány. Pokud je dávkové zpracování zakázáno, jsou aktivovány dvě události `RowUpdating` s prokládáním 1:1, kde jedna událost a jedna `RowUpdated` událost se zapálí pro řádek a pak jeden `RowUpdating` a jeden `RowUpdated` požár události pro další řádek, dokud nebudou zpracovány všechny řádky.  
  
### <a name="accessing-updated-rows"></a>Přístup k aktualizovaným řádkům  
 Pokud je dávkové zpracování zakázáno, je k <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> aktualizovanému <xref:System.Data.Common.RowUpdatedEventArgs> řádku přistupovat pomocí vlastnosti třídy.  
  
 Pokud je povoleno dávkové `RowUpdated` zpracování, je generována jedna událost pro více řádků. Proto je hodnota `Row` vlastnosti pro každý řádek null. `RowUpdating`události jsou stále generovány pro každý řádek. Metoda <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> <xref:System.Data.Common.RowUpdatedEventArgs> třídy umožňuje přístup ke zpracovaným řádkům zkopírováním odkazů na řádky do pole. Pokud nejsou zpracovávány žádné `CopyToRows` řádky, <xref:System.ArgumentNullException>vyvolá . Pomocí <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> vlastnosti vrátíte počet řádků zpracovaných <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> před voláním metody.  
  
### <a name="handling-data-errors"></a>Zpracování chyb dat  
 Dávkové spuštění má stejný účinek jako provádění každého jednotlivého příkazu. Příkazy jsou prováděny v pořadí, ve které byly přidány do dávky. Chyby jsou zpracovány stejným způsobem v dávkovém režimu, jako jsou zakázány dávkovém režimu. Každý řádek je zpracován samostatně. Pouze řádky, které byly úspěšně zpracovány v databázi <xref:System.Data.DataRow> budou <xref:System.Data.DataTable>aktualizovány v odpovídající v rámci .  
  
 Zprostředkovatel dat a databázový server back-end určují, které konstrukce SQL jsou podporovány pro dávkové spuštění. Výjimka může být vyvolána, pokud je odeslán nepodporovaný příkaz k provedení.  
  
## <a name="see-also"></a>Viz také

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)
- [Zpracování událostí adaptéru dat](handling-dataadapter-events.md)
- [Přehled ADO.NET](ado-net-overview.md)
