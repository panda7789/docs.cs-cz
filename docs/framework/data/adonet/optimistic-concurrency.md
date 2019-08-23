---
title: Optimistická metoda souběžného zpracování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: 37641056f2f3110685c24266d2612845ffbf0b3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929242"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="7367e-102">Optimistická metoda souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="7367e-102">Optimistic Concurrency</span></span>
<span data-ttu-id="7367e-103">Ve víceuživatelském prostředí existují dva modely pro aktualizaci dat v databázi: Optimistická souběžnost a pesimistická souběžnost.</span><span class="sxs-lookup"><span data-stu-id="7367e-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="7367e-104"><xref:System.Data.DataSet> Objekt je navržený tak, aby podporoval použití optimistické souběžnosti pro dlouhotrvající aktivity, jako jsou vzdálená data a interakce s daty.</span><span class="sxs-lookup"><span data-stu-id="7367e-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="7367e-105">Pesimistická souběžnost zahrnuje uzamykání řádků ve zdroji dat, aby ostatní uživatelé nemohli upravovat data způsobem, který má vliv na aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="7367e-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="7367e-106">V pesimistické modelu, pokud uživatel provede akci, která způsobí použití zámku, nemohou jiní uživatelé provádět akce, které by mohly být v konfliktu s zámkem, dokud ho vlastník zámku neuvolní.</span><span class="sxs-lookup"><span data-stu-id="7367e-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="7367e-107">Tento model se primárně používá v prostředích, kde se vyskytují silné kolize dat, takže náklady na ochranu dat s zámky jsou nižší než náklady na vracení zpět transakcí, pokud dojde ke konfliktům souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7367e-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="7367e-108">Proto v pesimistické Concurrency modelu vytvoří uživatel, který aktualizuje řádek, zámek.</span><span class="sxs-lookup"><span data-stu-id="7367e-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="7367e-109">Dokud uživatel nedokončil aktualizaci a uvolnil zámek, žádný jiný tento řádek nemůže změnit.</span><span class="sxs-lookup"><span data-stu-id="7367e-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="7367e-110">Z tohoto důvodu je pesimistická souběžnost nejlépe implementována v případě, že doba uzamčení bude krátká, jako při programovém zpracování záznamů.</span><span class="sxs-lookup"><span data-stu-id="7367e-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="7367e-111">Pesimistická souběžnost není škálovatelná možnost, když uživatelé vzájemně pracují s daty a způsobují, aby byly záznamy uzamčené poměrně velkých časových období.</span><span class="sxs-lookup"><span data-stu-id="7367e-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7367e-112">Pokud potřebujete aktualizovat více řádků ve stejné operaci, pak vytvoření transakce je pružnější možnost než použití Pesimistické uzamykání.</span><span class="sxs-lookup"><span data-stu-id="7367e-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="7367e-113">Naproti tomu uživatelé, kteří používají optimistické řízení souběžnosti, nezamkne řádek při čtení.</span><span class="sxs-lookup"><span data-stu-id="7367e-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="7367e-114">Když uživatel chce aktualizovat řádek, aplikace musí určit, jestli jiný uživatel změnil řádek od jeho čtení.</span><span class="sxs-lookup"><span data-stu-id="7367e-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="7367e-115">Optimistická souběžnost se obecně používá v prostředích s nízkým kolizí dat.</span><span class="sxs-lookup"><span data-stu-id="7367e-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="7367e-116">Optimistická souběžnost zlepšuje výkon, protože není nutné žádné zamykání záznamů a uzamykání záznamů vyžaduje další prostředky serveru.</span><span class="sxs-lookup"><span data-stu-id="7367e-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="7367e-117">Aby bylo možné zachovat zámky záznamů, je nutné trvale připojit k databázovému serveru.</span><span class="sxs-lookup"><span data-stu-id="7367e-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="7367e-118">Vzhledem k tomu, že se nejedná o případ v optimistickém modelu souběžnosti, připojení k serveru jsou zdarma pro poskytování většího počtu klientů v kratší dobu.</span><span class="sxs-lookup"><span data-stu-id="7367e-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="7367e-119">V modelu optimistického souběžnosti se porušení považuje za, pokud poté, co uživatel obdrží hodnotu z databáze, změní jiný uživatel hodnotu předtím, než se první uživatel pokusí ho změnit.</span><span class="sxs-lookup"><span data-stu-id="7367e-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="7367e-120">Jak server řeší porušení souběžnosti, je nejlepším způsobem, jak nejprve popsat následující příklad.</span><span class="sxs-lookup"><span data-stu-id="7367e-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="7367e-121">Následující tabulky následují jako příklad optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7367e-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="7367e-122">V 1:00 hodin uživatel1 přečte řádek z databáze s následujícími hodnotami:</span><span class="sxs-lookup"><span data-stu-id="7367e-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="7367e-123">**CustID příjmení FirstName**</span><span class="sxs-lookup"><span data-stu-id="7367e-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="7367e-124">101 Smith Jan</span><span class="sxs-lookup"><span data-stu-id="7367e-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="7367e-125">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="7367e-125">Column name</span></span>|<span data-ttu-id="7367e-126">Původní hodnota</span><span class="sxs-lookup"><span data-stu-id="7367e-126">Original value</span></span>|<span data-ttu-id="7367e-127">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="7367e-127">Current value</span></span>|<span data-ttu-id="7367e-128">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="7367e-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="7367e-129">CustID</span><span class="sxs-lookup"><span data-stu-id="7367e-129">CustID</span></span>|<span data-ttu-id="7367e-130">101</span><span class="sxs-lookup"><span data-stu-id="7367e-130">101</span></span>|<span data-ttu-id="7367e-131">101</span><span class="sxs-lookup"><span data-stu-id="7367e-131">101</span></span>|<span data-ttu-id="7367e-132">101</span><span class="sxs-lookup"><span data-stu-id="7367e-132">101</span></span>|  
|<span data-ttu-id="7367e-133">LastName</span><span class="sxs-lookup"><span data-stu-id="7367e-133">LastName</span></span>|<span data-ttu-id="7367e-134">Smith</span><span class="sxs-lookup"><span data-stu-id="7367e-134">Smith</span></span>|<span data-ttu-id="7367e-135">Smith</span><span class="sxs-lookup"><span data-stu-id="7367e-135">Smith</span></span>|<span data-ttu-id="7367e-136">Smith</span><span class="sxs-lookup"><span data-stu-id="7367e-136">Smith</span></span>|  
|<span data-ttu-id="7367e-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="7367e-137">FirstName</span></span>|<span data-ttu-id="7367e-138">Bob</span><span class="sxs-lookup"><span data-stu-id="7367e-138">Bob</span></span>|<span data-ttu-id="7367e-139">Bob</span><span class="sxs-lookup"><span data-stu-id="7367e-139">Bob</span></span>|<span data-ttu-id="7367e-140">Bob</span><span class="sxs-lookup"><span data-stu-id="7367e-140">Bob</span></span>|  
  
 <span data-ttu-id="7367e-141">V 1:01 večer uživatel2 načte stejný řádek.</span><span class="sxs-lookup"><span data-stu-id="7367e-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="7367e-142">V 1:03. uživatel2 uživatel2 změní **FirstName** z "Bob" na "Robert" a aktualizuje databázi.</span><span class="sxs-lookup"><span data-stu-id="7367e-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="7367e-143">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="7367e-143">Column name</span></span>|<span data-ttu-id="7367e-144">Původní hodnota</span><span class="sxs-lookup"><span data-stu-id="7367e-144">Original value</span></span>|<span data-ttu-id="7367e-145">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="7367e-145">Current value</span></span>|<span data-ttu-id="7367e-146">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="7367e-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="7367e-147">CustID</span><span class="sxs-lookup"><span data-stu-id="7367e-147">CustID</span></span>|<span data-ttu-id="7367e-148">101</span><span class="sxs-lookup"><span data-stu-id="7367e-148">101</span></span>|<span data-ttu-id="7367e-149">101</span><span class="sxs-lookup"><span data-stu-id="7367e-149">101</span></span>|<span data-ttu-id="7367e-150">101</span><span class="sxs-lookup"><span data-stu-id="7367e-150">101</span></span>|  
