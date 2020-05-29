---
title: Parametry s hodnotami v tabulkách
ms.date: 10/12/2018
dev_langs:
- csharp
- vb
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.openlocfilehash: b968c599cf061fbd03b7ba8fb19470f6ace11a55
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202177"
---
# <a name="table-valued-parameters"></a><span data-ttu-id="b2a2c-102">Parametry s hodnotami v tabulkách</span><span class="sxs-lookup"><span data-stu-id="b2a2c-102">Table-Valued Parameters</span></span>
<span data-ttu-id="b2a2c-103">Parametry s hodnotou tabulky poskytují snadný způsob, jak zařadit více řádků dat z klientské aplikace do SQL Server bez vyžadování více zpátečních cest nebo speciální logiky na straně serveru pro zpracování dat.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to SQL Server without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="b2a2c-104">K zapouzdření řádků dat v klientské aplikaci a posílání dat na server v jednom parametrizovaném příkazu můžete použít parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="b2a2c-105">Příchozí datové řádky jsou uloženy v proměnné tabulky, které lze následně provozovat pomocí jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-105">The incoming data rows are stored in a table variable that can then be operated on by using Transact-SQL.</span></span>  
  
 <span data-ttu-id="b2a2c-106">Hodnoty sloupce v parametrech s hodnotou tabulky lze použít jako standardní příkazy SELECT jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-106">Column values in table-valued parameters can be accessed using standard Transact-SQL SELECT statements.</span></span> <span data-ttu-id="b2a2c-107">Parametry s hodnotou tabulky jsou silného typu a jejich struktura je automaticky ověřena.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="b2a2c-108">Velikost parametrů s hodnotou tabulky je omezená jenom na paměť serveru.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2a2c-109">Nelze vrátit data v parametru s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="b2a2c-110">Parametry s hodnotou tabulky jsou pouze vstupní; klíčové slovo OUTPUT není podporováno.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="b2a2c-111">Další informace o parametrech s hodnotou tabulky najdete v následujících zdrojích informací.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="b2a2c-112">Prostředek</span><span class="sxs-lookup"><span data-stu-id="b2a2c-112">Resource</span></span>|<span data-ttu-id="b2a2c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b2a2c-113">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="b2a2c-114">Použití parametrů s hodnotou tabulky (databázový stroj)</span><span class="sxs-lookup"><span data-stu-id="b2a2c-114">Use Table-Valued Parameters (Database Engine)</span></span>](/sql/relational-databases/tables/use-table-valued-parameters-database-engine)|<span data-ttu-id="b2a2c-115">Popisuje, jak vytvořit a použít parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="b2a2c-116">[Uživatelem definované typy tabulek](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="b2a2c-116">[User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100))</span></span>|<span data-ttu-id="b2a2c-117">Popisuje uživatelsky definované typy tabulek, které se používají k deklaraci parametrů s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="b2a2c-118">Předávání více řádků v předchozích verzích SQL Server</span><span class="sxs-lookup"><span data-stu-id="b2a2c-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="b2a2c-119">Než byly zavedeny parametry s hodnotou tabulky SQL Server 2008, byly omezeny možnosti pro předávání více řádků dat do uložené procedury nebo parametrizovaný příkaz SQL.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-119">Before table-valued parameters were introduced to SQL Server 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="b2a2c-120">Vývojář se může rozhodnout z následujících možností pro předávání více řádků serveru:</span><span class="sxs-lookup"><span data-stu-id="b2a2c-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
