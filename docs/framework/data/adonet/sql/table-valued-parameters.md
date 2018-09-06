---
title: Parametry Table-Valued
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: 333154f26a575886f19a914ce2f91beebd6be49e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742514"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="d48ec-102">Parametry Table-Valued</span><span class="sxs-lookup"><span data-stu-id="d48ec-102">Table-Valued Parameters</span></span>
<span data-ttu-id="d48ec-103">Parametry s hodnotou tabulky poskytují snadný způsob, jak zařadit více řádků dat z klientské aplikace k SQL serveru bez nutnosti více výměn nebo zvláštní logiku na straně serveru pro zpracování dat.</span><span class="sxs-lookup"><span data-stu-id="d48ec-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="d48ec-104">Parametry table-valued můžete použít k zapouzdření řádky dat v aplikaci klienta a odesílání dat na server v jedné parametrizovaného příkazu.</span><span class="sxs-lookup"><span data-stu-id="d48ec-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="d48ec-105">Řádky příchozích dat jsou uložené v proměnné tabulky, který může pak být provozována pomocí [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d48ec-105">The incoming data rows are stored in a table variable that can then be operated on by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="d48ec-106">Hodnoty sloupců v parametrů table-valued lze přistupovat pomocí standardní [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazů SELECT.</span><span class="sxs-lookup"><span data-stu-id="d48ec-106">Column values in table-valued parameters can be accessed using standard [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT statements.</span></span> <span data-ttu-id="d48ec-107">Parametry Table-valued jsou silného typu a jejich strukturu se automaticky ověří.</span><span class="sxs-lookup"><span data-stu-id="d48ec-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="d48ec-108">Velikost parametrů table-valued je omezena pouze paměť serveru.</span><span class="sxs-lookup"><span data-stu-id="d48ec-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d48ec-109">Nelze vrátit data v parametru s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="d48ec-110">Parametry Table-valued jsou výhradně; VÝSTUP – klíčové slovo se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="d48ec-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="d48ec-111">Další informace o parametry table-valued najdete v následující prostředky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="d48ec-112">Prostředek</span><span class="sxs-lookup"><span data-stu-id="d48ec-112">Resource</span></span>|<span data-ttu-id="d48ec-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d48ec-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d48ec-114">[Parametry Table-Valued (databázový stroj)](https://go.microsoft.com/fwlink/?LinkId=98363) v Online knihách serveru SQL</span><span class="sxs-lookup"><span data-stu-id="d48ec-114">[Table-Valued Parameters (Database Engine)](https://go.microsoft.com/fwlink/?LinkId=98363) in SQL Server Books Online</span></span>|<span data-ttu-id="d48ec-115">Popisuje, jak vytvořit a používat parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="d48ec-116">[Uživatelem definované typy tabulek](https://go.microsoft.com/fwlink/?LinkId=98364) v Online knihách serveru SQL</span><span class="sxs-lookup"><span data-stu-id="d48ec-116">[User-Defined Table Types](https://go.microsoft.com/fwlink/?LinkId=98364) in SQL Server Books Online</span></span>|<span data-ttu-id="d48ec-117">Popisuje uživatele definovaných typů tabulek, které se používají k deklarování parametrů table-valued.</span><span class="sxs-lookup"><span data-stu-id="d48ec-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="d48ec-118">Předání více řádků v předchozích verzích systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="d48ec-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="d48ec-119">Předtím, než se seznámili s parametry table-valued systému SQL Server 2008, byly omezené možnosti pro předání více řádků dat uložené procedury nebo parametrizovaného příkazu SQL.</span><span class="sxs-lookup"><span data-stu-id="d48ec-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="d48ec-120">Vývojář může zvolit jednu z následujících možností pro předání více řádků na server:</span><span class="sxs-lookup"><span data-stu-id="d48ec-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
-   <span data-ttu-id="d48ec-121">K reprezentaci hodnoty do více sloupců a řádků dat použijte řadu jednotlivé parametry.</span><span class="sxs-lookup"><span data-stu-id="d48ec-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="d48ec-122">Množství dat, které mohou být předány tímto způsobem je omezen počet povolených parametrů.</span><span class="sxs-lookup"><span data-stu-id="d48ec-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="d48ec-123">Postupy pro SQL Server může mít maximálně 2100 parametry.</span><span class="sxs-lookup"><span data-stu-id="d48ec-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="d48ec-124">Je potřeba sestavit tyto jednotlivé hodnoty do proměnné tabulky nebo dočasná tabulka pro zpracování logiky na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="d48ec-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
-   <span data-ttu-id="d48ec-125">Vytvoření balíčku více hodnot dat do řetězce s oddělovači nebo dokumentů XML a předat tyto hodnoty text do procedury nebo příkaz.</span><span class="sxs-lookup"><span data-stu-id="d48ec-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="d48ec-126">To vyžaduje procedury nebo prohlášení přidat logiku potřebnou pro ověření datových struktur a zpřístupnění hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d48ec-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
-   <span data-ttu-id="d48ec-127">Vytvořte řadu jednotlivých příkazů SQL pro změny dat, které ovlivňují více řádků, jako jsou ty voláním `Update` metodu <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="d48ec-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="d48ec-128">Změny můžete odeslat na server samostatně nebo v dávce do skupin.</span><span class="sxs-lookup"><span data-stu-id="d48ec-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="d48ec-129">Ale i v případě, že odešle v dávkách, které obsahují více příkazů, každý příkaz je proveden odděleně na serveru.</span><span class="sxs-lookup"><span data-stu-id="d48ec-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
-   <span data-ttu-id="d48ec-130">Použití `bcp` nástroj nebo <xref:System.Data.SqlClient.SqlBulkCopy> objektu, který chcete načíst počet řádků dat do tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="d48ec-131">I když tato technika je velmi efektivní, nepodporuje zpracování na straně serveru, pokud načtení dat do dočasné tabulky nebo proměnné tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="d48ec-132">Vytváření typů Table-Valued Parameter</span><span class="sxs-lookup"><span data-stu-id="d48ec-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="d48ec-133">Parametry Table-valued jsou založené na tabulce silného typu struktury, které jsou definovány pomocí [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy CREATE TYPE.</span><span class="sxs-lookup"><span data-stu-id="d48ec-133">Table-valued parameters are based on strongly-typed table structures that are defined by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE statements.</span></span> <span data-ttu-id="d48ec-134">Budete muset vytvořit tabulku typu a definují strukturu v systému SQL Server, abyste mohli používat parametry table-valued v klientských aplikacích.</span><span class="sxs-lookup"><span data-stu-id="d48ec-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="d48ec-135">Další informace o vytváření typů tabulek, naleznete v tématu [uživatelem definované typy tabulek](https://go.microsoft.com/fwlink/?LinkID=98364) v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="d48ec-135">For more information about creating table types, see [User-Defined Table Types](https://go.microsoft.com/fwlink/?LinkID=98364) in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="d48ec-136">Následující příkaz vytvoří typ tabulky s názvem CategoryTableType, který se skládá z ID kategorie a CategoryName sloupce:</span><span class="sxs-lookup"><span data-stu-id="d48ec-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="d48ec-137">Jakmile vytvoříte typ tabulky, je možné deklarovat parametry s hodnotou tabulky na základě tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="d48ec-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="d48ec-138">Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment ukazuje, jak deklarovat parametr s hodnotou tabulky v definici uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="d48ec-138">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="d48ec-139">Všimněte si, že READONLY – klíčové slovo je vyžadována pro deklarování parametr s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="d48ec-140">Úpravy dat s parametry Table-Valued (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d48ec-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="d48ec-141">Parametry s hodnotou tabulky je možné v změny založeným na set dat, které ovlivňují více řádků pomocí provádí jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="d48ec-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="d48ec-142">Například můžete vybrat všechny řádky v parametru s hodnotou tabulky a vložení do tabulky databáze, nebo vytvoříte příkazu update spojením parametr s hodnotou tabulky do tabulky, kterou chcete aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="d48ec-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="d48ec-143">Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazu UPDATE ukazuje, jak se pomocí připojení k tabulce kategorie parametr s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-143">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="d48ec-144">Pokud použijete parametr s hodnotou tabulky s spojení v klauzuli FROM, musíte mít také alias, jak je znázorněno zde, kde parametr s hodnotou tabulky je alias jako "ES":</span><span class="sxs-lookup"><span data-stu-id="d48ec-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="d48ec-145">To [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příklad ukazuje, jak pro výběr řádků z parametru s hodnotou tabulky provést vložení v rámci jedné operace založeným na set.</span><span class="sxs-lookup"><span data-stu-id="d48ec-145">This [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="d48ec-146">Omezení parametrů Table-Valued</span><span class="sxs-lookup"><span data-stu-id="d48ec-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="d48ec-147">Existují některá omezení pro parametry s hodnotou tabulky:</span><span class="sxs-lookup"><span data-stu-id="d48ec-147">There are several limitations to table-valued parameters:</span></span>  
  
-   <span data-ttu-id="d48ec-148">Nelze předat parametry s hodnotou tabulky [uživatelem definované funkce CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span><span class="sxs-lookup"><span data-stu-id="d48ec-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
-   <span data-ttu-id="d48ec-149">Parametry s hodnotou tabulky je možné indexovat pouze pro podporu omezení UNIQUE a PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="d48ec-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="d48ec-150">SQL Server nespravuje statistiky pro parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
-   <span data-ttu-id="d48ec-151">Parametry Table-valued jsou jen pro čtení v [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kódu.</span><span class="sxs-lookup"><span data-stu-id="d48ec-151">Table-valued parameters are read-only in [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="d48ec-152">Hodnoty sloupce na řádky parametr s hodnotou tabulky nelze aktualizovat, a nelze vložit nebo odstranit řádky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="d48ec-153">Pokud chcete upravit data, která je předána uloženou proceduru nebo příkaz v parametr s hodnotou tabulky s parametry, je nutné vložit data do dočasné tabulky nebo do proměnné tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
-   <span data-ttu-id="d48ec-154">Pomocí příkazů ALTER TABLE nelze použít k úpravě návrhu parametrů table-valued.</span><span class="sxs-lookup"><span data-stu-id="d48ec-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="d48ec-155">Konfigurace příklad SqlParameter</span><span class="sxs-lookup"><span data-stu-id="d48ec-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="d48ec-156"><xref:System.Data.SqlClient> podporuje sestavování parametrů table-valued z <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> nebo <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="d48ec-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="d48ec-157">Musíte zadat název typu pro parametr s hodnotou tabulky s použitím <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="d48ec-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="d48ec-158">`TypeName` Musí odpovídat názvu kompatibilního typu dříve vytvořené na serveru.</span><span class="sxs-lookup"><span data-stu-id="d48ec-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="d48ec-159">Následující fragment kódu ukazuje, jak nakonfigurovat <xref:System.Data.SqlClient.SqlParameter> vložit data.</span><span class="sxs-lookup"><span data-stu-id="d48ec-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
  
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
  
 <span data-ttu-id="d48ec-160">Můžete také použít jakéhokoli objektu odvozeného od <xref:System.Data.Common.DbDataReader> pro datový proud řádky dat na parametr s hodnotou tabulky, jak je znázorněno v tomto fragmentu:</span><span class="sxs-lookup"><span data-stu-id="d48ec-160">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><span data-ttu-id="d48ec-161">Předání parametru s hodnotou tabulky uložené procedury</span><span class="sxs-lookup"><span data-stu-id="d48ec-161">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="d48ec-162">Tento příklad ukazuje, jak předat parametr s hodnotou tabulky data pro uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="d48ec-162">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="d48ec-163">Kód extrahuje přidání řádků do nového <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.GetChanges%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d48ec-163">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="d48ec-164">Kód poté definuje <xref:System.Data.SqlClient.SqlCommand>a nastavte <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> vlastnost <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="d48ec-164">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="d48ec-165"><xref:System.Data.SqlClient.SqlParameter> Naplněn pomocí <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> metoda a <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> je nastavena na `Structured`.</span><span class="sxs-lookup"><span data-stu-id="d48ec-165">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="d48ec-166"><xref:System.Data.SqlClient.SqlCommand> Je pak provést pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d48ec-166">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="d48ec-167">Předávání Table-Valued Parameter parametrizovaného dotazu SQL příkaz</span><span class="sxs-lookup"><span data-stu-id="d48ec-167">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="d48ec-168">Následující příklad ukazuje, jak vložit data do vlastníka. Tabulky kategorií pomocí příkazu INSERT SELECT poddotazu, která má parametr s hodnotou tabulky jako zdroje dat</span><span class="sxs-lookup"><span data-stu-id="d48ec-168">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="d48ec-169">Při předávání parametru s hodnotou tabulky parametrizovaného příkazu SQL, musíte zadat název typu pro parametr s hodnotou tabulky s použitím nového <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="d48ec-169">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="d48ec-170">To `TypeName` musí odpovídat názvu kompatibilního typu dříve vytvořené na serveru.</span><span class="sxs-lookup"><span data-stu-id="d48ec-170">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="d48ec-171">Kód v tomto příkladu používá `TypeName` vlastnost odkazovat na typ struktury definované v dbo. CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="d48ec-171">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d48ec-172">Pokud zadáte hodnotu pro sloupec identity v parametru s hodnotou tabulky, musíte vydat příkaz IDENTITY_INSERT NASTAVENA pro relaci.</span><span class="sxs-lookup"><span data-stu-id="d48ec-172">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="d48ec-173">Streamování řádků pomocí čtečky dat</span><span class="sxs-lookup"><span data-stu-id="d48ec-173">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="d48ec-174">Můžete také použít jakéhokoli objektu odvozeného od <xref:System.Data.Common.DbDataReader> pro datový proud řádky dat na parametr s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-174">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="d48ec-175">Následující fragment kódu ukazuje, načítání dat z databáze Oracle pomocí <xref:System.Data.OracleClient.OracleCommand> a <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d48ec-175">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="d48ec-176">Kód poté konfiguruje <xref:System.Data.SqlClient.SqlCommand> vyvolat uloženou proceduru s jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="d48ec-176">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="d48ec-177"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Vlastnost <xref:System.Data.SqlClient.SqlParameter> je nastavena na `Structured`.</span><span class="sxs-lookup"><span data-stu-id="d48ec-177">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="d48ec-178"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Předává `OracleDataReader` sadu výsledků pro uloženou proceduru jako parametr s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="d48ec-178">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d48ec-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="d48ec-179">See Also</span></span>  
 [<span data-ttu-id="d48ec-180">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="d48ec-180">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="d48ec-181">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="d48ec-181">Commands and Parameters</span></span>](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="d48ec-182">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="d48ec-182">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="d48ec-183">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d48ec-183">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="d48ec-184">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="d48ec-184">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