|<span data-ttu-id="7367e-151">LastName</span><span class="sxs-lookup"><span data-stu-id="7367e-151">LastName</span></span>|<span data-ttu-id="7367e-152">Smith</span><span class="sxs-lookup"><span data-stu-id="7367e-152">Smith</span></span>|<span data-ttu-id="7367e-153">Smith</span><span class="sxs-lookup"><span data-stu-id="7367e-153">Smith</span></span>|<span data-ttu-id="7367e-154">Smith</span><span class="sxs-lookup"><span data-stu-id="7367e-154">Smith</span></span>|  
|<span data-ttu-id="7367e-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="7367e-155">FirstName</span></span>|<span data-ttu-id="7367e-156">Bob</span><span class="sxs-lookup"><span data-stu-id="7367e-156">Bob</span></span>|<span data-ttu-id="7367e-157">Robert</span><span class="sxs-lookup"><span data-stu-id="7367e-157">Robert</span></span>|<span data-ttu-id="7367e-158">Bob</span><span class="sxs-lookup"><span data-stu-id="7367e-158">Bob</span></span>|  
  
 <span data-ttu-id="7367e-159">Aktualizace je úspěšná, protože hodnoty v databázi v době aktualizace odpovídají původním hodnotám, které má uživatel2.</span><span class="sxs-lookup"><span data-stu-id="7367e-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="7367e-160">V 1:05 ODP. uživatel1 změní jméno "Bob" na "James" a pokusí se řádek aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="7367e-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="7367e-161">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="7367e-161">Column name</span></span>|<span data-ttu-id="7367e-162">Původní hodnota</span><span class="sxs-lookup"><span data-stu-id="7367e-162">Original value</span></span>|<span data-ttu-id="7367e-163">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="7367e-163">Current value</span></span>|<span data-ttu-id="7367e-164">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="7367e-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="7367e-165">CustID</span><span class="sxs-lookup"><span data-stu-id="7367e-165">CustID</span></span>|<span data-ttu-id="7367e-166">101</span><span class="sxs-lookup"><span data-stu-id="7367e-166">101</span></span>|<span data-ttu-id="7367e-167">101</span><span class="sxs-lookup"><span data-stu-id="7367e-167">101</span></span>|<span data-ttu-id="7367e-168">101</span><span class="sxs-lookup"><span data-stu-id="7367e-168">101</span></span>|  
