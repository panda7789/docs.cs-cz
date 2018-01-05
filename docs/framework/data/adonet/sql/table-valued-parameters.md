---
title: Parametry s hodnotou tabulky
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
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ce210e1da2002fe599a3703ec90374afba843c3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="table-valued-parameters"></a><span data-ttu-id="dfb13-102">Parametry s hodnotou tabulky</span><span class="sxs-lookup"><span data-stu-id="dfb13-102">Table-Valued Parameters</span></span>
<span data-ttu-id="dfb13-103">Parametry s hodnotou tabulky představují snadný způsob, jak zařazování více řádků dat z klientskou aplikaci, aby [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] bez nutnosti více odezev nebo speciální logiku na straně serveru pro zpracování dat.</span><span class="sxs-lookup"><span data-stu-id="dfb13-103">Table-valued parameters provide an easy way to marshal multiple rows of data from a client application to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] without requiring multiple round trips or special server-side logic for processing the data.</span></span> <span data-ttu-id="dfb13-104">Parametry s hodnotou tabulky můžete použít k zapouzdření řádky dat v aplikaci klienta a odesílání dat na server v jedné parametrizovaného příkazu.</span><span class="sxs-lookup"><span data-stu-id="dfb13-104">You can use table-valued parameters to encapsulate rows of data in a client application and send the data to the server in a single parameterized command.</span></span> <span data-ttu-id="dfb13-105">Příchozí data řádky jsou uložené v proměnné tabulky, která lze poté ho zpracovat. pomocí [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dfb13-105">The incoming data rows are stored in a table variable that can then be operated on by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="dfb13-106">Hodnoty ve sloupcích v parametry s hodnotou tabulky lze přistupovat pomocí standardní [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazů SELECT.</span><span class="sxs-lookup"><span data-stu-id="dfb13-106">Column values in table-valued parameters can be accessed using standard [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] SELECT statements.</span></span> <span data-ttu-id="dfb13-107">Parametry s hodnotou tabulky jsou silného typu a jejich struktura je automaticky ověřit.</span><span class="sxs-lookup"><span data-stu-id="dfb13-107">Table-valued parameters are strongly typed and their structure is automatically validated.</span></span> <span data-ttu-id="dfb13-108">Velikost parametry s hodnotou tabulky je omezena pouze paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="dfb13-108">The size of table-valued parameters is limited only by server memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfb13-109">Parametr s hodnotou tabulky nelze vrátit data.</span><span class="sxs-lookup"><span data-stu-id="dfb13-109">You cannot return data in a table-valued parameter.</span></span> <span data-ttu-id="dfb13-110">Parametry s hodnotou tabulky jsou jenom vstupní; klíčové slovo výstup není podporováno.</span><span class="sxs-lookup"><span data-stu-id="dfb13-110">Table-valued parameters are input-only; the OUTPUT keyword is not supported.</span></span>  
  
 <span data-ttu-id="dfb13-111">Další informace o parametry s hodnotou tabulky najdete v následujících materiálech.</span><span class="sxs-lookup"><span data-stu-id="dfb13-111">For more information about table-valued parameters, see the following resources.</span></span>  
  
|<span data-ttu-id="dfb13-112">Prostředek</span><span class="sxs-lookup"><span data-stu-id="dfb13-112">Resource</span></span>|<span data-ttu-id="dfb13-113">Popis</span><span class="sxs-lookup"><span data-stu-id="dfb13-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="dfb13-114">[Parametry s hodnotou tabulky (databázový stroj)](http://go.microsoft.com/fwlink/?LinkId=98363) v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] zarezervuje Online</span><span class="sxs-lookup"><span data-stu-id="dfb13-114">[Table-Valued Parameters (Database Engine)](http://go.microsoft.com/fwlink/?LinkId=98363) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="dfb13-115">Popisuje, jak vytvořit a používat parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-115">Describes how to create and use table-valued parameters.</span></span>|  
|<span data-ttu-id="dfb13-116">[Uživatelem definované typy tabulky](http://go.microsoft.com/fwlink/?LinkId=98364) v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] zarezervuje Online</span><span class="sxs-lookup"><span data-stu-id="dfb13-116">[User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkId=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online</span></span>|<span data-ttu-id="dfb13-117">Popisuje typy uživatelem definovaná tabulka, které se používá k deklaraci parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-117">Describes user-defined table types that are used to declare table-valued parameters.</span></span>|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a><span data-ttu-id="dfb13-118">Předávání více řádků v předchozích verzích systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="dfb13-118">Passing Multiple Rows in Previous Versions of SQL Server</span></span>  
 <span data-ttu-id="dfb13-119">Předtím, než se seznámili s parametry s hodnotou tabulky [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, možnosti předání více řádků dat do uložené procedury nebo parametrizované příkaz SQL byly omezené.</span><span class="sxs-lookup"><span data-stu-id="dfb13-119">Before table-valued parameters were introduced to [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2008, the options for passing multiple rows of data to a stored procedure or a parameterized SQL command were limited.</span></span> <span data-ttu-id="dfb13-120">Vývojář může zvolit z následujících možností pro předávání více řádků k serveru:</span><span class="sxs-lookup"><span data-stu-id="dfb13-120">A developer could choose from the following options for passing multiple rows to the server:</span></span>  
  
-   <span data-ttu-id="dfb13-121">K reprezentaci hodnoty ve více sloupců a řádků dat použijte řadu jednotlivé parametry.</span><span class="sxs-lookup"><span data-stu-id="dfb13-121">Use a series of individual parameters to represent the values in multiple columns and rows of data.</span></span> <span data-ttu-id="dfb13-122">Množství dat, který může být předán pomocí této metody je omezen počet parametrů, které jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="dfb13-122">The amount of data that can be passed by using this method is limited by the number of parameters allowed.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="dfb13-123">procedury může mít maximálně 2100 parametry.</span><span class="sxs-lookup"><span data-stu-id="dfb13-123"> procedures can have, at most, 2100 parameters.</span></span> <span data-ttu-id="dfb13-124">Je potřeba sestavte tyto jednotlivé hodnoty do proměnné tabulky nebo dočasné tabulky pro zpracování logiky na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="dfb13-124">Server-side logic is required to assemble these individual values into a table variable or a temporary table for processing.</span></span>  
  
-   <span data-ttu-id="dfb13-125">Sady více hodnot dat do odděleného řetězce nebo dokumentů XML a pak předejte tyto hodnoty text do procedury nebo příkaz.</span><span class="sxs-lookup"><span data-stu-id="dfb13-125">Bundle multiple data values into delimited strings or XML documents and then pass those text values to a procedure or statement.</span></span> <span data-ttu-id="dfb13-126">To vyžaduje procedura nebo údajů přidat logiku, která je potřebná pro ověření datové struktury a zpřístupnění hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dfb13-126">This requires the procedure or statement to include the logic necessary for validating the data structures and unbundling the values.</span></span>  
  
-   <span data-ttu-id="dfb13-127">Vytvořit řadu jednotlivé příkazy SQL pro změny dat, které ovlivňují více řádků, jako jsou ty vytvořená voláním `Update` metodu <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="dfb13-127">Create a series of individual SQL statements for data modifications that affect multiple rows, such as those created by calling the `Update` method of a <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="dfb13-128">Změny může být odeslána na server individuálně nebo v dávce do skupin.</span><span class="sxs-lookup"><span data-stu-id="dfb13-128">Changes can be submitted to the server individually or batched into groups.</span></span> <span data-ttu-id="dfb13-129">Ale i v případě, že odeslání v dávkách, které obsahují více příkazů, každý se spustit příkaz samostatně na serveru.</span><span class="sxs-lookup"><span data-stu-id="dfb13-129">However, even when submitted in batches that contain multiple statements, each statement is executed separately on the server.</span></span>  
  
-   <span data-ttu-id="dfb13-130">Použití `bcp` nástroj program nebo <xref:System.Data.SqlClient.SqlBulkCopy> objekt, který chcete načíst počet řádků dat do tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-130">Use the `bcp` utility program or the <xref:System.Data.SqlClient.SqlBulkCopy> object to load many rows of data into a table.</span></span> <span data-ttu-id="dfb13-131">I když tato technika je velmi efektivní, nejsou podporovány serverové zpracování, pokud je načíst data do dočasné tabulky nebo proměnná tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-131">Although this technique is very efficient, it does not support server-side processing unless the data is loaded into a temporary table or table variable.</span></span>  
  
## <a name="creating-table-valued-parameter-types"></a><span data-ttu-id="dfb13-132">Vytváření parametr s hodnotou tabulky typů</span><span class="sxs-lookup"><span data-stu-id="dfb13-132">Creating Table-Valued Parameter Types</span></span>  
 <span data-ttu-id="dfb13-133">Parametry s hodnotou tabulky jsou založené na struktury silného typu tabulky, které jsou definované za použití [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazy CREATE TYPE.</span><span class="sxs-lookup"><span data-stu-id="dfb13-133">Table-valued parameters are based on strongly-typed table structures that are defined by using [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] CREATE TYPE statements.</span></span> <span data-ttu-id="dfb13-134">Budete muset vytvořit typ tabulky a definovat strukturu v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] před parametry s hodnotou tabulky lze použít v klientských aplikacích.</span><span class="sxs-lookup"><span data-stu-id="dfb13-134">You have to create a table type and define the structure in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] before you can use table-valued parameters in your client applications.</span></span> <span data-ttu-id="dfb13-135">Další informace o vytváření typů tabulek najdete v tématu [uživatelem definovaných typů tabulek](http://go.microsoft.com/fwlink/?LinkID=98364) v [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] na webu knihy Online.</span><span class="sxs-lookup"><span data-stu-id="dfb13-135">For more information about creating table types, see [User-Defined Table Types](http://go.microsoft.com/fwlink/?LinkID=98364) in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="dfb13-136">Následující příkaz vytvoří typ tabulky s názvem CategoryTableType, která se skládá z CategoryID a CategoryName sloupce:</span><span class="sxs-lookup"><span data-stu-id="dfb13-136">The following statement creates a table type named CategoryTableType that consists of CategoryID and CategoryName columns:</span></span>  
  
```  
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
 <span data-ttu-id="dfb13-137">Jakmile vytvoříte typ tabulky, je možné deklarovat parametry s hodnotou tabulky na základě tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="dfb13-137">After you create a table type, you can declare table-valued parameters based on that type.</span></span> <span data-ttu-id="dfb13-138">Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment ukazuje, jak lze deklarovat parametr s hodnotou tabulky v definici uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="dfb13-138">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] fragment demonstrates how to declare a table-valued parameter in a stored procedure definition.</span></span> <span data-ttu-id="dfb13-139">Všimněte si, že READONLY – klíčové slovo je vyžadována pro deklarování parametr s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-139">Note that the READONLY keyword is required for declaring a table-valued parameter.</span></span>  
  
```  
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a><span data-ttu-id="dfb13-140">Úprava dat s parametry s hodnotou tabulky (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="dfb13-140">Modifying Data with Table-Valued Parameters (Transact-SQL)</span></span>  
 <span data-ttu-id="dfb13-141">Parametry s hodnotou tabulky lze použít v změny na základě sady dat, které ovlivňují více řádků spuštěním jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="dfb13-141">Table-valued parameters can be used in set-based data modifications that affect multiple rows by executing a single statement.</span></span> <span data-ttu-id="dfb13-142">Například můžete vybrat všechny řádky v parametru s hodnotou tabulky a vložte je do databázové tabulky, nebo můžete vytvořit příkazu update připojení parametr s hodnotou tabulky do tabulky, kterou chcete aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="dfb13-142">For example, you can select all the rows in a table-valued parameter and insert them into a database table, or you can create an update statement by joining a table-valued parameter to the table you want to update.</span></span>  
  
 <span data-ttu-id="dfb13-143">Následující [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příkazu UPDATE ukazuje, jak použít parametr s hodnotou tabulky s připojením k tabulce kategorie.</span><span class="sxs-lookup"><span data-stu-id="dfb13-143">The following [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] UPDATE statement demonstrates how to use a table-valued parameter by joining it to the Categories table.</span></span> <span data-ttu-id="dfb13-144">Pokud použijete parametr s hodnotou tabulky s spojení v klauzuli FROM, musíte také alias, jak je vidět tady, kde parametr s hodnotou tabulky je alias jako "ES":</span><span class="sxs-lookup"><span data-stu-id="dfb13-144">When you use a table-valued parameter with a JOIN in a FROM clause, you must also alias it, as shown here, where the table-valued parameter is aliased as "ec":</span></span>  
  
```  
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
 <span data-ttu-id="dfb13-145">To [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] příklad ukazuje, jak vybírat parametr s hodnotou tabulky k provedení typu vložení v rámci jedné operace založené na sadě řádků.</span><span class="sxs-lookup"><span data-stu-id="dfb13-145">This [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] example demonstrates how to select rows from a table-valued parameter to perform an INSERT in a single set-based operation.</span></span>  
  
```  
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a><span data-ttu-id="dfb13-146">Omezení parametrů s hodnotou tabulky</span><span class="sxs-lookup"><span data-stu-id="dfb13-146">Limitations of Table-Valued Parameters</span></span>  
 <span data-ttu-id="dfb13-147">Existuje několik omezení pro parametry s hodnotou tabulky:</span><span class="sxs-lookup"><span data-stu-id="dfb13-147">There are several limitations to table-valued parameters:</span></span>  
  
-   <span data-ttu-id="dfb13-148">Nelze předat parametry s hodnotou tabulky [uživatelsky definované funkce CLR](http://msdn.microsoft.com/library/ms131077.aspx).</span><span class="sxs-lookup"><span data-stu-id="dfb13-148">You cannot pass table-valued parameters to [CLR user-defined functions](http://msdn.microsoft.com/library/ms131077.aspx).</span></span>  
  
-   <span data-ttu-id="dfb13-149">Parametry s hodnotou tabulky lze indexovat pouze pro podporu omezení JEDINEČNÝ nebo primární klíč.</span><span class="sxs-lookup"><span data-stu-id="dfb13-149">Table-valued parameters can only be indexed to support UNIQUE or PRIMARY KEY constraints.</span></span> [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="dfb13-150">neudržuje statistiky na parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-150"> does not maintain statistics on table-valued parameters.</span></span>  
  
-   <span data-ttu-id="dfb13-151">Parametry s hodnotou tabulky jsou jen pro čtení v [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] kódu.</span><span class="sxs-lookup"><span data-stu-id="dfb13-151">Table-valued parameters are read-only in [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] code.</span></span> <span data-ttu-id="dfb13-152">Hodnoty ve sloupcích v řádcích parametr s hodnotou tabulky nelze aktualizovat, a nelze vložit nebo odstranit řádky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-152">You cannot update the column values in the rows of a table-valued parameter and you cannot insert or delete rows.</span></span> <span data-ttu-id="dfb13-153">Chcete-li upravit data, která je předaný uložené proceduře nebo příkaz v parametru s hodnotou tabulky s parametry, je nutné vložit data do dočasné tabulky nebo do proměnné tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-153">To modify the data that is passed to a stored procedure or parameterized statement in table-valued parameter, you must insert the data into a temporary table or into a table variable.</span></span>  
  
-   <span data-ttu-id="dfb13-154">Pomocí příkazů ALTER TABLE nelze použít k úpravě návrh parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-154">You cannot use ALTER TABLE statements to modify the design of table-valued parameters.</span></span>  
  
## <a name="configuring-a-sqlparameter-example"></a><span data-ttu-id="dfb13-155">Konfigurace SqlParameter příklad</span><span class="sxs-lookup"><span data-stu-id="dfb13-155">Configuring a SqlParameter Example</span></span>  
 <span data-ttu-id="dfb13-156"><xref:System.Data.SqlClient>podporuje naplnění parametry s hodnotou tabulky z <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> nebo <xref:System.Collections.Generic.IEnumerable%601>  \  <xref:Microsoft.SqlServer.Server.SqlDataRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="dfb13-156"><xref:System.Data.SqlClient> supports populating table-valued parameters from <xref:System.Data.DataTable>, <xref:System.Data.Common.DbDataReader> or <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.SqlServer.Server.SqlDataRecord> objects.</span></span> <span data-ttu-id="dfb13-157">Musíte zadat název typu pro parametr s hodnotou tabulky s použitím <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="dfb13-157">You must specify a type name for the table-valued parameter by using the <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="dfb13-158">`TypeName` Musí odpovídat názvu kompatibilní typ vytvořili na serveru.</span><span class="sxs-lookup"><span data-stu-id="dfb13-158">The `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="dfb13-159">Následující fragment kódu ukazuje, jak nakonfigurovat <xref:System.Data.SqlClient.SqlParameter> vložit data.</span><span class="sxs-lookup"><span data-stu-id="dfb13-159">The following code fragment demonstrates how to configure <xref:System.Data.SqlClient.SqlParameter> to insert data.</span></span>  
  
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
  
 <span data-ttu-id="dfb13-160">Můžete také použít libovolného objektu odvozeného z <xref:System.Data.Common.DbDataReader> na datový proud řádky dat do parametr s hodnotou tabulky, jak je uvedené v tomto fragmentu:</span><span class="sxs-lookup"><span data-stu-id="dfb13-160">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter, as shown in this fragment:</span></span>  
  
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
  
## <a name="passing-a-table-valued-parameter-to-a-stored-procedure"></a><span data-ttu-id="dfb13-161">Předání parametru s hodnotou tabulky uložené procedury</span><span class="sxs-lookup"><span data-stu-id="dfb13-161">Passing a Table-Valued Parameter to a Stored Procedure</span></span>  
 <span data-ttu-id="dfb13-162">Tento příklad ukazuje, jak k předávání dat parametr s hodnotou tabulky uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="dfb13-162">This example demonstrates how to pass table-valued parameter data to a stored procedure.</span></span> <span data-ttu-id="dfb13-163">Vyextrahuje přidání řádků do nového <xref:System.Data.DataTable> pomocí <xref:System.Data.DataTable.GetChanges%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="dfb13-163">The code extracts added rows into a new <xref:System.Data.DataTable> by using the <xref:System.Data.DataTable.GetChanges%2A> method.</span></span> <span data-ttu-id="dfb13-164">Kód pak definuje <xref:System.Data.SqlClient.SqlCommand>, nastavení <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> vlastnost <xref:System.Data.CommandType.StoredProcedure>.</span><span class="sxs-lookup"><span data-stu-id="dfb13-164">The code then defines a <xref:System.Data.SqlClient.SqlCommand>, setting the <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> property to <xref:System.Data.CommandType.StoredProcedure>.</span></span> <span data-ttu-id="dfb13-165"><xref:System.Data.SqlClient.SqlParameter> Je vyplněný pomocí <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> metoda a <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> je nastaven na `Structured`.</span><span class="sxs-lookup"><span data-stu-id="dfb13-165">The <xref:System.Data.SqlClient.SqlParameter> is populated by using the <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> method and the <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> is set to `Structured`.</span></span> <span data-ttu-id="dfb13-166"><xref:System.Data.SqlClient.SqlCommand> Se pak spustí pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="dfb13-166">The <xref:System.Data.SqlClient.SqlCommand> is then executed by using the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method.</span></span>  
  
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
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a><span data-ttu-id="dfb13-167">Předání parametru s hodnotou tabulky příkazu parametrizované SQL</span><span class="sxs-lookup"><span data-stu-id="dfb13-167">Passing a Table-Valued Parameter to a Parameterized SQL Statement</span></span>  
 <span data-ttu-id="dfb13-168">Následující příklad ukazuje, jak pro vložení dat do vlastníka. Kategorie tabulky pomocí příkazu INSERT vyberte poddotazu, která má jako zdroj dat pro parametr s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-168">The following example demonstrates how to insert data into the dbo.Categories table by using an INSERT statement with a SELECT subquery that has a table-valued parameter as the data source.</span></span> <span data-ttu-id="dfb13-169">Při předávání parametr s hodnotou tabulky parametrizované příkazu jazyka SQL, musíte zadat název typu pro parametr s hodnotou tabulky pomocí nové <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> vlastnost <xref:System.Data.SqlClient.SqlParameter>.</span><span class="sxs-lookup"><span data-stu-id="dfb13-169">When passing a table-valued parameter to a parameterized SQL statement, you must specify a type name for the table-valued parameter by using the new <xref:System.Data.SqlClient.SqlParameter.TypeName%2A> property of a <xref:System.Data.SqlClient.SqlParameter>.</span></span> <span data-ttu-id="dfb13-170">To `TypeName` musí odpovídat názvu kompatibilní typ vytvořili na serveru.</span><span class="sxs-lookup"><span data-stu-id="dfb13-170">This `TypeName` must match the name of a compatible type previously created on the server.</span></span> <span data-ttu-id="dfb13-171">Kód v tomto příkladu používá `TypeName` vlastnost tak, aby odkazovaly strukturou typů, které jsou definované v dbo. CategoryTableType.</span><span class="sxs-lookup"><span data-stu-id="dfb13-171">The code in this example uses the `TypeName` property to reference the type structure defined in dbo.CategoryTableType.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfb13-172">Pokud zadáte hodnotu pro sloupec identity parametr s hodnotou tabulky, musíte vydat příkaz nastavit možnost identity_insert nastavena pro relaci.</span><span class="sxs-lookup"><span data-stu-id="dfb13-172">If you supply a value for an identity column in a table-valued parameter, you must issue the SET IDENTITY_INSERT statement for the session.</span></span>  
  
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
  
## <a name="streaming-rows-with-a-datareader"></a><span data-ttu-id="dfb13-173">Streamování řádky s DataReader –</span><span class="sxs-lookup"><span data-stu-id="dfb13-173">Streaming Rows with a DataReader</span></span>  
 <span data-ttu-id="dfb13-174">Můžete také použít libovolného objektu odvozeného z <xref:System.Data.Common.DbDataReader> na datový proud řádky dat do parametr s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-174">You can also use any object derived from <xref:System.Data.Common.DbDataReader> to stream rows of data to a table-valued parameter.</span></span> <span data-ttu-id="dfb13-175">Následující fragment kódu ukazuje načítání dat z databáze Oracle pomocí <xref:System.Data.OracleClient.OracleCommand> a <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="dfb13-175">The following code fragment demonstrates retrieving data from an Oracle database by using an <xref:System.Data.OracleClient.OracleCommand> and an <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="dfb13-176">Kód, nakonfiguruje <xref:System.Data.SqlClient.SqlCommand> k vyvolání uložená procedura s jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="dfb13-176">The code then configures a <xref:System.Data.SqlClient.SqlCommand> to invoke a stored procedure with a single input parameter.</span></span> <span data-ttu-id="dfb13-177"><xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> Vlastnost <xref:System.Data.SqlClient.SqlParameter> je nastaven na `Structured`.</span><span class="sxs-lookup"><span data-stu-id="dfb13-177">The <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> property of the <xref:System.Data.SqlClient.SqlParameter> is set to `Structured`.</span></span> <span data-ttu-id="dfb13-178"><xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> Předá `OracleDataReader` sady výsledků uložené procedury jako parametr s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="dfb13-178">The <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> passes the `OracleDataReader` result set to the stored procedure as a table-valued parameter.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dfb13-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="dfb13-179">See Also</span></span>  
 [<span data-ttu-id="dfb13-180">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="dfb13-180">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="dfb13-181">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="dfb13-181">Commands and Parameters</span></span>](../../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="dfb13-182">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="dfb13-182">DataAdapter Parameters</span></span>](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [<span data-ttu-id="dfb13-183">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dfb13-183">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="dfb13-184">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="dfb13-184">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
