---
title: Optimistická metoda souběžného zpracování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: f2fc69867ae1659a342161b00dfd91852441fa5b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126214"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="6b5eb-102">Optimistická metoda souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="6b5eb-102">Optimistic Concurrency</span></span>
<span data-ttu-id="6b5eb-103">V prostředí, existují dva modely pro aktualizaci dat v databázi: optimistického řízení souběžnosti a Pesimistická souběžnost.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="6b5eb-104"><xref:System.Data.DataSet> Objektu je účelem je podporovat používání optimistického řízení souběžnosti pro dlouho běžící aktivity, jako jsou data vzdálenou komunikaci a interakci s daty.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="6b5eb-105">Pesimistická souběžnost zahrnuje uzamčení řádků ve zdroji dat k ostatním uživatelům zabránit ve změně data způsobem, který má vliv aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="6b5eb-106">Pesimistické modelu když uživatel provede akci, která způsobí, že zámek, který má být použita, nemůže ostatním uživatelům provádět akce, které by byla v konfliktu s uzamčením dokud ho vlastník zámku uvolní.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="6b5eb-107">Tento model se používá především v prostředích, kde je těžké kolizí pro data, aby náklady na ochranu dat pomocí zámků je nižší než náklady na transakce vrácení zpět, jestliže se vyskytnou konflikty souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="6b5eb-108">V modelu Pesimistická souběžnost, proto uživatel, který aktualizuje řádek vytvoří zámek.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="6b5eb-109">Dokud uživatel dokončení aktualizace a vydání zámek, nikdo jiný změňte tento řádek.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="6b5eb-110">Z tohoto důvodu je Pesimistická souběžnost nejlépe implementována, pokud bude zámek časy krátký, stejně jako v programové zpracování záznamů.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="6b5eb-111">Pesimistická souběžnost není škálovatelné možnost, když jsou uživatelé interakci s daty a způsobí záznamů, které mají být uzamčen pro relativně velké časová období.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b5eb-112">Pokud je potřeba aktualizovat v rámci jedné operace více řádků, pak vytváření transakcí je možnost a větší škálovatelnost než použití pesimistické zamykání.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="6b5eb-113">Oproti tomu uživatelé, kteří používají optimistického řízení souběžnosti nepoužívejte zámky řádku při čtení.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="6b5eb-114">Když chce uživatel aktualizace řádku, musíte aplikaci určit, zda jiný uživatel změnil řádek, protože byl načten.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="6b5eb-115">Optimistického řízení souběžnosti se obvykle používá v prostředích s nízkou kolizí pro data.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="6b5eb-116">Optimistická souběžnost zlepší výkon, protože žádné uzamčení záznamů je povinná a klauzule zamykání záznamů vyžaduje dalších serverových prostředků.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="6b5eb-117">Aby zůstalo zachované uzamčení záznamů, je také požadované trvalé připojení k databázovému serveru.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="6b5eb-118">Protože to není případ v modelu optimistického řízení souběžnosti, připojení k serveru je zdarma pro obsluhu větší počet klientů v méně času.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="6b5eb-119">V modelu optimistického řízení souběžnosti porušení se považuje za došlo, pokud, jakmile uživatel obdrží hodnotu z databáze, jiný uživatel změní hodnotu před první uživatel se pokusil změnit.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="6b5eb-120">Jak server odstraňuje narušení souběžného zpracování se nejlíp zobrazí první popsáním v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="6b5eb-121">V následujících tabulkách použijte příklad optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="6b5eb-122">Uživatel1 v 13:00:00, načte řádek z databáze s použitím následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="6b5eb-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 **<span data-ttu-id="6b5eb-123">Jméno příjmení CustID</span><span class="sxs-lookup"><span data-stu-id="6b5eb-123">CustID     LastName     FirstName</span></span>**  
  
 <span data-ttu-id="6b5eb-124">101 Smith Bob</span><span class="sxs-lookup"><span data-stu-id="6b5eb-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="6b5eb-125">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="6b5eb-125">Column name</span></span>|<span data-ttu-id="6b5eb-126">Původní hodnota</span><span class="sxs-lookup"><span data-stu-id="6b5eb-126">Original value</span></span>|<span data-ttu-id="6b5eb-127">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="6b5eb-127">Current value</span></span>|<span data-ttu-id="6b5eb-128">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="6b5eb-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="6b5eb-129">CustID</span><span class="sxs-lookup"><span data-stu-id="6b5eb-129">CustID</span></span>|<span data-ttu-id="6b5eb-130">101</span><span class="sxs-lookup"><span data-stu-id="6b5eb-130">101</span></span>|<span data-ttu-id="6b5eb-131">101</span><span class="sxs-lookup"><span data-stu-id="6b5eb-131">101</span></span>|<span data-ttu-id="6b5eb-132">101</span><span class="sxs-lookup"><span data-stu-id="6b5eb-132">101</span></span>|  
