---
title: Povolení více aktivních sad výsledků
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 72125be835298218e5445fe1915d6a17f5008bb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148722"
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="212aa-102">Povolení více aktivních sad výsledků</span><span class="sxs-lookup"><span data-stu-id="212aa-102">Enabling Multiple Active Result Sets</span></span>
<span data-ttu-id="212aa-103">Více sad aktivních výsledků (MARS) je funkce, která pracuje s SQL Server povolit provádění více dávek na jedno připojení.</span><span class="sxs-lookup"><span data-stu-id="212aa-103">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="212aa-104">Pokud je mars povolen pro použití se serverem SQL Server, každý použitý objekt příkazu přidá relaci připojení.</span><span class="sxs-lookup"><span data-stu-id="212aa-104">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="212aa-105">Jedna relace MARS otevře jedno logické připojení pro MARS pro použití a pak jedno logické připojení pro každý aktivní příkaz.</span><span class="sxs-lookup"><span data-stu-id="212aa-105">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="212aa-106">Povolení a zakázání marsu v připojovacím řetězci</span><span class="sxs-lookup"><span data-stu-id="212aa-106">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
> <span data-ttu-id="212aa-107">Následující připojovací řetězce používají ukázkovou databázi **AdventureWorks,** která je součástí serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="212aa-107">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="212aa-108">Poskytnuté připojovací řetězce předpokládají, že databáze je nainstalována na serveru s názvem MSSQL1.</span><span class="sxs-lookup"><span data-stu-id="212aa-108">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="212aa-109">Podle potřeby upravte připojovací řetězec pro vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="212aa-109">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="212aa-110">Funkce MARS je ve výchozím nastavení zakázána.</span><span class="sxs-lookup"><span data-stu-id="212aa-110">The MARS feature is disabled by default.</span></span> <span data-ttu-id="212aa-111">To může být povoleno přidáním "MultipleActiveResultSets=True" pár klíčových slov do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="212aa-111">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="212aa-112">"True" je jediná platná hodnota pro povolení MARS.</span><span class="sxs-lookup"><span data-stu-id="212aa-112">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="212aa-113">Následující příklad ukazuje, jak se připojit k instanci SQL Server a jak určit, že MARS by měla být povolena.</span><span class="sxs-lookup"><span data-stu-id="212aa-113">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
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
  
 <span data-ttu-id="212aa-114">Mars můžete zakázat přidáním dvojice klíčových slov MultipleActiveResultSets=False do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="212aa-114">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="212aa-115">"False" je jediná platná hodnota pro zakázání MARS.</span><span class="sxs-lookup"><span data-stu-id="212aa-115">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="212aa-116">Následující připojovací řetězec ukazuje, jak zakázat MARS.</span><span class="sxs-lookup"><span data-stu-id="212aa-116">The following connection string demonstrates how to disable MARS.</span></span>  
  
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
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="212aa-117">Zvláštní aspekty při použití MARS</span><span class="sxs-lookup"><span data-stu-id="212aa-117">Special Considerations When Using MARS</span></span>  
 <span data-ttu-id="212aa-118">Obecně platí, že existující aplikace by neměly vyžadovat úpravy, aby bylo nutné používat připojení s podporou MARS.</span><span class="sxs-lookup"><span data-stu-id="212aa-118">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="212aa-119">Pokud však chcete používat funkce MARS ve vašich aplikacích, měli byste pochopit následující zvláštní aspekty.</span><span class="sxs-lookup"><span data-stu-id="212aa-119">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="212aa-120">Prokládání výkazu</span><span class="sxs-lookup"><span data-stu-id="212aa-120">Statement Interleaving</span></span>  
 <span data-ttu-id="212aa-121">Operace MARS se provádějí synchronně na serveru.</span><span class="sxs-lookup"><span data-stu-id="212aa-121">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="212aa-122">Prokládání příkazů SELECT a BULK INSERT je povoleno.</span><span class="sxs-lookup"><span data-stu-id="212aa-122">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="212aa-123">Příkazy jazyka pro manipulaci s daty (DML) a jazyka definice dat (DDL) se však provádějí atomicky.</span><span class="sxs-lookup"><span data-stu-id="212aa-123">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="212aa-124">Všechny příkazy, které se pokoušejí provést při provádění atomické dávky, jsou blokovány.</span><span class="sxs-lookup"><span data-stu-id="212aa-124">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="212aa-125">Paralelní spuštění na serveru není funkce MARS.</span><span class="sxs-lookup"><span data-stu-id="212aa-125">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="212aa-126">Pokud jsou dvě dávky odeslány v rámci připojení MARS, jeden z nich obsahuje příkaz SELECT, druhý obsahující příkaz DML, DML může zahájit provádění v rámci provádění příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="212aa-126">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="212aa-127">Příkaz DML však musí být spuštěn do dokončení, než může příkaz SELECT dosáhnout pokroku.</span><span class="sxs-lookup"><span data-stu-id="212aa-127">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="212aa-128">Pokud jsou oba příkazy spuštěny v rámci stejné transakce, všechny změny provedené příkazem DML po spuštění příkazu SELECT nejsou viditelné pro operaci čtení.</span><span class="sxs-lookup"><span data-stu-id="212aa-128">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="212aa-129">Příkaz WAITFOR uvnitř příkazu SELECT neposkytuje transakce během čekání, to znamená, dokud není vytvořen první řádek.</span><span class="sxs-lookup"><span data-stu-id="212aa-129">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="212aa-130">To znamená, že žádné jiné dávky lze spustit v rámci stejného připojení při čekání příkazwaitfor.</span><span class="sxs-lookup"><span data-stu-id="212aa-130">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="212aa-131">Mezipaměť relace MARS</span><span class="sxs-lookup"><span data-stu-id="212aa-131">MARS Session Cache</span></span>  
 <span data-ttu-id="212aa-132">Při otevření připojení s povolenou funkcí MARS je vytvořena logická relace, která přidává další režii.</span><span class="sxs-lookup"><span data-stu-id="212aa-132">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="212aa-133">Chcete-li minimalizovat režii a zvýšit výkon, **SqlClient** ukládá relace MARS v rámci připojení.</span><span class="sxs-lookup"><span data-stu-id="212aa-133">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="212aa-134">Mezipaměť obsahuje maximálně 10 relací MARS.</span><span class="sxs-lookup"><span data-stu-id="212aa-134">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="212aa-135">Tato hodnota není uživatelsky nastavitelná.</span><span class="sxs-lookup"><span data-stu-id="212aa-135">This value is not user adjustable.</span></span> <span data-ttu-id="212aa-136">Pokud je dosaženo limitu relace, je vytvořena nová relace – není generována chyba.</span><span class="sxs-lookup"><span data-stu-id="212aa-136">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="212aa-137">Mezipaměť a relace obsažené v něm jsou na připojení; nejsou sdíleny mezi připojeními.</span><span class="sxs-lookup"><span data-stu-id="212aa-137">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="212aa-138">Při uvolnění relace je vrácena do fondu, pokud bylo dosaženo horního limitu fondu.</span><span class="sxs-lookup"><span data-stu-id="212aa-138">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="212aa-139">Pokud je fond mezipamětí plný, relace je uzavřena.</span><span class="sxs-lookup"><span data-stu-id="212aa-139">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="212aa-140">Mars relace nevyprší.</span><span class="sxs-lookup"><span data-stu-id="212aa-140">MARS sessions do not expire.</span></span> <span data-ttu-id="212aa-141">Jsou vyčištěny pouze při uvolnění objektu připojení.</span><span class="sxs-lookup"><span data-stu-id="212aa-141">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="212aa-142">Mezipaměť relace MARS není předinstalována.</span><span class="sxs-lookup"><span data-stu-id="212aa-142">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="212aa-143">Je načten, protože aplikace vyžaduje více relací.</span><span class="sxs-lookup"><span data-stu-id="212aa-143">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="212aa-144">Bezpečnost vlákna</span><span class="sxs-lookup"><span data-stu-id="212aa-144">Thread Safety</span></span>  
 <span data-ttu-id="212aa-145">Operace MARS nejsou bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="212aa-145">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="212aa-146">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="212aa-146">Connection Pooling</span></span>  
 <span data-ttu-id="212aa-147">Připojení s podporou MARS jsou sdružená jako jakékoli jiné připojení.</span><span class="sxs-lookup"><span data-stu-id="212aa-147">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="212aa-148">Pokud aplikace otevře dvě připojení, jedno s povolenou funkcí MARS a jedno se zakázaným marsem, jsou dvě připojení v samostatných fondech.</span><span class="sxs-lookup"><span data-stu-id="212aa-148">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="212aa-149">Další informace naleznete v tématu [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="212aa-149">For more information, see [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="212aa-150">Prostředí pro spuštění dávky serveru SQL Server</span><span class="sxs-lookup"><span data-stu-id="212aa-150">SQL Server Batch Execution Environment</span></span>  
 <span data-ttu-id="212aa-151">Při otevření připojení je definováno výchozí prostředí.</span><span class="sxs-lookup"><span data-stu-id="212aa-151">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="212aa-152">Toto prostředí je pak zkopírováno do logické relace MARS.</span><span class="sxs-lookup"><span data-stu-id="212aa-152">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="212aa-153">Prostředí spuštění dávky zahrnuje následující součásti:</span><span class="sxs-lookup"><span data-stu-id="212aa-153">The batch execution environment includes the following components:</span></span>  
  
- <span data-ttu-id="212aa-154">Nastavit možnosti (například ANSI_NULLS, DATE_FORMAT, JAZYK, VELIKOST TEXTU)</span><span class="sxs-lookup"><span data-stu-id="212aa-154">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
- <span data-ttu-id="212aa-155">Kontext zabezpečení (role uživatele/aplikace)</span><span class="sxs-lookup"><span data-stu-id="212aa-155">Security context (user/application role)</span></span>  
  
- <span data-ttu-id="212aa-156">Kontext databáze (aktuální databáze)</span><span class="sxs-lookup"><span data-stu-id="212aa-156">Database context (current database)</span></span>  
  
- <span data-ttu-id="212aa-157">Proměnné stavu spuštění (například@ERROR@@ROWCOUNT,@FETCH_STATUS @IDENTITY@ , @ @ )</span><span class="sxs-lookup"><span data-stu-id="212aa-157">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
- <span data-ttu-id="212aa-158">Dočasné tabulky nejvyšší úrovně</span><span class="sxs-lookup"><span data-stu-id="212aa-158">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="212aa-159">S MARS výchozí spuštění prostředí je spojena s připojením.</span><span class="sxs-lookup"><span data-stu-id="212aa-159">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="212aa-160">Každá nová dávka, která se spustí v rámci daného připojení, obdrží kopii výchozího prostředí.</span><span class="sxs-lookup"><span data-stu-id="212aa-160">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="212aa-161">Vždy, když je kód spuštěn v rámci dané dávky, všechny změny provedené v prostředí jsou vymezeny na konkrétní dávku.</span><span class="sxs-lookup"><span data-stu-id="212aa-161">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="212aa-162">Po dokončení spuštění jsou nastavení spuštění zkopírovány do výchozího prostředí.</span><span class="sxs-lookup"><span data-stu-id="212aa-162">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="212aa-163">V případě jedné dávky vydávání několik příkazů, které mají být provedeny postupně v rámci stejné transakce, sémantiku jsou stejné jako ty, které jsou vystaveny připojení zahrnující starší klienty nebo servery.</span><span class="sxs-lookup"><span data-stu-id="212aa-163">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="212aa-164">Paralelní provádění</span><span class="sxs-lookup"><span data-stu-id="212aa-164">Parallel Execution</span></span>  
 <span data-ttu-id="212aa-165">MARS není určen k odebrání všech požadavků pro více připojení v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="212aa-165">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="212aa-166">Pokud aplikace potřebuje skutečné paralelní provádění příkazů proti serveru, by měla být použita více připojení.</span><span class="sxs-lookup"><span data-stu-id="212aa-166">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="212aa-167">Představte si například následující scénář.</span><span class="sxs-lookup"><span data-stu-id="212aa-167">For example, consider the following scenario.</span></span> <span data-ttu-id="212aa-168">Jsou vytvořeny dva objekty příkazů, jeden pro zpracování sady výsledků a druhý pro aktualizaci dat; sdílejí společné spojení přes MARS.</span><span class="sxs-lookup"><span data-stu-id="212aa-168">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="212aa-169">V tomto scénáři `Transaction`.`Commit`</span><span class="sxs-lookup"><span data-stu-id="212aa-169">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="212aa-170">se nezdaří při aktualizaci, dokud všechny výsledky byly přečteny na první příkaz objektu, dávat následující výjimku:</span><span class="sxs-lookup"><span data-stu-id="212aa-170">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="212aa-171">Zpráva: Kontext transakce je používán jinou relací.</span><span class="sxs-lookup"><span data-stu-id="212aa-171">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="212aa-172">Zdroj: Zprostředkovatel dat .NET SqlClient</span><span class="sxs-lookup"><span data-stu-id="212aa-172">Source: .NET SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="212aa-173">Bylo očekáváno: (null)</span><span class="sxs-lookup"><span data-stu-id="212aa-173">Expected: (null)</span></span>  
  
 <span data-ttu-id="212aa-174">Přijato: System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="212aa-174">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="212aa-175">Existují tři možnosti pro zpracování tohoto scénáře:</span><span class="sxs-lookup"><span data-stu-id="212aa-175">There are three options for handling this scenario:</span></span>  
  
1. <span data-ttu-id="212aa-176">Spusťte transakci po vytvoření čtečky tak, aby nebyla součástí transakce.</span><span class="sxs-lookup"><span data-stu-id="212aa-176">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="212aa-177">Každá aktualizace se pak stane vlastní transakcí.</span><span class="sxs-lookup"><span data-stu-id="212aa-177">Every update then becomes its own transaction.</span></span>  
  
2. <span data-ttu-id="212aa-178">Po zavření čtečky odevzkaďte veškerou práci.</span><span class="sxs-lookup"><span data-stu-id="212aa-178">Commit all work after the reader is closed.</span></span> <span data-ttu-id="212aa-179">To má potenciál pro podstatnou dávku aktualizací.</span><span class="sxs-lookup"><span data-stu-id="212aa-179">This has the potential for a substantial batch of updates.</span></span>  
  
3. <span data-ttu-id="212aa-180">Nepoužívejte MARS; místo toho použít samostatné připojení pro každý objekt příkazu, jako byste měli před MARS.</span><span class="sxs-lookup"><span data-stu-id="212aa-180">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="212aa-181">Detekce podpory MARS</span><span class="sxs-lookup"><span data-stu-id="212aa-181">Detecting MARS Support</span></span>  
 <span data-ttu-id="212aa-182">Aplikace může zkontrolovat podporu MARS `SqlConnection.ServerVersion` čtením hodnoty.</span><span class="sxs-lookup"><span data-stu-id="212aa-182">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="212aa-183">Hlavní číslo by mělo být 9 pro SQL Server 2005 a 10 pro SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="212aa-183">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="212aa-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="212aa-184">See also</span></span>

- [<span data-ttu-id="212aa-185">Více aktivních sad výsledků (MARS)</span><span class="sxs-lookup"><span data-stu-id="212aa-185">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="212aa-186">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="212aa-186">ADO.NET Overview</span></span>](../ado-net-overview.md)