|<span data-ttu-id="7367e-169">LastName</span><span class="sxs-lookup"><span data-stu-id="7367e-169">LastName</span></span>|<span data-ttu-id="7367e-170">Smith</span><span class="sxs-lookup"><span data-stu-id="7367e-170">Smith</span></span>|<span data-ttu-id="7367e-171">Smith</span><span class="sxs-lookup"><span data-stu-id="7367e-171">Smith</span></span>|<span data-ttu-id="7367e-172">Smith</span><span class="sxs-lookup"><span data-stu-id="7367e-172">Smith</span></span>|  
|<span data-ttu-id="7367e-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="7367e-173">FirstName</span></span>|<span data-ttu-id="7367e-174">Bob</span><span class="sxs-lookup"><span data-stu-id="7367e-174">Bob</span></span>|<span data-ttu-id="7367e-175">Petr</span><span class="sxs-lookup"><span data-stu-id="7367e-175">James</span></span>|<span data-ttu-id="7367e-176">Robert</span><span class="sxs-lookup"><span data-stu-id="7367e-176">Robert</span></span>|  
  
 <span data-ttu-id="7367e-177">V tomto okamžiku uživatel1 narazí na porušení optimistické souběžnosti, protože hodnota v databázi ("Robert") se už neshoduje s původní hodnotou, kterou uživatel1 očekával ("Bob").</span><span class="sxs-lookup"><span data-stu-id="7367e-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="7367e-178">Porušení souběžnosti vám stačí, když zjistíte, že se aktualizace nezdařila.</span><span class="sxs-lookup"><span data-stu-id="7367e-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="7367e-179">Rozhodnutí teď musí být provedeno bez ohledu na to, jestli se změny dodávají v rámci aplikace uživatel2, a změny poskytované uživatelem user1, nebo změny podle uživatele user1 zrušit.</span><span class="sxs-lookup"><span data-stu-id="7367e-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="7367e-180">Testování pro porušení optimistické souběžnosti</span><span class="sxs-lookup"><span data-stu-id="7367e-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="7367e-181">K dispozici je několik technik pro testování v případě porušení optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7367e-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="7367e-182">Jedna zahrnuje zahrnutí sloupce časového razítka do tabulky.</span><span class="sxs-lookup"><span data-stu-id="7367e-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="7367e-183">Databáze běžně poskytují funkci časového razítka, která se dá použít k identifikaci data a času poslední aktualizace záznamu.</span><span class="sxs-lookup"><span data-stu-id="7367e-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="7367e-184">Pomocí této techniky je v definici tabulky zahrnut sloupec časového razítka.</span><span class="sxs-lookup"><span data-stu-id="7367e-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="7367e-185">Pokaždé, když se záznam aktualizuje, časové razítko se aktualizuje tak, aby odráželo aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="7367e-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="7367e-186">V testu pro porušení optimistické souběžnosti je sloupec časového razítka vrácen libovolným dotazem na obsah tabulky.</span><span class="sxs-lookup"><span data-stu-id="7367e-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="7367e-187">Při pokusu o aktualizaci je hodnota časového razítka v databázi porovnána s původní hodnotou časového razítka obsaženou ve změněném řádku.</span><span class="sxs-lookup"><span data-stu-id="7367e-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="7367e-188">Pokud se shodují, provede se aktualizace a sloupec časového razítka se aktualizuje aktuálním časem, aby odrážel aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="7367e-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="7367e-189">Pokud se neshodují, došlo k narušení optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7367e-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="7367e-190">Další technikou pro testování pro porušení optimistické souběžnosti je ověřit, zda všechny původní hodnoty sloupců v řádku stále odpovídají hodnotám nalezeným v databázi.</span><span class="sxs-lookup"><span data-stu-id="7367e-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="7367e-191">Zvažte například následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="7367e-191">For example, consider the following query:</span></span>  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="7367e-192">Chcete-li provést test optimistického chování souběžnosti při aktualizaci řádku ve vlastnosti **Tabulka1**, vydejte následující příkaz Update:</span><span class="sxs-lookup"><span data-stu-id="7367e-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="7367e-193">Pokud se původní hodnoty shodují s hodnotami v databázi, provede se aktualizace.</span><span class="sxs-lookup"><span data-stu-id="7367e-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="7367e-194">Pokud byla hodnota změněna, nebude tato aktualizace řádek upravovat, protože klauzule WHERE nenajde shodu.</span><span class="sxs-lookup"><span data-stu-id="7367e-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="7367e-195">Všimněte si, že se doporučuje vždycky vracet jedinečnou hodnotu primárního klíče v dotazu.</span><span class="sxs-lookup"><span data-stu-id="7367e-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="7367e-196">V opačném případě může předchozí příkaz UPDATE aktualizovat více než jeden řádek, který nemusí být vaším záměrem.</span><span class="sxs-lookup"><span data-stu-id="7367e-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="7367e-197">Pokud sloupec v datovém zdroji povoluje hodnoty null, může být nutné zvětšit klauzuli WHERE, aby kontrolovala shodný odkaz null v místní tabulce a ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="7367e-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="7367e-198">Například následující příkaz UPDATE ověřuje, že odkaz s hodnotou null v místním řádku se stále shoduje s nulovým odkazem ve zdroji dat nebo že hodnota v místním řádku se stále shoduje s hodnotou ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="7367e-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="7367e-199">Při použití optimistického modelu souběžnosti můžete také zvolit, že se mají použít méně omezující kritéria.</span><span class="sxs-lookup"><span data-stu-id="7367e-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="7367e-200">Například použití pouze sloupců primárního klíče v klauzuli WHERE způsobí, že data budou přepsána bez ohledu na to, zda byly od posledního dotazu aktualizovány ostatní sloupce.</span><span class="sxs-lookup"><span data-stu-id="7367e-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="7367e-201">Klauzuli WHERE můžete také použít pouze na konkrétní sloupce a výsledná data budou přepsána, pokud nebyla aktualizována konkrétní pole od posledního dotazu.</span><span class="sxs-lookup"><span data-stu-id="7367e-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="7367e-202">Událost DataAdapter. RowUpdated metody Update</span><span class="sxs-lookup"><span data-stu-id="7367e-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="7367e-203">Událost<xref:System.Data.Common.DataAdapter> **RowUpdated metody Update** objektu lze použít ve spojení s výše popsanými postupy, aby bylo možné poskytnout oznámení vaší aplikaci s porušením optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7367e-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="7367e-204">K **RowUpdated metody Update** dochází po každém pokusu o aktualizaci **upraveného** řádku z **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="7367e-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="7367e-205">To umožňuje přidat speciální kód pro zpracování, včetně zpracování, když dojde k výjimce, přidání vlastních informací o chybě, přidání logiky opakování atd.</span><span class="sxs-lookup"><span data-stu-id="7367e-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="7367e-206">Objekt vrátí vlastnost RecordsAffected obsahující počet řádků ovlivněných určitým příkazem aktualizace pro upravený řádek v tabulce. <xref:System.Data.Common.RowUpdatedEventArgs></span><span class="sxs-lookup"><span data-stu-id="7367e-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="7367e-207">Nastavením příkazu Update na test pro optimistickou souběžnost bude vlastnost **RecordsAffected** v důsledku toho vracet hodnotu 0, pokud došlo k narušení optimistické souběžnosti, protože nebyly aktualizovány žádné záznamy.</span><span class="sxs-lookup"><span data-stu-id="7367e-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="7367e-208">Pokud se jedná o tento případ, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7367e-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="7367e-209">Událost **RowUpdated metody Update** umožňuje zpracovat tento výskyt a vyhnout se výjimce nastavením příslušné hodnoty **RowUpdatedEventArgs. status** , například **UpdateStatus. SkipCurrentRow**.</span><span class="sxs-lookup"><span data-stu-id="7367e-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="7367e-210">Další informace o události **RowUpdated metody Update** naleznete v tématu [zpracování událostí DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="7367e-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="7367e-211">Volitelně můžete nastavit vlastnost **DataAdapter. ContinueUpdateOnError** na **hodnotu true**, před voláním metody **Update**a reagovat na informace o chybě uložené ve vlastnosti **RowError** určitého řádku po dokončení **aktualizace** .</span><span class="sxs-lookup"><span data-stu-id="7367e-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="7367e-212">Další informace najdete v tématu [informace o chybě řádku](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="7367e-212">For more information, see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="7367e-213">Příklad optimistického řízení souběžnosti</span><span class="sxs-lookup"><span data-stu-id="7367e-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="7367e-214">Následuje jednoduchý příklad, který nastaví **událost UpdateCommand** na test pro optimistickou souběžnost a poté používá událost **RowUpdated metody Update** k otestování optimistického chování souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7367e-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="7367e-215">Když dojde k narušení optimistického řízení souběžnosti, aplikace nastaví **RowError** řádku, pro který byla aktualizace vystavena, aby odrážela optimistické porušení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7367e-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="7367e-216">Všimněte si, že hodnoty parametrů předané do klauzule WHERE příkazu UPDATE jsou namapovány na **původní** hodnoty příslušných sloupců.</span><span class="sxs-lookup"><span data-stu-id="7367e-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then   
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)   
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7367e-217">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7367e-217">See also</span></span>

- [<span data-ttu-id="7367e-218">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7367e-218">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="7367e-219">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="7367e-219">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="7367e-220">Informace o chybě na řádku</span><span class="sxs-lookup"><span data-stu-id="7367e-220">Row Error Information</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="7367e-221">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="7367e-221">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="7367e-222">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="7367e-222">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