|<span data-ttu-id="6b5eb-133">LastName</span><span class="sxs-lookup"><span data-stu-id="6b5eb-133">LastName</span></span>|<span data-ttu-id="6b5eb-134">Smith</span><span class="sxs-lookup"><span data-stu-id="6b5eb-134">Smith</span></span>|<span data-ttu-id="6b5eb-135">Smith</span><span class="sxs-lookup"><span data-stu-id="6b5eb-135">Smith</span></span>|<span data-ttu-id="6b5eb-136">Smith</span><span class="sxs-lookup"><span data-stu-id="6b5eb-136">Smith</span></span>|  
|<span data-ttu-id="6b5eb-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="6b5eb-137">FirstName</span></span>|<span data-ttu-id="6b5eb-138">Bob</span><span class="sxs-lookup"><span data-stu-id="6b5eb-138">Bob</span></span>|<span data-ttu-id="6b5eb-139">Bob</span><span class="sxs-lookup"><span data-stu-id="6b5eb-139">Bob</span></span>|<span data-ttu-id="6b5eb-140">Bob</span><span class="sxs-lookup"><span data-stu-id="6b5eb-140">Bob</span></span>|  
  
 <span data-ttu-id="6b5eb-141">V 13:01:00 uživatel2 přečte na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="6b5eb-142">Ve 13:03:00, uživatel2 změní **FirstName** z "Bob" řetězec "Robert" a aktualizaci databáze.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="6b5eb-143">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="6b5eb-143">Column name</span></span>|<span data-ttu-id="6b5eb-144">Původní hodnota</span><span class="sxs-lookup"><span data-stu-id="6b5eb-144">Original value</span></span>|<span data-ttu-id="6b5eb-145">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="6b5eb-145">Current value</span></span>|<span data-ttu-id="6b5eb-146">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="6b5eb-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="6b5eb-147">CustID</span><span class="sxs-lookup"><span data-stu-id="6b5eb-147">CustID</span></span>|<span data-ttu-id="6b5eb-148">101</span><span class="sxs-lookup"><span data-stu-id="6b5eb-148">101</span></span>|<span data-ttu-id="6b5eb-149">101</span><span class="sxs-lookup"><span data-stu-id="6b5eb-149">101</span></span>|<span data-ttu-id="6b5eb-150">101</span><span class="sxs-lookup"><span data-stu-id="6b5eb-150">101</span></span>|  
|<span data-ttu-id="6b5eb-151">LastName</span><span class="sxs-lookup"><span data-stu-id="6b5eb-151">LastName</span></span>|<span data-ttu-id="6b5eb-152">Smith</span><span class="sxs-lookup"><span data-stu-id="6b5eb-152">Smith</span></span>|<span data-ttu-id="6b5eb-153">Smith</span><span class="sxs-lookup"><span data-stu-id="6b5eb-153">Smith</span></span>|<span data-ttu-id="6b5eb-154">Smith</span><span class="sxs-lookup"><span data-stu-id="6b5eb-154">Smith</span></span>|  
|<span data-ttu-id="6b5eb-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="6b5eb-155">FirstName</span></span>|<span data-ttu-id="6b5eb-156">Bob</span><span class="sxs-lookup"><span data-stu-id="6b5eb-156">Bob</span></span>|<span data-ttu-id="6b5eb-157">Robert</span><span class="sxs-lookup"><span data-stu-id="6b5eb-157">Robert</span></span>|<span data-ttu-id="6b5eb-158">Bob</span><span class="sxs-lookup"><span data-stu-id="6b5eb-158">Bob</span></span>|  
  
 <span data-ttu-id="6b5eb-159">Tato aktualizace bude úspěšné, protože původní hodnoty, které má uživatel2 shodovat s hodnotami v databázi v době aktualizace.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="6b5eb-160">V 13:05:00 uživatel1 "Bob" jméno se změní na "James" a pokus o aktualizaci řádku.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="6b5eb-161">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="6b5eb-161">Column name</span></span>|<span data-ttu-id="6b5eb-162">Původní hodnota</span><span class="sxs-lookup"><span data-stu-id="6b5eb-162">Original value</span></span>|<span data-ttu-id="6b5eb-163">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="6b5eb-163">Current value</span></span>|<span data-ttu-id="6b5eb-164">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="6b5eb-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="6b5eb-165">CustID</span><span class="sxs-lookup"><span data-stu-id="6b5eb-165">CustID</span></span>|<span data-ttu-id="6b5eb-166">101</span><span class="sxs-lookup"><span data-stu-id="6b5eb-166">101</span></span>|<span data-ttu-id="6b5eb-167">101</span><span class="sxs-lookup"><span data-stu-id="6b5eb-167">101</span></span>|<span data-ttu-id="6b5eb-168">101</span><span class="sxs-lookup"><span data-stu-id="6b5eb-168">101</span></span>|  
