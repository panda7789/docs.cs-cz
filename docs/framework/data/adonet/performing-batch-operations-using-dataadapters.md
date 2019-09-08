---
title: Provádění dávkových operací pomocí adaptérů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 8667cffb032daf0043915d3bee7127ef9b70756b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794516"
---
# <a name="performing-batch-operations-using-dataadapters"></a>Provádění dávkových operací pomocí adaptérů dat
Dávková podpora v ADO.NET umožňuje <xref:System.Data.Common.DataAdapter> Seskupit operace vložení, aktualizace a odstranění <xref:System.Data.DataSet> ze serveru nebo <xref:System.Data.DataTable> na server, místo aby bylo možné současně odeslat jednu operaci. Snížení počtu zpátečních cest k serveru obvykle vede k výraznému nárůstu výkonu. Aktualizace služby Batch jsou podporované pro zprostředkovatele dat .NET pro SQL Server (<xref:System.Data.SqlClient>) a Oracle (<xref:System.Data.OracleClient>).  
  
 Při aktualizaci databáze se změnami z <xref:System.Data.DataSet> verze v předchozích verzích nástroje ADO.NET `Update` Metoda `DataAdapter` provedených aktualizací do databáze po jednom řádku. Jak prochází řádky v určeném <xref:System.Data.DataTable>, <xref:System.Data.DataRow> prozkoumali jste je, abyste viděli, zda byla upravena. Pokud byl řádek upraven, byl označován jako `UpdateCommand`příslušný, `InsertCommand`nebo `DeleteCommand`v závislosti na hodnotě <xref:System.Data.DataRow.RowState%2A> vlastnosti pro daný řádek. Každá aktualizace řádku zahrnovala síťovou zpáteční cestu k databázi.  
  
 Počínaje verzí ADO.NET 2,0 <xref:System.Data.Common.DbDataAdapter> <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> zpřístupňuje vlastnost. `UpdateBatchSize` Nastavení na kladnou celočíselnou hodnotu způsobí, že se aktualizace databáze odešlou jako dávky zadané velikosti. Například nastavení na hodnotu `UpdateBatchSize` 10 bude seskupovat 10 samostatných příkazů a odešle je jako jednu dávku. Nastavení na hodnotu 0 způsobí, že <xref:System.Data.Common.DataAdapter> bude používat největší velikost dávky, kterou může server zpracovat. `UpdateBatchSize` Nastavení na hodnotu 1 zakáže dávkové aktualizace, protože řádky jsou odesílány po jednom.  
  
 Spuštění extrémně velké dávky může snížit výkon. Proto byste měli před implementací aplikace otestovat nastavení optimální velikosti dávky.  
  
## <a name="using-the-updatebatchsize-property"></a>Použití vlastnosti UpdateBatchSize  
 Pokud jsou <xref:System.Data.IDbCommand.UpdatedRowSource%2A> povoleny aktualizace dávky, hodnota vlastnosti `UpdateCommand`DataAdapter, `InsertCommand`a `DeleteCommand` by měla být nastavena na <xref:System.Data.UpdateRowSource.None> nebo <xref:System.Data.UpdateRowSource.OutputParameters>. Při provádění aktualizace dávky je <xref:System.Data.IDbCommand.UpdatedRowSource%2A> <xref:System.Data.UpdateRowSource.FirstReturnedRecord> hodnota vlastnosti příkazu nebo <xref:System.Data.UpdateRowSource.Both> neplatná.  
  
 Následující postup demonstruje použití `UpdateBatchSize` vlastnosti. Procedura přijímá dva argumenty <xref:System.Data.DataSet> , objekt, který má sloupce reprezentující pole **ProductCategoryID** a **Name** v tabulce **produkčního sloupce ProductCategory** a celé číslo představující velikost dávky (počet řádky v dávce). Kód vytvoří nový <xref:System.Data.SqlClient.SqlDataAdapter> objekt, nastaví jeho <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>vlastnosti, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>a <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> . Kód předpokládá, že <xref:System.Data.DataSet> objekt má změněné řádky. Nastaví `UpdateBatchSize` vlastnost a provede aktualizaci.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Zpracování událostí a chyb souvisejících s aktualizací Batch  
 Objekt **DataAdapter** má dvě události související s aktualizací: **RowUpdating** a **RowUpdated metody Update**. Pokud je v předchozích verzích ADO.NET zakázané dávkové zpracování, každá z těchto událostí se vygeneruje jednou pro každý zpracovávaný řádek. **RowUpdating** se vygeneruje před tím, než dojde k aktualizaci, a po dokončení aktualizace databáze se vygeneruje **RowUpdated metody Update** .  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Změny chování události v dávkových aktualizacích  
 Pokud je povoleno dávkové zpracování, v rámci jedné databáze se aktualizuje více řádků. Proto se pro každou `RowUpdated` dávku vyvolá jenom jedna událost, `RowUpdating` zatímco pro každý zpracovávaný řádek dojde k události. Když je dávkové zpracování zakázané, jsou tyto dvě události vyvolány pomocí prokládání 1:1, kdy jedna `RowUpdating` událost a jedna `RowUpdated` aktivovaná událost pro řádek a pak jedna `RowUpdating` a jedna `RowUpdated` událost pro další řádek, až do všech řádků. jsou zpracovávány.  
  
### <a name="accessing-updated-rows"></a>Přístup k aktualizovaným řádkům  
 Když je dávkové zpracování zakázané, k řádku, který se má aktualizovat, <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> se dá dostat <xref:System.Data.Common.RowUpdatedEventArgs> pomocí vlastnosti třídy.  
  
 Pokud je povoleno dávkové zpracování, je vygenerována jedna `RowUpdated` událost pro více řádků. Proto hodnota `Row` vlastnosti pro každý řádek má hodnotu null. `RowUpdating`události jsou stále generovány pro každý řádek. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metoda<xref:System.Data.Common.RowUpdatedEventArgs> třídy umožňuje přístup ke zpracovaným řádkům zkopírováním odkazů na řádky do pole. Pokud nejsou zpracovávány žádné řádky, `CopyToRows` <xref:System.ArgumentNullException>vyvolá. Použijte vlastnost k vrácení počtu zpracovaných řádků před <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> voláním metody. <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A>  
  
### <a name="handling-data-errors"></a>Zpracování chyb dat  
 Dávkové zpracování má stejný účinek jako spuštění každého jednotlivého příkazu. Příkazy jsou spouštěny v pořadí, v jakém byly do dávky přidány příkazy. Chyby jsou zpracovávány stejným způsobem v dávkovém režimu, protože jsou v režimu dávky zakázané. Každý řádek se zpracovává samostatně. Pouze řádky, které byly úspěšně zpracovány v databázi, budou aktualizovány v odpovídajícím <xref:System.Data.DataRow> <xref:System.Data.DataTable>rámci.  
  
 Poskytovatel dat a back-end databázový server určují, které konstrukce SQL jsou podporovány pro provádění dávky. Výjimka může být vyvolána, pokud je odeslán nepodporovaný příkaz ke spuštění.  
  
## <a name="see-also"></a>Viz také:

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)
- [Zpracování událostí adaptéru dat](handling-dataadapter-events.md)
- [Přehled ADO.NET](ado-net-overview.md)
