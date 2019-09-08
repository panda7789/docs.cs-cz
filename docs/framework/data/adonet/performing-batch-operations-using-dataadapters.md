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
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="ba344-102">Provádění dávkových operací pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="ba344-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="ba344-103">Dávková podpora v ADO.NET umožňuje <xref:System.Data.Common.DataAdapter> Seskupit operace vložení, aktualizace a odstranění <xref:System.Data.DataSet> ze serveru nebo <xref:System.Data.DataTable> na server, místo aby bylo možné současně odeslat jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="ba344-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="ba344-104">Snížení počtu zpátečních cest k serveru obvykle vede k výraznému nárůstu výkonu.</span><span class="sxs-lookup"><span data-stu-id="ba344-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="ba344-105">Aktualizace služby Batch jsou podporované pro zprostředkovatele dat .NET pro SQL Server (<xref:System.Data.SqlClient>) a Oracle (<xref:System.Data.OracleClient>).</span><span class="sxs-lookup"><span data-stu-id="ba344-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="ba344-106">Při aktualizaci databáze se změnami z <xref:System.Data.DataSet> verze v předchozích verzích nástroje ADO.NET `Update` Metoda `DataAdapter` provedených aktualizací do databáze po jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="ba344-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="ba344-107">Jak prochází řádky v určeném <xref:System.Data.DataTable>, <xref:System.Data.DataRow> prozkoumali jste je, abyste viděli, zda byla upravena.</span><span class="sxs-lookup"><span data-stu-id="ba344-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="ba344-108">Pokud byl řádek upraven, byl označován jako `UpdateCommand`příslušný, `InsertCommand`nebo `DeleteCommand`v závislosti na hodnotě <xref:System.Data.DataRow.RowState%2A> vlastnosti pro daný řádek.</span><span class="sxs-lookup"><span data-stu-id="ba344-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="ba344-109">Každá aktualizace řádku zahrnovala síťovou zpáteční cestu k databázi.</span><span class="sxs-lookup"><span data-stu-id="ba344-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="ba344-110">Počínaje verzí ADO.NET 2,0 <xref:System.Data.Common.DbDataAdapter> <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> zpřístupňuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ba344-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="ba344-111">`UpdateBatchSize` Nastavení na kladnou celočíselnou hodnotu způsobí, že se aktualizace databáze odešlou jako dávky zadané velikosti.</span><span class="sxs-lookup"><span data-stu-id="ba344-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="ba344-112">Například nastavení na hodnotu `UpdateBatchSize` 10 bude seskupovat 10 samostatných příkazů a odešle je jako jednu dávku.</span><span class="sxs-lookup"><span data-stu-id="ba344-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="ba344-113">Nastavení na hodnotu 0 způsobí, že <xref:System.Data.Common.DataAdapter> bude používat největší velikost dávky, kterou může server zpracovat. `UpdateBatchSize`</span><span class="sxs-lookup"><span data-stu-id="ba344-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="ba344-114">Nastavení na hodnotu 1 zakáže dávkové aktualizace, protože řádky jsou odesílány po jednom.</span><span class="sxs-lookup"><span data-stu-id="ba344-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="ba344-115">Spuštění extrémně velké dávky může snížit výkon.</span><span class="sxs-lookup"><span data-stu-id="ba344-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="ba344-116">Proto byste měli před implementací aplikace otestovat nastavení optimální velikosti dávky.</span><span class="sxs-lookup"><span data-stu-id="ba344-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="ba344-117">Použití vlastnosti UpdateBatchSize</span><span class="sxs-lookup"><span data-stu-id="ba344-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="ba344-118">Pokud jsou <xref:System.Data.IDbCommand.UpdatedRowSource%2A> povoleny aktualizace dávky, hodnota vlastnosti `UpdateCommand`DataAdapter, `InsertCommand`a `DeleteCommand` by měla být nastavena na <xref:System.Data.UpdateRowSource.None> nebo <xref:System.Data.UpdateRowSource.OutputParameters>.</span><span class="sxs-lookup"><span data-stu-id="ba344-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="ba344-119">Při provádění aktualizace dávky je <xref:System.Data.IDbCommand.UpdatedRowSource%2A> <xref:System.Data.UpdateRowSource.FirstReturnedRecord> hodnota vlastnosti příkazu nebo <xref:System.Data.UpdateRowSource.Both> neplatná.</span><span class="sxs-lookup"><span data-stu-id="ba344-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="ba344-120">Následující postup demonstruje použití `UpdateBatchSize` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ba344-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="ba344-121">Procedura přijímá dva argumenty <xref:System.Data.DataSet> , objekt, který má sloupce reprezentující pole **ProductCategoryID** a **Name** v tabulce **produkčního sloupce ProductCategory** a celé číslo představující velikost dávky (počet řádky v dávce).</span><span class="sxs-lookup"><span data-stu-id="ba344-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="ba344-122">Kód vytvoří nový <xref:System.Data.SqlClient.SqlDataAdapter> objekt, nastaví jeho <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>vlastnosti, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>a <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> .</span><span class="sxs-lookup"><span data-stu-id="ba344-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="ba344-123">Kód předpokládá, že <xref:System.Data.DataSet> objekt má změněné řádky.</span><span class="sxs-lookup"><span data-stu-id="ba344-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="ba344-124">Nastaví `UpdateBatchSize` vlastnost a provede aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="ba344-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="ba344-125">Zpracování událostí a chyb souvisejících s aktualizací Batch</span><span class="sxs-lookup"><span data-stu-id="ba344-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="ba344-126">Objekt **DataAdapter** má dvě události související s aktualizací: **RowUpdating** a **RowUpdated metody Update**.</span><span class="sxs-lookup"><span data-stu-id="ba344-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="ba344-127">Pokud je v předchozích verzích ADO.NET zakázané dávkové zpracování, každá z těchto událostí se vygeneruje jednou pro každý zpracovávaný řádek.</span><span class="sxs-lookup"><span data-stu-id="ba344-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="ba344-128">**RowUpdating** se vygeneruje před tím, než dojde k aktualizaci, a po dokončení aktualizace databáze se vygeneruje **RowUpdated metody Update** .</span><span class="sxs-lookup"><span data-stu-id="ba344-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="ba344-129">Změny chování události v dávkových aktualizacích</span><span class="sxs-lookup"><span data-stu-id="ba344-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="ba344-130">Pokud je povoleno dávkové zpracování, v rámci jedné databáze se aktualizuje více řádků.</span><span class="sxs-lookup"><span data-stu-id="ba344-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="ba344-131">Proto se pro každou `RowUpdated` dávku vyvolá jenom jedna událost, `RowUpdating` zatímco pro každý zpracovávaný řádek dojde k události.</span><span class="sxs-lookup"><span data-stu-id="ba344-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="ba344-132">Když je dávkové zpracování zakázané, jsou tyto dvě události vyvolány pomocí prokládání 1:1, kdy jedna `RowUpdating` událost a jedna `RowUpdated` aktivovaná událost pro řádek a pak jedna `RowUpdating` a jedna `RowUpdated` událost pro další řádek, až do všech řádků. jsou zpracovávány.</span><span class="sxs-lookup"><span data-stu-id="ba344-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="ba344-133">Přístup k aktualizovaným řádkům</span><span class="sxs-lookup"><span data-stu-id="ba344-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="ba344-134">Když je dávkové zpracování zakázané, k řádku, který se má aktualizovat, <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> se dá dostat <xref:System.Data.Common.RowUpdatedEventArgs> pomocí vlastnosti třídy.</span><span class="sxs-lookup"><span data-stu-id="ba344-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="ba344-135">Pokud je povoleno dávkové zpracování, je vygenerována jedna `RowUpdated` událost pro více řádků.</span><span class="sxs-lookup"><span data-stu-id="ba344-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="ba344-136">Proto hodnota `Row` vlastnosti pro každý řádek má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ba344-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="ba344-137">`RowUpdating`události jsou stále generovány pro každý řádek.</span><span class="sxs-lookup"><span data-stu-id="ba344-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="ba344-138"><xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Metoda<xref:System.Data.Common.RowUpdatedEventArgs> třídy umožňuje přístup ke zpracovaným řádkům zkopírováním odkazů na řádky do pole.</span><span class="sxs-lookup"><span data-stu-id="ba344-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="ba344-139">Pokud nejsou zpracovávány žádné řádky, `CopyToRows` <xref:System.ArgumentNullException>vyvolá.</span><span class="sxs-lookup"><span data-stu-id="ba344-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="ba344-140">Použijte vlastnost k vrácení počtu zpracovaných řádků před <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> voláním metody. <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A></span><span class="sxs-lookup"><span data-stu-id="ba344-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="ba344-141">Zpracování chyb dat</span><span class="sxs-lookup"><span data-stu-id="ba344-141">Handling Data Errors</span></span>  
 <span data-ttu-id="ba344-142">Dávkové zpracování má stejný účinek jako spuštění každého jednotlivého příkazu.</span><span class="sxs-lookup"><span data-stu-id="ba344-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="ba344-143">Příkazy jsou spouštěny v pořadí, v jakém byly do dávky přidány příkazy.</span><span class="sxs-lookup"><span data-stu-id="ba344-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="ba344-144">Chyby jsou zpracovávány stejným způsobem v dávkovém režimu, protože jsou v režimu dávky zakázané.</span><span class="sxs-lookup"><span data-stu-id="ba344-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="ba344-145">Každý řádek se zpracovává samostatně.</span><span class="sxs-lookup"><span data-stu-id="ba344-145">Each row is processed separately.</span></span> <span data-ttu-id="ba344-146">Pouze řádky, které byly úspěšně zpracovány v databázi, budou aktualizovány v odpovídajícím <xref:System.Data.DataRow> <xref:System.Data.DataTable>rámci.</span><span class="sxs-lookup"><span data-stu-id="ba344-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="ba344-147">Poskytovatel dat a back-end databázový server určují, které konstrukce SQL jsou podporovány pro provádění dávky.</span><span class="sxs-lookup"><span data-stu-id="ba344-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="ba344-148">Výjimka může být vyvolána, pokud je odeslán nepodporovaný příkaz ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="ba344-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba344-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba344-149">See also</span></span>

- [<span data-ttu-id="ba344-150">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="ba344-150">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="ba344-151">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="ba344-151">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="ba344-152">Zpracování událostí adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="ba344-152">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)
- [<span data-ttu-id="ba344-153">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ba344-153">ADO.NET Overview</span></span>](ado-net-overview.md)