|<span data-ttu-id="6b5eb-169">LastName</span><span class="sxs-lookup"><span data-stu-id="6b5eb-169">LastName</span></span>|<span data-ttu-id="6b5eb-170">Smith</span><span class="sxs-lookup"><span data-stu-id="6b5eb-170">Smith</span></span>|<span data-ttu-id="6b5eb-171">Smith</span><span class="sxs-lookup"><span data-stu-id="6b5eb-171">Smith</span></span>|<span data-ttu-id="6b5eb-172">Smith</span><span class="sxs-lookup"><span data-stu-id="6b5eb-172">Smith</span></span>|  
|<span data-ttu-id="6b5eb-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="6b5eb-173">FirstName</span></span>|<span data-ttu-id="6b5eb-174">Bob</span><span class="sxs-lookup"><span data-stu-id="6b5eb-174">Bob</span></span>|<span data-ttu-id="6b5eb-175">James</span><span class="sxs-lookup"><span data-stu-id="6b5eb-175">James</span></span>|<span data-ttu-id="6b5eb-176">Robert</span><span class="sxs-lookup"><span data-stu-id="6b5eb-176">Robert</span></span>|  
  
 <span data-ttu-id="6b5eb-177">V tomto okamžiku User1 dojde k narušení optimistického řízení souběžnosti protože hodnota v databázi ("Robert") už odpovídá původní hodnotu, že User1 očekávané ("Bob").</span><span class="sxs-lookup"><span data-stu-id="6b5eb-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="6b5eb-178">Narušení souběžného zpracování jednoduše poznáte, že aktualizace nebyla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="6b5eb-179">Rozhodnutí teď je potřeba provést, zda chcete přepsat změny poskytnutých uživatel2 změnami poskytnutých uživatel1, nebo zrušit změny uživatele User1.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="6b5eb-180">Testování pro porušení optimistického řízení souběžnosti</span><span class="sxs-lookup"><span data-stu-id="6b5eb-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="6b5eb-181">Existuje několik postupů pro testování na narušení optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="6b5eb-182">Zahrnuje jeden, včetně sloupec časového razítka v tabulce.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="6b5eb-183">Databáze obvykle poskytují funkce časového razítka, který můžete použít k identifikaci datum a čas poslední aktualizace záznamu.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="6b5eb-184">Tímto způsobem je sloupec časového razítka zahrnuta v definici tabulky.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="6b5eb-185">Pokaždé, když se tento záznam se aktualizuje, časové razítko se aktualizuje tak, aby odrážela aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="6b5eb-186">V rámci testu pro porušení optimistického řízení souběžnosti je vrácen sloupec časového razítka s jakýkoli dotaz obsah tabulky.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="6b5eb-187">Při pokusu o aktualizaci hodnotu časového razítka v databázi je ve srovnání s původní hodnotu časového razítka v řádku upravené.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="6b5eb-188">Pokud se shodují, se provádí aktualizace a sloupec časového razítka se aktualizuje s aktuálním časem tak, aby odrážely aktualizace.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="6b5eb-189">Pokud shodné nejsou, došlo k narušení optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="6b5eb-190">Další možností, jak testování pro narušení optimistického řízení souběžnosti se k ověření, že všechny původní hodnoty sloupce v řádku stále shodovat s hodnotami v databázi nalezen.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="6b5eb-191">Zvažte například následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="6b5eb-191">For example, consider the following query:</span></span>  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="6b5eb-192">Pro testování narušení optimistického řízení souběžnosti při aktualizaci řádku **Tabulka1**, by vydat příkaz následující aktualizace:</span><span class="sxs-lookup"><span data-stu-id="6b5eb-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="6b5eb-193">Za předpokladu, původní hodnoty shodují s hodnotami v databázi, provádí se aktualizace.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="6b5eb-194">Pokud se změnila hodnotu, nebude aktualizace změnit řádku, protože klauzule WHERE nenajde shoda.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="6b5eb-195">Mějte na paměti, doporučuje se vždycky vrátit jedinečné hodnoty primárního klíče v dotazu.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="6b5eb-196">Předchozí příkaz UPDATE v opačném případě může aktualizovat více než jeden řádek, který nemusí být vašich představ.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="6b5eb-197">Pokud sloupec na zdroj dat se povoluje hodnoty Null, budete muset rozšířit vaše klauzule WHERE, která pro odpovídající odkaz s hodnotou null v lokální tabulce a ve zdroji dat. Zkontrolujte.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="6b5eb-198">Například následující příkaz aktualizace ověřuje, že odkaz s hodnotou null v řádku místní stále odpovídá nulový odkaz na zdroj dat, nebo jestli hodnotu v řádku místní stále odpovídá hodnotě ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="6b5eb-199">Můžete také použít méně omezující kritéria při použití modelu optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="6b5eb-200">Například použití pouze primární klíčových sloupců v klauzuli WHERE způsobí, že data, která mají být přepsány bez ohledu na to, zda další sloupce, které byly aktualizovány od posledního dotazu.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="6b5eb-201">Můžete také použít klauzuli WHERE pouze na konkrétní sloupce, což vede k přepsání Pokud konkrétních polích byly aktualizovány od posledního dotazovat data.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="6b5eb-202">DataAdapter.RowUpdated události</span><span class="sxs-lookup"><span data-stu-id="6b5eb-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="6b5eb-203">**RowUpdated** událost <xref:System.Data.Common.DataAdapter> objekt lze použít ve spojení pomocí technik popsaných výše, k poskytování oznámení do vaší aplikace porušení optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="6b5eb-204">**RowUpdated** dojde poté, co každý pokus o aktualizaci **změněné** řádek z **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="6b5eb-205">To umožňuje přidat zvláštní zpracování kódu, včetně zpracování, když dojde k výjimce, přidání vlastních informací o chybě, přidání logiky pro opakování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="6b5eb-206"><xref:System.Data.Common.RowUpdatedEventArgs> Vrátí objekt **RecordsAffected** vlastnost obsahuje počet řádků, které jsou ovlivněny příkazu konkrétní update pro upravené řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="6b5eb-207">Nastavením příkaz aktualizace pro testování optimistického řízení souběžnosti **RecordsAffected** vlastnost, v důsledku toho vrátí hodnotu 0 při došlo k narušení optimistického řízení souběžnosti, protože byly aktualizovány žádné záznamy.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="6b5eb-208">Pokud je to tento případ, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="6b5eb-209">**RowUpdated** událostí umožňuje zpracovávat tento výskyt a vyhnout se výjimka nastavením odpovídající **RowUpdatedEventArgs.Status** hodnoty, jako například  **UpdateStatus.SkipCurrentRow**.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="6b5eb-210">Další informace o **RowUpdated** událostí, naleznete v tématu [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="6b5eb-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="6b5eb-211">Volitelně můžete nastavit **DataAdapter.ContinueUpdateOnError** k **true**, před voláním **aktualizace**a reagovat na chybové informace uložené v **RowError** vlastnost konkrétní řádek, kdy **aktualizace** je dokončena.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="6b5eb-212">Další informace najdete v tématu [informace o chybě řádek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="6b5eb-212">For more information, see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="6b5eb-213">Příklad optimistického řízení souběžnosti</span><span class="sxs-lookup"><span data-stu-id="6b5eb-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="6b5eb-214">Tady je jednoduchý příklad, který nastaví **událost UpdateCommand** z **DataAdapter** pro testování optimistického řízení souběžnosti a potom použije **RowUpdated** události pro testování porušení optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="6b5eb-215">Když je zjištěna narušení optimistického řízení souběžnosti, aplikace nastaví **RowError** řádku, na který aktualizace byl vydán pro tak, aby odrážely narušení optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="6b5eb-216">Všimněte si, že se parametr hodnoty předané do klauzule WHERE příkazu pro aktualizaci se mapují na **původní** hodnoty jejich odpovídajících sloupců.</span><span class="sxs-lookup"><span data-stu-id="6b5eb-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b5eb-217">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b5eb-217">See also</span></span>

- [<span data-ttu-id="6b5eb-218">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6b5eb-218">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="6b5eb-219">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="6b5eb-219">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="6b5eb-220">Informace o chybě na řádku</span><span class="sxs-lookup"><span data-stu-id="6b5eb-220">Row Error Information</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="6b5eb-221">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="6b5eb-221">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="6b5eb-222">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="6b5eb-222">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
