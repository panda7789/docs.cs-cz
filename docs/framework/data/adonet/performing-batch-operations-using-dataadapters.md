---
title: Provádění dávkových operací pomocí adaptérů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: cfc77ff3b030ffebf52feab0190f81fc4e581cf9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43789028"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="64175-102">Provádění dávkových operací pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="64175-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="64175-103">Umožňuje podporu služby batch v ADO.NET <xref:System.Data.Common.DataAdapter> pro operace INSERT, UPDATE a DELETE ze skupin <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> na server, místo abyste odesílali jednu operaci najednou.</span><span class="sxs-lookup"><span data-stu-id="64175-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="64175-104">Snížení počet zpátečních cest k serveru se obvykle vytváří nárůstu výkonu.</span><span class="sxs-lookup"><span data-stu-id="64175-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="64175-105">Pro zprostředkovatele dat .NET pro SQL Server jsou podporovány dávkové aktualizace (<xref:System.Data.SqlClient>) a Oracle (<xref:System.Data.OracleClient>).</span><span class="sxs-lookup"><span data-stu-id="64175-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="64175-106">Při aktualizaci databáze se změní z <xref:System.Data.DataSet> v předchozích verzích technologie ADO.NET, `Update` metodu `DataAdapter` provést aktualizace databáze pro jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="64175-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="64175-107">Jak provést iteraci přes řádky v zadané <xref:System.Data.DataTable>, přezkoumání všech <xref:System.Data.DataRow> zobrazíte, pokud má byla změněna.</span><span class="sxs-lookup"><span data-stu-id="64175-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="64175-108">Pokud řádek měl byl upraven, a volat odpovídající `UpdateCommand`, `InsertCommand`, nebo `DeleteCommand`, v závislosti na hodnotě <xref:System.Data.DataRow.RowState%2A> vlastnost pro tento řádek.</span><span class="sxs-lookup"><span data-stu-id="64175-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="64175-109">Každá aktualizace řádku podílejí síťové cesty k databázi.</span><span class="sxs-lookup"><span data-stu-id="64175-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="64175-110">Spouštění pomocí technologie ADO.NET 2.0 <xref:System.Data.Common.DbDataAdapter> zpřístupňuje <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="64175-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="64175-111">Nastavení `UpdateBatchSize` na kladné celé číslo hodnoty způsobí, že aktualizace databáze, kterou chcete odeslat jako dávek zadané velikosti.</span><span class="sxs-lookup"><span data-stu-id="64175-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="64175-112">Například nastavení `UpdateBatchSize` 10 se skupině 10 samostatných příkazů a odeslat jako jedné dávce.</span><span class="sxs-lookup"><span data-stu-id="64175-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="64175-113">Nastavení `UpdateBatchSize` na hodnotu 0 způsobí, že <xref:System.Data.Common.DataAdapter> použít největší velikost dávky, který dokáže pracovat na serveru.</span><span class="sxs-lookup"><span data-stu-id="64175-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="64175-114">Nastavení na 1 zakáže dávkové aktualizace s odesíláním řádky jsou postupně po jednom.</span><span class="sxs-lookup"><span data-stu-id="64175-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="64175-115">Provádění velmi velký batch může snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="64175-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="64175-116">Proto byste měli testovat pro nastavení velikosti dávky optimální před implementací vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="64175-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="64175-117">Pomocí vlastnosti UpdateBatchSize</span><span class="sxs-lookup"><span data-stu-id="64175-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="64175-118">Pokud se povolí aktualizace služby batch, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> hodnotou vlastnosti Vlastnost DataAdapter `UpdateCommand`, `InsertCommand`, a `DeleteCommand` by mělo být nastavené <xref:System.Data.UpdateRowSource.None> nebo <xref:System.Data.UpdateRowSource.OutputParameters>.</span><span class="sxs-lookup"><span data-stu-id="64175-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="64175-119">Při provádění dávky aktualizací, příkaz <xref:System.Data.IDbCommand.UpdatedRowSource%2A> hodnotou vlastnosti <xref:System.Data.UpdateRowSource.FirstReturnedRecord> nebo <xref:System.Data.UpdateRowSource.Both> je neplatný.</span><span class="sxs-lookup"><span data-stu-id="64175-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="64175-120">Následující postup demonstruje použití `UpdateBatchSize` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="64175-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="64175-121">Podle postupu přebírá dva argumenty <xref:System.Data.DataSet> objekt, který má sloupce představující **ProductCategoryID** a **název** pole v **Production.ProductCategory**tabulky a celé číslo představující velikost dávky (počet řádků v dávce).</span><span class="sxs-lookup"><span data-stu-id="64175-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="64175-122">Kód vytvoří novou <xref:System.Data.SqlClient.SqlDataAdapter> objekt nastavení jeho <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, a <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="64175-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="64175-123">Kód předpokládá, <xref:System.Data.DataSet> objekt má upravit řádky.</span><span class="sxs-lookup"><span data-stu-id="64175-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="64175-124">Nastaví `UpdateBatchSize` vlastnost a provede aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="64175-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="64175-125">Zpracování dávkové aktualizace související události a chyby</span><span class="sxs-lookup"><span data-stu-id="64175-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="64175-126">**DataAdapter** má dvě události související s aktualizace: **RowUpdating** a **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="64175-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="64175-127">V předchozích verzích technologie ADO.NET Pokud dávkové zpracování je zakázané, každá z těchto událostí se vygeneruje jednou pro každý řádek zpracování.</span><span class="sxs-lookup"><span data-stu-id="64175-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="64175-128">**RowUpdating** je generovaná, než dojde k aktualizaci, a **RowUpdated** se vygeneruje po dokončení aktualizace databáze.</span><span class="sxs-lookup"><span data-stu-id="64175-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="64175-129">Událost změny chování s aktualizacemi služby Batch</span><span class="sxs-lookup"><span data-stu-id="64175-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="64175-130">Pokud je povoleno dávkové zpracování, více řádků se aktualizují v rámci operace izolované databáze.</span><span class="sxs-lookup"><span data-stu-id="64175-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="64175-131">Proto pouze jeden `RowUpdated` dojde k události pro jednotlivé dávky, zatímco `RowUpdating` pro každý řádek zpracování dojde k události.</span><span class="sxs-lookup"><span data-stu-id="64175-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="64175-132">Při zpracování dávky je zakázaná, jsou vyvolávány dvě události s 1: 1 prokládání, pokud jeden `RowUpdating` událost a jedna `RowUpdated` fire události pro řádek a potom na jeden `RowUpdating` a jeden `RowUpdated` fire události pro další řádek, dokud se všechny řádky jsou zpracovávány.</span><span class="sxs-lookup"><span data-stu-id="64175-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="64175-133">Přístup k aktualizované řádky</span><span class="sxs-lookup"><span data-stu-id="64175-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="64175-134">Pokud je zakázáno dávkové zpracování, řádek aktualizuje lze přistupovat pomocí <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> vlastnost <xref:System.Data.Common.RowUpdatedEventArgs> třídy.</span><span class="sxs-lookup"><span data-stu-id="64175-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="64175-135">Pokud je povolená dávkové zpracování, jeden `RowUpdated` vygenerování události pro více řádků.</span><span class="sxs-lookup"><span data-stu-id="64175-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="64175-136">Proto se hodnota `Row` vlastnost pro každý řádek má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="64175-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="64175-137">`RowUpdating` události jsou i nadále vygenerována pro každý řádek.</span><span class="sxs-lookup"><span data-stu-id="64175-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="64175-138"><xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metodu <xref:System.Data.Common.RowUpdatedEventArgs> třída umožňuje přístup k zpracovaných řádků zkopírováním odkazy na řádky do pole.</span><span class="sxs-lookup"><span data-stu-id="64175-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="64175-139">Pokud jsou zpracovávány žádné řádky, `CopyToRows` vyvolá <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="64175-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="64175-140">Použití <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> vlastnost vrátí počet zpracovaných před voláním řádků <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="64175-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="64175-141">Chyby zpracování dat</span><span class="sxs-lookup"><span data-stu-id="64175-141">Handling Data Errors</span></span>  
 <span data-ttu-id="64175-142">Spuštění dávky má stejný účinek jako spuštění všech jednotlivých příkazů.</span><span class="sxs-lookup"><span data-stu-id="64175-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="64175-143">Příkazy jsou spouštěny v pořadí, příkazy byly přidány do služby batch.</span><span class="sxs-lookup"><span data-stu-id="64175-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="64175-144">Zpracování chyb v dávkovém režimu stejným způsobem jako při dávkovém režimu je zakázané.</span><span class="sxs-lookup"><span data-stu-id="64175-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="64175-145">Každý řádek se zpracovávají odděleně.</span><span class="sxs-lookup"><span data-stu-id="64175-145">Each row is processed separately.</span></span> <span data-ttu-id="64175-146">Pouze řádky, které byly úspěšně zpracovány v databázi budou aktualizovány v odpovídající <xref:System.Data.DataRow> v rámci <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="64175-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="64175-147">Zprostředkovatel dat a serveru back-end databáze určují, které konstrukce SQL jsou podporovány pro spuštění dávky.</span><span class="sxs-lookup"><span data-stu-id="64175-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="64175-148">Pokud příkazu není podporováno se odešle ke spuštění může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="64175-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64175-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="64175-149">See Also</span></span>  
 [<span data-ttu-id="64175-150">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="64175-150">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="64175-151">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="64175-151">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="64175-152">Zpracování událostí adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="64175-152">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [<span data-ttu-id="64175-153">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="64175-153">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
