---
title: "Povolení více aktivních sad"
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
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0235a63a24f81968718d526ff676b023c060b9a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="96616-102">Povolení více aktivních sad</span><span class="sxs-lookup"><span data-stu-id="96616-102">Enabling Multiple Active Result Sets</span></span>
<span data-ttu-id="96616-103">Několik sad Active výsledek (MARS) je funkce, která spolupracuje se serverem SQL Server k provádění více jednoho připojení.</span><span class="sxs-lookup"><span data-stu-id="96616-103">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="96616-104">Pokud MARS je povoleno pro použití se systémem SQL Server, přidá každý objekt příkazu používá relaci připojení.</span><span class="sxs-lookup"><span data-stu-id="96616-104">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96616-105">Jedné relace MARS otevře jedno logické připojení pro MARS používat a pak jedno logické připojení u každého příkazu aktivní.</span><span class="sxs-lookup"><span data-stu-id="96616-105">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="96616-106">Povolení a zakázání MARS v připojovacím řetězci</span><span class="sxs-lookup"><span data-stu-id="96616-106">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96616-107">Následující připojovací řetězce použijte ukázku, která **AdventureWorks** databáze je součástí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96616-107">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="96616-108">Připojovací řetězce zadaná předpokládá, že je databáze nainstalována na serveru s názvem MSSQL1.</span><span class="sxs-lookup"><span data-stu-id="96616-108">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="96616-109">Upravte připojovací řetězec v případě potřeby pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="96616-109">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="96616-110">Funkci MARS se ve výchozím nastavení vypnutá.</span><span class="sxs-lookup"><span data-stu-id="96616-110">The MARS feature is disabled by default.</span></span> <span data-ttu-id="96616-111">Může být povoleno přidáním "MultipleActiveResultSets = True" dvojici – klíčové slovo připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="96616-111">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="96616-112">"True" je jedinou platnou hodnotou pro povolení MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-112">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="96616-113">Následující příklad ukazuje, jak se připojit k instanci systému SQL Server a určení, že by měla být povolená MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-113">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 <span data-ttu-id="96616-114">Můžete zakázat MARS přidáním "MultipleActiveResultSets = False" dvojici – klíčové slovo připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="96616-114">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="96616-115">"Nepravda" je jedinou platnou hodnotou pro zakázání MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-115">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="96616-116">Následující připojovací řetězec ukazuje, jak zakázat MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-116">The following connection string demonstrates how to disable MARS.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="96616-117">Zvláštní aspekty při používání MARS</span><span class="sxs-lookup"><span data-stu-id="96616-117">Special Considerations When Using MARS</span></span>  
 <span data-ttu-id="96616-118">Obecně platí stávající aplikace by neměl nutné změny pomocí připojení s MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-118">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="96616-119">Ale pokud chcete používat funkce MARS ve svých aplikacích byste měli porozumět následující zvláštní aspekty.</span><span class="sxs-lookup"><span data-stu-id="96616-119">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="96616-120">Prokládání – příkaz</span><span class="sxs-lookup"><span data-stu-id="96616-120">Statement Interleaving</span></span>  
 <span data-ttu-id="96616-121">Operace MARS synchronně spustit na serveru.</span><span class="sxs-lookup"><span data-stu-id="96616-121">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="96616-122">Příkaz prokládání příkazů vyberte a BULK INSERT je povolen.</span><span class="sxs-lookup"><span data-stu-id="96616-122">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="96616-123">Však jazyk pro manipulaci dat (DML) a příkazy data definition language (DDL) spusťte atomicky.</span><span class="sxs-lookup"><span data-stu-id="96616-123">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="96616-124">Všechny příkazy pokusu provést v době, kdy je prováděna atomic batch jsou zablokované.</span><span class="sxs-lookup"><span data-stu-id="96616-124">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="96616-125">Paralelní provádění na serveru není funkce MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-125">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="96616-126">Pokud dvě dávky se odešlou v části připojení relace MARS, jeden z nich obsahující příkaz SELECT, druhá obsahuje příkaz DML, DML můžete zahájit provádění v rámci provádění příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="96616-126">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="96616-127">Příkaz DML však musíte spustit na dokončení před příkaz SELECT provádět průběh.</span><span class="sxs-lookup"><span data-stu-id="96616-127">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="96616-128">Pokud oba příkazy běží ve stejné transakci, všechny změny provedené příkaz DML po spuštění provádění příkazu SELECT nejsou viditelné pro operace čtení.</span><span class="sxs-lookup"><span data-stu-id="96616-128">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="96616-129">Příkaz WAITFOR uvnitř příkazu SELECT nepřinese transakce, zatímco čeká, to znamená, dokud se vytvářejí na prvním řádku.</span><span class="sxs-lookup"><span data-stu-id="96616-129">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="96616-130">To znamená, že žádné další dávky může spustit v rámci stejné připojení při příkaz WAITFOR čeká.</span><span class="sxs-lookup"><span data-stu-id="96616-130">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="96616-131">Mezipaměť relace MARS</span><span class="sxs-lookup"><span data-stu-id="96616-131">MARS Session Cache</span></span>  
 <span data-ttu-id="96616-132">Po otevření připojení s MARS povoleno se vytvoří relaci logického, přidává další režii.</span><span class="sxs-lookup"><span data-stu-id="96616-132">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="96616-133">Chcete-li minimalizovat režijní náklady a zvýšit výkon, **SqlClient** ukládá do mezipaměti v rámci připojení relace MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-133">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="96616-134">Mezipaměť obsahuje maximálně 10 relace MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-134">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="96616-135">Tato hodnota není uživatel upravit.</span><span class="sxs-lookup"><span data-stu-id="96616-135">This value is not user adjustable.</span></span> <span data-ttu-id="96616-136">Pokud bude dosažen limit relace, je vytvořit novou relaci – není generována chyba.</span><span class="sxs-lookup"><span data-stu-id="96616-136">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="96616-137">Mezipaměť a relací, které v ní jsou připojení; že nejsou sdílená mezi připojení.</span><span class="sxs-lookup"><span data-stu-id="96616-137">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="96616-138">Po vydání relaci, se vrátí do fondu pokud bylo dosaženo horní limit fondu.</span><span class="sxs-lookup"><span data-stu-id="96616-138">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="96616-139">Pokud fond mezipaměti je plná, relace je zavřený.</span><span class="sxs-lookup"><span data-stu-id="96616-139">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="96616-140">Platnost MARS relací.</span><span class="sxs-lookup"><span data-stu-id="96616-140">MARS sessions do not expire.</span></span> <span data-ttu-id="96616-141">Že jsou pouze vyčistit při uvolnění objekt připojení.</span><span class="sxs-lookup"><span data-stu-id="96616-141">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="96616-142">Mezipaměť relace MARS není předem načtena.</span><span class="sxs-lookup"><span data-stu-id="96616-142">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="96616-143">Načte se jako aplikace vyžaduje více relací.</span><span class="sxs-lookup"><span data-stu-id="96616-143">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="96616-144">Bezpečnost vlákna</span><span class="sxs-lookup"><span data-stu-id="96616-144">Thread Safety</span></span>  
 <span data-ttu-id="96616-145">Operace MARS nejsou bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="96616-145">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="96616-146">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="96616-146">Connection Pooling</span></span>  
 <span data-ttu-id="96616-147">MARS povoleno připojení jsou ve fondu, podobně jako jakékoli jiné připojení.</span><span class="sxs-lookup"><span data-stu-id="96616-147">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="96616-148">Pokud aplikace otevře dvě připojení, jeden s MARS povolené a jeden s MARS zakázáno, jsou dvě připojení v samostatné fondy.</span><span class="sxs-lookup"><span data-stu-id="96616-148">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="96616-149">Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="96616-149">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="96616-150">Prostředí pro spuštění dávky SQL serveru</span><span class="sxs-lookup"><span data-stu-id="96616-150">SQL Server Batch Execution Environment</span></span>  
 <span data-ttu-id="96616-151">Po otevření připojení je definován výchozí prostředí.</span><span class="sxs-lookup"><span data-stu-id="96616-151">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="96616-152">Toto prostředí poté zkopíruje do logické relace MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-152">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="96616-153">Prostředí pro spuštění dávky zahrnuje následující součásti:</span><span class="sxs-lookup"><span data-stu-id="96616-153">The batch execution environment includes the following components:</span></span>  
  