- <span data-ttu-id="b2a2c-121">Pro reprezentaci hodnot ve více sloupcích a řádcích dat použijte řadu jednotlivých parametrů.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="b2a2c-122">Množství dat, které lze předat pomocí této metody, je omezeno počtem povolených parametrů.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> <span data-ttu-id="b2a2c-123">SQL Server postupy může mít maximálně 2100 parametrů.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-123">SQL Server procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="b2a2c-124">Logika na straně serveru je nutná k sestavení těchto jednotlivých hodnot do proměnné tabulky nebo dočasné tabulky pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
- <span data-ttu-id="b2a2c-125">Seskupit více hodnot dat do řetězců s oddělovači nebo dokumentů XML a pak tyto textové hodnoty předat proceduře nebo příkazu.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="b2a2c-126">K tomu je potřeba, aby procedura nebo příkaz zahrnoval logiku potřebnou k ověřování datových struktur a odstavování hodnot.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
- <span data-ttu-id="b2a2c-127">Vytvořte řadu jednotlivých příkazů SQL pro úpravy dat, které ovlivňují více řádků, například ty, které byly vytvořeny voláním `Update` metody typu <xref:System.Data.SqlClient.SqlDataAdapter> .</span><span class="sxs-lookup"><span data-stu-id="b2a2c-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="b2a2c-128">Změny je možné odeslat na server jednotlivě nebo do skupin v dávce.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="b2a2c-129">Nicméně i v případě odeslání v dávkách, které obsahují více příkazů, každý příkaz je proveden samostatně na serveru.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
- <span data-ttu-id="b2a2c-130">Pomocí `bcp` programu nebo <xref:System.Data.SqlClient.SqlBulkCopy> objektu můžete načíst mnoho řádků dat do tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="b2a2c-131">I když je tato technika velmi efektivní, nepodporuje zpracování na straně serveru, pokud nejsou data načtena do dočasné tabulky nebo proměnné tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="b2a2c-132">Vytváření typů parametrů s hodnotou tabulky</span><span class="sxs-lookup"><span data-stu-id="b2a2c-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="b2a2c-133">Parametry s hodnotou tabulky jsou založené na strukturách tabulek se silnými typy, které jsou definovány pomocí příkazů CREATE-SQL CREATE TYPE.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-133">Table-valued parameters are based on strongly typed table structures that are defined by using Transact-SQL CREATE TYPE statements.</span></span> <span data-ttu-id="b2a2c-134">Aby bylo možné v klientských aplikacích použít parametry s hodnotou tabulky, je třeba vytvořit typ tabulky a definovat strukturu v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-134">You have to create a table type and define the structure in SQL Server before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="b2a2c-135">Další informace o vytváření typů tabulek naleznete v tématu [uživatelsky definované typy tabulek](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span><span class="sxs-lookup"><span data-stu-id="b2a2c-135">For more information about creating table types, see [User-Defined Table Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/bb522526(v=sql.100)).</span></span>  
  
 <span data-ttu-id="b2a2c-136">Následující příkaz vytvoří typ tabulky s názvem CategoryTableType, který se skládá z sloupců KódKategorie a CategoryName:</span><span class="sxs-lookup"><span data-stu-id="b2a2c-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="b2a2c-137">Po vytvoření typu tabulky můžete deklarovat parametry s hodnotou tabulky na základě tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="b2a2c-138">Následující fragment Transact-SQL ukazuje, jak deklarovat parametr s hodnotou tabulky v definici uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-138">The following Transact-SQL fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="b2a2c-139">Všimněte si, že klíčové slovo READONLY je vyžadováno pro deklaraci parametru s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```sql
CREATE PROCEDURE usp_UpdateCategories
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="b2a2c-140">Úprava dat pomocí parametrů s hodnotou tabulky (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b2a2c-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="b2a2c-141">Parametry s hodnotou tabulky lze použít v úpravách dat založených na sadě, které mají vliv na více řádků provedením jednoho příkazu.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="b2a2c-142">Můžete například vybrat všechny řádky v parametru s hodnotou tabulky a vložit je do tabulky databáze, nebo můžete vytvořit příkaz Update připojením parametru s hodnotou tabulky do tabulky, kterou chcete aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="b2a2c-143">Následující příkaz UPDATE jazyka Transact-SQL ukazuje, jak použít parametr s hodnotou tabulky připojením k tabulce categories (kategorie).</span><span class="sxs-lookup"><span data-stu-id="b2a2c-143">The following Transact-SQL UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="b2a2c-144">Když použijete parametr s hodnotou tabulky s SPOJENÍm v klauzuli FROM, musíte ho také aliasovat, jak je znázorněno zde, kde parametr s hodnotou tabulky má alias "ES":</span><span class="sxs-lookup"><span data-stu-id="b2a2c-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="b2a2c-145">Tento příklad Transact-SQL ukazuje, jak vybrat řádky z parametru s hodnotou tabulky k provedení vložení v rámci jedné operace založené na sadě.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-145">This Transact-SQL example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="b2a2c-146">Omezení parametrů s hodnotou tabulky</span><span class="sxs-lookup"><span data-stu-id="b2a2c-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="b2a2c-147">Existují několik omezení pro parametry s hodnotou tabulky:</span><span class="sxs-lookup"><span data-stu-id="b2a2c-147">There are several limitations to table-valued parameters:</span></span>  
  
- <span data-ttu-id="b2a2c-148">Do [uživatelsky definovaných funkcí CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions)nelze předat parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-148">You cannot pass table-valued parameters to [CLR user-defined functions](/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions).</span></span>  
  
- <span data-ttu-id="b2a2c-149">Parametry s hodnotou tabulky můžou být indexované jenom pro podporu omezení UNIQUE nebo PRIMARY KEY.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> <span data-ttu-id="b2a2c-150">SQL Server neudržuje statistiku pro parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-150">SQL Server does not maintain statistics on table-valued parameters.</span></span>  
  
- <span data-ttu-id="b2a2c-151">Parametry s hodnotou tabulky jsou jen pro čtení v kódu Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-151">Table-valued parameters are read-only in Transact-SQL code.</span></span> <span data-ttu-id="b2a2c-152">Hodnoty sloupce nelze aktualizovat v řádcích parametru s hodnotou tabulky a nelze vkládat ani odstraňovat řádky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="b2a2c-153">Chcete-li upravit data předávaná do uložené procedury nebo parametrizovaného příkazu v parametru s hodnotou tabulky, je nutné vložit data do dočasné tabulky nebo do proměnné tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
- <span data-ttu-id="b2a2c-154">Pomocí příkazů ALTER TABLE nelze upravovat návrh parametrů s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="b2a2c-155">Příklad konfigurace SqlParameter</span><span class="sxs-lookup"><span data-stu-id="b2a2c-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="b2a2c-156"><xref:System.Data.SqlClient>podporuje zaplňování parametrů s hodnotou tabulky <xref:System.Data.DataTable> z <xref:System.Data.Common.DbDataReader> nebo <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="b2a2c-157">Je nutné zadat název typu pro parametr s hodnotou tabulky pomocí <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnosti <xref:System.Data.SqlClient.SqlParameter> .</span><span class="sxs-lookup"><span data-stu-id="b2a2c-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="b2a2c-158">Se `TypeName` musí shodovat s názvem kompatibilního typu, který byl dříve vytvořen na serveru.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="b2a2c-159">Následující fragment kódu ukazuje, jak konfigurovat <xref:System.Data.SqlClient.SqlParameter> pro vkládání dat.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  

<span data-ttu-id="b2a2c-160">V následujícím příkladu `addedCategories` proměnná obsahuje <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="b2a2c-160">In the following example, the `addedCategories` variable contains a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="b2a2c-161">Chcete-li zjistit, jak je proměnná naplněna, přečtěte si příklady v následující části, [předáním parametru s hodnotou tabulky do uložené procedury](#passing).</span><span class="sxs-lookup"><span data-stu-id="b2a2c-161">To see how the variable is populated, see the examples in the next section, [Passing a Table-Valued Parameter to a Stored Procedure](#passing).</span></span>

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
  
 <span data-ttu-id="b2a2c-162">Můžete také použít libovolný objekt odvozený z <xref:System.Data.Common.DbDataReader> pro streamování řádků dat do parametru s hodnotou tabulky, jak je znázorněno v tomto fragmentu:</span><span class="sxs-lookup"><span data-stu-id="b2a2c-162">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><a name="passing"></a><span data-ttu-id="b2a2c-163">Předání parametru s hodnotou tabulky do uložené procedury</span><span class="sxs-lookup"><span data-stu-id="b2a2c-163">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="b2a2c-164">Tento příklad ukazuje, jak předat data parametrů s hodnotou tabulky do uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-164">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="b2a2c-165">Kód extrahuje přidané řádky do nového <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.GetChanges%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-165">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="b2a2c-166">Kód pak definuje a <xref:System.Data.SqlClient.SqlCommand> nastaví <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> vlastnost na hodnotu <xref:System.Data.CommandType.StoredProcedure> .</span><span class="sxs-lookup"><span data-stu-id="b2a2c-166">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="b2a2c-167"><xref:System.Data.SqlClient.SqlParameter>Hodnota je naplněna pomocí <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> metody a <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> je nastavena na `Structured` .</span><span class="sxs-lookup"><span data-stu-id="b2a2c-167">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="b2a2c-168"><xref:System.Data.SqlClient.SqlCommand>Pak se spustí pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-168">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="b2a2c-169">Předání parametru s hodnotou tabulky do parametrizovaného příkazu jazyka SQL</span><span class="sxs-lookup"><span data-stu-id="b2a2c-169">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="b2a2c-170">Následující příklad ukazuje, jak vložit data do databáze dbo. Tabulka kategorií pomocí příkazu INSERT s VÝBĚROVÝm poddotazem, který má parametr s hodnotou tabulky jako zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-170">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="b2a2c-171">Při předání parametru s hodnotou tabulky do parametrizovaného příkazu jazyka SQL je nutné zadat název typu pro parametr s hodnotou tabulky pomocí <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnosti New třídy <xref:System.Data.SqlClient.SqlParameter> .</span><span class="sxs-lookup"><span data-stu-id="b2a2c-171">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="b2a2c-172">Ta `TypeName` se musí shodovat s názvem kompatibilního typu dříve vytvořeným na serveru.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-172">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="b2a2c-173">Kód v tomto příkladu používá `TypeName` vlastnost k odkazování na strukturu typu definovanou v dbo. CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-173">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2a2c-174">Pokud zadáte hodnotu pro sloupec identity v parametru s hodnotou tabulky, je nutné vystavit příkaz SET IDENTITY_INSERT pro relaci.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-174">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="b2a2c-175">Streamování řádků pomocí objektu DataReader</span><span class="sxs-lookup"><span data-stu-id="b2a2c-175">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="b2a2c-176">Můžete také použít libovolný objekt odvozený z <xref:System.Data.Common.DbDataReader> pro streamování řádků dat do parametru s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-176">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="b2a2c-177">Následující fragment kódu ukazuje, jak načíst data z databáze Oracle pomocí <xref:System.Data.OracleClient.OracleCommand> a <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="b2a2c-177">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="b2a2c-178">Kód pak nakonfiguruje, <xref:System.Data.SqlClient.SqlCommand> aby vyvolal uloženou proceduru s jedním vstupním parametrem.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-178">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="b2a2c-179"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A>Vlastnost <xref:System.Data.SqlClient.SqlParameter> je nastavena na hodnotu `Structured` .</span><span class="sxs-lookup"><span data-stu-id="b2a2c-179">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="b2a2c-180"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> `OracleDataReader` Nastaví výsledek sady výsledků na uloženou proceduru jako parametr s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2a2c-180">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b2a2c-181">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2a2c-181">See also</span></span>

- [<span data-ttu-id="b2a2c-182">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="b2a2c-182">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="b2a2c-183">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="b2a2c-183">Commands and Parameters</span></span>](../commands-and-parameters.md)
- [<span data-ttu-id="b2a2c-184">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="b2a2c-184">DataAdapter Parameters</span></span>](../dataadapter-parameters.md)
- [<span data-ttu-id="b2a2c-185">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b2a2c-185">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="b2a2c-186">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b2a2c-186">ADO.NET Overview</span></span>](../ado-net-overview.md)
