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
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="a6c48-102">Provádění dávkových operací pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="a6c48-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="a6c48-103">Dávková podpora v <xref:System.Data.Common.DataAdapter> ADO.NET umožňuje seskupit <xref:System.Data.DataSet> operace <xref:System.Data.DataTable> INSERT, UPDATE a DELETE z nebo na server namísto odesílání jedné operace najednou.</span><span class="sxs-lookup"><span data-stu-id="a6c48-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="a6c48-104">Snížení počtu zpátečních cest na server obvykle vede k významnému zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="a6c48-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="a6c48-105">Dávkové aktualizace jsou podporovány pro zprostředkovatele<xref:System.Data.SqlClient>dat .NET pro SQL Server ( ) a Oracle (<xref:System.Data.OracleClient>).</span><span class="sxs-lookup"><span data-stu-id="a6c48-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="a6c48-106">Při aktualizaci databáze se <xref:System.Data.DataSet> změnami z v `Update` předchozích `DataAdapter` verzích ADO.NET, metoda provedené aktualizace databáze jeden řádek najednou.</span><span class="sxs-lookup"><span data-stu-id="a6c48-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="a6c48-107">Jak iteroval přes řádky v <xref:System.Data.DataTable>zadaném <xref:System.Data.DataRow> , zkoumal každý, zda byl změněn.</span><span class="sxs-lookup"><span data-stu-id="a6c48-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="a6c48-108">Pokud byl řádek změněn, nazývá `UpdateCommand`se `InsertCommand`příslušná , nebo `DeleteCommand`, <xref:System.Data.DataRow.RowState%2A> v závislosti na hodnotě vlastnosti pro tento řádek.</span><span class="sxs-lookup"><span data-stu-id="a6c48-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="a6c48-109">Každá aktualizace řádku zahrnovala síťovou odezvu do databáze.</span><span class="sxs-lookup"><span data-stu-id="a6c48-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="a6c48-110">Počínaje ADO.NET 2.0, <xref:System.Data.Common.DbDataAdapter> zpřístupňuje <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a6c48-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="a6c48-111">`UpdateBatchSize` Nastavení kladné celé číslo hodnota způsobí, že aktualizace databáze, které mají být odeslány jako dávky zadané velikosti.</span><span class="sxs-lookup"><span data-stu-id="a6c48-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="a6c48-112">Například nastavení `UpdateBatchSize` do 10 bude skupina 10 samostatné příkazy a odeslat jako jednu dávku.</span><span class="sxs-lookup"><span data-stu-id="a6c48-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="a6c48-113">Nastavení `UpdateBatchSize` na 0 způsobí, <xref:System.Data.Common.DataAdapter> že použije největší velikost dávky, kterou může server zpracovat.</span><span class="sxs-lookup"><span data-stu-id="a6c48-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="a6c48-114">Nastavení na 1 zakáže dávkové aktualizace, protože řádky jsou odesílány po jednom.</span><span class="sxs-lookup"><span data-stu-id="a6c48-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="a6c48-115">Spuštění extrémně velké dávky může snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="a6c48-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="a6c48-116">Proto byste měli před implementací aplikace otestovat optimální nastavení velikosti dávky.</span><span class="sxs-lookup"><span data-stu-id="a6c48-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="a6c48-117">Použití vlastnosti UpdateBatchSize</span><span class="sxs-lookup"><span data-stu-id="a6c48-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="a6c48-118">Pokud jsou povoleny <xref:System.Data.IDbCommand.UpdatedRowSource%2A> dávkové aktualizace, hodnota `UpdateCommand`vlastnosti DataAdapter , `InsertCommand`, a `DeleteCommand` by měla být nastavena na <xref:System.Data.UpdateRowSource.None> nebo <xref:System.Data.UpdateRowSource.OutputParameters>.</span><span class="sxs-lookup"><span data-stu-id="a6c48-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="a6c48-119">Při provádění dávkové aktualizace je <xref:System.Data.IDbCommand.UpdatedRowSource%2A> hodnota vlastnosti příkazu <xref:System.Data.UpdateRowSource.FirstReturnedRecord> nebo <xref:System.Data.UpdateRowSource.Both> je neplatná.</span><span class="sxs-lookup"><span data-stu-id="a6c48-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="a6c48-120">Následující postup ukazuje použití vlastnosti. `UpdateBatchSize`</span><span class="sxs-lookup"><span data-stu-id="a6c48-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="a6c48-121">Postup trvá dva <xref:System.Data.DataSet> argumenty, objekt, který má sloupce představující **ProductCategoryID** a **Název** pole v tabulce **Production.ProductCategory** a celé číslo představující velikost dávky (počet řádků v dávce).</span><span class="sxs-lookup"><span data-stu-id="a6c48-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="a6c48-122">Kód vytvoří nový <xref:System.Data.SqlClient.SqlDataAdapter> objekt, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>nastavení <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>jeho <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> , a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a6c48-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="a6c48-123">Kód předpokládá, že <xref:System.Data.DataSet> objekt má změněné řádky.</span><span class="sxs-lookup"><span data-stu-id="a6c48-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="a6c48-124">Nastaví `UpdateBatchSize` vlastnost a provede aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="a6c48-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="a6c48-125">Zpracování událostí a chyb souvisejících s dávkovou aktualizací</span><span class="sxs-lookup"><span data-stu-id="a6c48-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="a6c48-126">**DataAdapter** má dvě události související s aktualizací: **RowUpdating** a **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="a6c48-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="a6c48-127">V předchozích verzích ADO.NET, pokud je dávkové zpracování zakázáno, každá z těchto událostí je generována jednou pro každý řádek zpracován.</span><span class="sxs-lookup"><span data-stu-id="a6c48-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="a6c48-128">**RowUpdating** je generována před dojde k aktualizaci a **RowUpdated** je generována po dokončení aktualizace databáze.</span><span class="sxs-lookup"><span data-stu-id="a6c48-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="a6c48-129">Změny chování událostí s dávkovými aktualizacemi</span><span class="sxs-lookup"><span data-stu-id="a6c48-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="a6c48-130">Pokud je povoleno dávkové zpracování, více řádků jsou aktualizovány v rámci operace jedné databáze.</span><span class="sxs-lookup"><span data-stu-id="a6c48-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="a6c48-131">Proto pouze `RowUpdated` jedna událost nastane pro každou `RowUpdating` dávku, vzhledem k tomu, že k události dochází pro každý řádek zpracovány.</span><span class="sxs-lookup"><span data-stu-id="a6c48-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="a6c48-132">Pokud je dávkové zpracování zakázáno, jsou aktivovány dvě události `RowUpdating` s prokládáním 1:1, kde jedna událost a jedna `RowUpdated` událost se zapálí pro řádek a pak jeden `RowUpdating` a jeden `RowUpdated` požár události pro další řádek, dokud nebudou zpracovány všechny řádky.</span><span class="sxs-lookup"><span data-stu-id="a6c48-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="a6c48-133">Přístup k aktualizovaným řádkům</span><span class="sxs-lookup"><span data-stu-id="a6c48-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="a6c48-134">Pokud je dávkové zpracování zakázáno, je k <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> aktualizovanému <xref:System.Data.Common.RowUpdatedEventArgs> řádku přistupovat pomocí vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="a6c48-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="a6c48-135">Pokud je povoleno dávkové `RowUpdated` zpracování, je generována jedna událost pro více řádků.</span><span class="sxs-lookup"><span data-stu-id="a6c48-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="a6c48-136">Proto je hodnota `Row` vlastnosti pro každý řádek null.</span><span class="sxs-lookup"><span data-stu-id="a6c48-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="a6c48-137">`RowUpdating`události jsou stále generovány pro každý řádek.</span><span class="sxs-lookup"><span data-stu-id="a6c48-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="a6c48-138">Metoda <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> <xref:System.Data.Common.RowUpdatedEventArgs> třídy umožňuje přístup ke zpracovaným řádkům zkopírováním odkazů na řádky do pole.</span><span class="sxs-lookup"><span data-stu-id="a6c48-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="a6c48-139">Pokud nejsou zpracovávány žádné `CopyToRows` řádky, <xref:System.ArgumentNullException>vyvolá .</span><span class="sxs-lookup"><span data-stu-id="a6c48-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="a6c48-140">Pomocí <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> vlastnosti vrátíte počet řádků zpracovaných <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> před voláním metody.</span><span class="sxs-lookup"><span data-stu-id="a6c48-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="a6c48-141">Zpracování chyb dat</span><span class="sxs-lookup"><span data-stu-id="a6c48-141">Handling Data Errors</span></span>  
 <span data-ttu-id="a6c48-142">Dávkové spuštění má stejný účinek jako provádění každého jednotlivého příkazu.</span><span class="sxs-lookup"><span data-stu-id="a6c48-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="a6c48-143">Příkazy jsou prováděny v pořadí, ve které byly přidány do dávky.</span><span class="sxs-lookup"><span data-stu-id="a6c48-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="a6c48-144">Chyby jsou zpracovány stejným způsobem v dávkovém režimu, jako jsou zakázány dávkovém režimu.</span><span class="sxs-lookup"><span data-stu-id="a6c48-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="a6c48-145">Každý řádek je zpracován samostatně.</span><span class="sxs-lookup"><span data-stu-id="a6c48-145">Each row is processed separately.</span></span> <span data-ttu-id="a6c48-146">Pouze řádky, které byly úspěšně zpracovány v databázi <xref:System.Data.DataRow> budou <xref:System.Data.DataTable>aktualizovány v odpovídající v rámci .</span><span class="sxs-lookup"><span data-stu-id="a6c48-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="a6c48-147">Zprostředkovatel dat a databázový server back-end určují, které konstrukce SQL jsou podporovány pro dávkové spuštění.</span><span class="sxs-lookup"><span data-stu-id="a6c48-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="a6c48-148">Výjimka může být vyvolána, pokud je odeslán nepodporovaný příkaz k provedení.</span><span class="sxs-lookup"><span data-stu-id="a6c48-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c48-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6c48-149">See also</span></span>

- [<span data-ttu-id="a6c48-150">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="a6c48-150">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="a6c48-151">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="a6c48-151">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="a6c48-152">Zpracování událostí adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="a6c48-152">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)
- [<span data-ttu-id="a6c48-153">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a6c48-153">ADO.NET Overview</span></span>](ado-net-overview.md)