-   <span data-ttu-id="96616-154">Nastavení možností (například ANSI_NULLS, DATE_FORMAT, jazyka, velikost textu)</span><span class="sxs-lookup"><span data-stu-id="96616-154">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
-   <span data-ttu-id="96616-155">Kontext zabezpečení (role uživatele nebo aplikace)</span><span class="sxs-lookup"><span data-stu-id="96616-155">Security context (user/application role)</span></span>  
  
-   <span data-ttu-id="96616-156">Kontext databáze (aktuální databázi)</span><span class="sxs-lookup"><span data-stu-id="96616-156">Database context (current database)</span></span>  
  
-   <span data-ttu-id="96616-157">Proměnné stavu spuštění (například @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="96616-157">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
-   <span data-ttu-id="96616-158">Nejvyšší úrovně dočasných tabulek</span><span class="sxs-lookup"><span data-stu-id="96616-158">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="96616-159">S MARS je přidružena k připojení k prostředí pro spouštění výchozí.</span><span class="sxs-lookup"><span data-stu-id="96616-159">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="96616-160">Každých nové dávky, která spustí provádění v rámci dané připojení obdrží kopii výchozího prostředí.</span><span class="sxs-lookup"><span data-stu-id="96616-160">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="96616-161">Při každém spuštění kódu v rámci dané batch, všechny změny provedené v prostředí jsou omezená na určité dávky.</span><span class="sxs-lookup"><span data-stu-id="96616-161">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="96616-162">Po dokončení provádění, nastavení spuštění se zkopírují do výchozího prostředí.</span><span class="sxs-lookup"><span data-stu-id="96616-162">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="96616-163">V případě jedné dávkové vydání několik příkazů postupně provést v rámci stejné transakci sémantika je stejná jako ta, vystavené připojení zahrnující starších klientů nebo serverů.</span><span class="sxs-lookup"><span data-stu-id="96616-163">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="96616-164">Paralelní provádění</span><span class="sxs-lookup"><span data-stu-id="96616-164">Parallel Execution</span></span>  
 <span data-ttu-id="96616-165">MARS nebyla navržena pro odebrat všechny požadavky pro víc připojení v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="96616-165">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="96616-166">Pokud aplikace potřebuje true paralelní provádění příkazů na serveru, je třeba použít víc připojení.</span><span class="sxs-lookup"><span data-stu-id="96616-166">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="96616-167">Představte si třeba následující scénář.</span><span class="sxs-lookup"><span data-stu-id="96616-167">For example, consider the following scenario.</span></span> <span data-ttu-id="96616-168">Dva objekty příkaz se vytvoření, jeden pro zpracování je sada výsledků dotazu a druhý pro aktualizace dat; sdílejí společné připojení prostřednictvím MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-168">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="96616-169">V tomto scénáři `Transaction`.`Commit`</span><span class="sxs-lookup"><span data-stu-id="96616-169">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="96616-170">na aktualizaci selhávat, dokud se všechny výsledky byly načteny na první objekt příkazu je následující výjimky:</span><span class="sxs-lookup"><span data-stu-id="96616-170">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="96616-171">Zpráva: Kontext transakce používá jiná relace.</span><span class="sxs-lookup"><span data-stu-id="96616-171">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="96616-172">Zdroj: Zprostředkovatel dat SqlClient .net</span><span class="sxs-lookup"><span data-stu-id="96616-172">Source: .Net SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="96616-173">Očekávané: (null)</span><span class="sxs-lookup"><span data-stu-id="96616-173">Expected: (null)</span></span>  
  
 <span data-ttu-id="96616-174">Přijaté: System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="96616-174">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="96616-175">Existují tři možnosti pro zpracování tento scénář:</span><span class="sxs-lookup"><span data-stu-id="96616-175">There are three options for handling this scenario:</span></span>  
  
1.  <span data-ttu-id="96616-176">Spuštění transakce po vytvoření čtečky tak, že není součástí transakce.</span><span class="sxs-lookup"><span data-stu-id="96616-176">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="96616-177">Každá aktualizace se pak stane vlastní transakce.</span><span class="sxs-lookup"><span data-stu-id="96616-177">Every update then becomes its own transaction.</span></span>  
  
2.  <span data-ttu-id="96616-178">Potvrďte všechny pracovní po zavření čtečky.</span><span class="sxs-lookup"><span data-stu-id="96616-178">Commit all work after the reader is closed.</span></span> <span data-ttu-id="96616-179">To se může pro významné hromadné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="96616-179">This has the potential for a substantial batch of updates.</span></span>  
  
3.  <span data-ttu-id="96616-180">Nepoužívejte MARS; Místo toho pomocí samostatného připojení pro každý objekt příkazu, jako byste před MARS.</span><span class="sxs-lookup"><span data-stu-id="96616-180">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="96616-181">Zjišťování MARS podpory</span><span class="sxs-lookup"><span data-stu-id="96616-181">Detecting MARS Support</span></span>  
 <span data-ttu-id="96616-182">Aplikace můžete zkontrolovat pro MARS podporují přečíst `SqlConnection.ServerVersion` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="96616-182">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="96616-183">Hlavní číslo by mělo být 9 pro SQL Server 2005 a 10 pro SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="96616-183">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96616-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="96616-184">See Also</span></span>  
 [<span data-ttu-id="96616-185">Více aktivních sad výsledků (MARS)</span><span class="sxs-lookup"><span data-stu-id="96616-185">Multiple Active Result Sets (MARS)</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [<span data-ttu-id="96616-186">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="96616-186">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
