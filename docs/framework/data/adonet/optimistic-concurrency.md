---
title: Optimistická metoda souběžného zpracování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: e8d24a3998ca97fdf45e647bc40c1f7d6018ec20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149450"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="7dfa8-102">Optimistická metoda souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="7dfa8-102">Optimistic Concurrency</span></span>
<span data-ttu-id="7dfa8-103">Ve víceuživatelském prostředí existují dva modely pro aktualizaci dat v databázi: optimistická souběžnost a pesimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="7dfa8-104">Objekt <xref:System.Data.DataSet> je navržen tak, aby podporoval použití optimistické souběžnosti pro dlouhotrvající aktivity, jako je například vzdálené komunikace dat a interakci s daty.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="7dfa8-105">Pesimistické souběžnosti zahrnuje uzamčení řádků ve zdroji dat zabránit ostatním uživatelům v úpravě dat způsobem, který ovlivňuje aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="7dfa8-106">V pesimistickém modelu, když uživatel provede akci, která způsobí použití zámku, ostatní uživatelé nemohou provádět akce, které by byly v konfliktu se zámkem, dokud jej vlastník zámku neuvolní.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="7dfa8-107">Tento model se používá především v prostředích, kde je těžké tvrzení pro data, tak, aby náklady na ochranu dat s zámky je menší než náklady na vrácení transakce zpět, pokud dojde ke konfliktům souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="7dfa8-108">Proto v pesimistické souběžnosti modelu, uživatel, který aktualizuje řádek vytvoří zámek.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="7dfa8-109">Dokud uživatel nedokončí aktualizaci a neuvolní zámek, nikdo jiný nemůže tento řádek změnit.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="7dfa8-110">Z tohoto důvodu pesimistické souběžnosti je nejlépe implementovat, když bude krátké časy uzamčení, jako v programovém zpracování záznamů.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="7dfa8-111">Pesimistické souběžnosti není škálovatelná možnost, když uživatelé jsou interakci s daty a způsobuje záznamy, které mají být uzamčeny pro relativně velké časové období.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7dfa8-112">Pokud potřebujete aktualizovat více řádků ve stejné operaci, pak vytvoření transakce je škálovatelnější možnost než pomocí pesimistické zamykání.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="7dfa8-113">Naproti tomu uživatelé, kteří používají optimistickou souběžnost, neuzamknou řádek při čtení.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="7dfa8-114">Pokud chce uživatel aktualizovat řádek, musí aplikace určit, zda jiný uživatel změnil řádek od jeho čtení.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="7dfa8-115">Optimistická souběžnost se obvykle používá v prostředích s nízkou kolizí pro data.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="7dfa8-116">Optimistická souběžnost zlepšuje výkon, protože není vyžadováno žádné uzamčení záznamů a uzamčení záznamů vyžaduje další prostředky serveru.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="7dfa8-117">Chcete-li zachovat uzamčení záznamů, je také vyžadováno trvalé připojení k databázovému serveru.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="7dfa8-118">Vzhledem k tomu, že tomu tak není v optimistickém modelu souběžnosti, připojení k serveru mohou obsluhovat větší počet klientů v kratším čase.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="7dfa8-119">V optimistické souběžnosti modelu porušení se považuje za došlo, pokud poté, co uživatel obdrží hodnotu z databáze, jiný uživatel upraví hodnotu před první uživatel se pokusí upravit.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="7dfa8-120">Jak server řeší porušení souběžnosti je nejlépe zobrazit nejprve popisující následující příklad.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="7dfa8-121">Následující tabulky následují příklad optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="7dfa8-122">V 13:00 uživatel1 přečte řádek z databáze s následujícími hodnotami:</span><span class="sxs-lookup"><span data-stu-id="7dfa8-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="7dfa8-123">**Jméno příjmení CustID**</span><span class="sxs-lookup"><span data-stu-id="7dfa8-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="7dfa8-124">101 Kovář Bob</span><span class="sxs-lookup"><span data-stu-id="7dfa8-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="7dfa8-125">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="7dfa8-125">Column name</span></span>|<span data-ttu-id="7dfa8-126">Původní hodnota</span><span class="sxs-lookup"><span data-stu-id="7dfa8-126">Original value</span></span>|<span data-ttu-id="7dfa8-127">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="7dfa8-127">Current value</span></span>|<span data-ttu-id="7dfa8-128">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="7dfa8-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="7dfa8-129">CustID</span><span class="sxs-lookup"><span data-stu-id="7dfa8-129">CustID</span></span>|<span data-ttu-id="7dfa8-130">101</span><span class="sxs-lookup"><span data-stu-id="7dfa8-130">101</span></span>|<span data-ttu-id="7dfa8-131">101</span><span class="sxs-lookup"><span data-stu-id="7dfa8-131">101</span></span>|<span data-ttu-id="7dfa8-132">101</span><span class="sxs-lookup"><span data-stu-id="7dfa8-132">101</span></span>|  
|<span data-ttu-id="7dfa8-133">LastName</span><span class="sxs-lookup"><span data-stu-id="7dfa8-133">LastName</span></span>|<span data-ttu-id="7dfa8-134">Smith</span><span class="sxs-lookup"><span data-stu-id="7dfa8-134">Smith</span></span>|<span data-ttu-id="7dfa8-135">Smith</span><span class="sxs-lookup"><span data-stu-id="7dfa8-135">Smith</span></span>|<span data-ttu-id="7dfa8-136">Smith</span><span class="sxs-lookup"><span data-stu-id="7dfa8-136">Smith</span></span>|  
|<span data-ttu-id="7dfa8-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="7dfa8-137">FirstName</span></span>|<span data-ttu-id="7dfa8-138">Bob</span><span class="sxs-lookup"><span data-stu-id="7dfa8-138">Bob</span></span>|<span data-ttu-id="7dfa8-139">Bob</span><span class="sxs-lookup"><span data-stu-id="7dfa8-139">Bob</span></span>|<span data-ttu-id="7dfa8-140">Bob</span><span class="sxs-lookup"><span data-stu-id="7dfa8-140">Bob</span></span>|  
  
 <span data-ttu-id="7dfa8-141">V 13:01, User2 přečte stejný řádek.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="7dfa8-142">V 13:03 uživatele změní **Jméno z** "Bob" na "Robert" a aktualizuje databázi.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="7dfa8-143">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="7dfa8-143">Column name</span></span>|<span data-ttu-id="7dfa8-144">Původní hodnota</span><span class="sxs-lookup"><span data-stu-id="7dfa8-144">Original value</span></span>|<span data-ttu-id="7dfa8-145">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="7dfa8-145">Current value</span></span>|<span data-ttu-id="7dfa8-146">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="7dfa8-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="7dfa8-147">CustID</span><span class="sxs-lookup"><span data-stu-id="7dfa8-147">CustID</span></span>|<span data-ttu-id="7dfa8-148">101</span><span class="sxs-lookup"><span data-stu-id="7dfa8-148">101</span></span>|<span data-ttu-id="7dfa8-149">101</span><span class="sxs-lookup"><span data-stu-id="7dfa8-149">101</span></span>|<span data-ttu-id="7dfa8-150">101</span><span class="sxs-lookup"><span data-stu-id="7dfa8-150">101</span></span>|  
|<span data-ttu-id="7dfa8-151">LastName</span><span class="sxs-lookup"><span data-stu-id="7dfa8-151">LastName</span></span>|<span data-ttu-id="7dfa8-152">Smith</span><span class="sxs-lookup"><span data-stu-id="7dfa8-152">Smith</span></span>|<span data-ttu-id="7dfa8-153">Smith</span><span class="sxs-lookup"><span data-stu-id="7dfa8-153">Smith</span></span>|<span data-ttu-id="7dfa8-154">Smith</span><span class="sxs-lookup"><span data-stu-id="7dfa8-154">Smith</span></span>|  
|<span data-ttu-id="7dfa8-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="7dfa8-155">FirstName</span></span>|<span data-ttu-id="7dfa8-156">Bob</span><span class="sxs-lookup"><span data-stu-id="7dfa8-156">Bob</span></span>|<span data-ttu-id="7dfa8-157">Robert</span><span class="sxs-lookup"><span data-stu-id="7dfa8-157">Robert</span></span>|<span data-ttu-id="7dfa8-158">Bob</span><span class="sxs-lookup"><span data-stu-id="7dfa8-158">Bob</span></span>|  
  
 <span data-ttu-id="7dfa8-159">Aktualizace je úspěšná, protože hodnoty v databázi v době aktualizace odpovídají původním hodnotám, které uživatelmá 2.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="7dfa8-160">V 13:05 uživatel1 změní křestní jméno "Bob" na "James" a pokusí se aktualizovat řádek.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="7dfa8-161">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="7dfa8-161">Column name</span></span>|<span data-ttu-id="7dfa8-162">Původní hodnota</span><span class="sxs-lookup"><span data-stu-id="7dfa8-162">Original value</span></span>|<span data-ttu-id="7dfa8-163">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="7dfa8-163">Current value</span></span>|<span data-ttu-id="7dfa8-164">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="7dfa8-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="7dfa8-165">CustID</span><span class="sxs-lookup"><span data-stu-id="7dfa8-165">CustID</span></span>|<span data-ttu-id="7dfa8-166">101</span><span class="sxs-lookup"><span data-stu-id="7dfa8-166">101</span></span>|<span data-ttu-id="7dfa8-167">101</span><span class="sxs-lookup"><span data-stu-id="7dfa8-167">101</span></span>|<span data-ttu-id="7dfa8-168">101</span><span class="sxs-lookup"><span data-stu-id="7dfa8-168">101</span></span>|  
|<span data-ttu-id="7dfa8-169">LastName</span><span class="sxs-lookup"><span data-stu-id="7dfa8-169">LastName</span></span>|<span data-ttu-id="7dfa8-170">Smith</span><span class="sxs-lookup"><span data-stu-id="7dfa8-170">Smith</span></span>|<span data-ttu-id="7dfa8-171">Smith</span><span class="sxs-lookup"><span data-stu-id="7dfa8-171">Smith</span></span>|<span data-ttu-id="7dfa8-172">Smith</span><span class="sxs-lookup"><span data-stu-id="7dfa8-172">Smith</span></span>|  
|<span data-ttu-id="7dfa8-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="7dfa8-173">FirstName</span></span>|<span data-ttu-id="7dfa8-174">Bob</span><span class="sxs-lookup"><span data-stu-id="7dfa8-174">Bob</span></span>|<span data-ttu-id="7dfa8-175">James</span><span class="sxs-lookup"><span data-stu-id="7dfa8-175">James</span></span>|<span data-ttu-id="7dfa8-176">Robert</span><span class="sxs-lookup"><span data-stu-id="7dfa8-176">Robert</span></span>|  
  
 <span data-ttu-id="7dfa8-177">V tomto okamžiku User1 narazí na optimistické narušení souběžnosti, protože hodnota v databázi ("Robert") již neodpovídá původní hodnotu, která User1 očekával ("Bob").</span><span class="sxs-lookup"><span data-stu-id="7dfa8-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="7dfa8-178">Porušení souběžnosti jednoduše vám umožní vědět, že aktualizace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="7dfa8-179">Nyní je třeba rozhodnout, zda přepsat změny zadané User2 se změnami zadanými User1, nebo zrušit změny uživatelem1.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="7dfa8-180">Testování pro optimistické porušení souběžnosti</span><span class="sxs-lookup"><span data-stu-id="7dfa8-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="7dfa8-181">Existuje několik technik pro testování pro narušení optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="7dfa8-182">Jeden zahrnuje včetně sloupce časového razítka v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="7dfa8-183">Databáze běžně poskytují funkce časového razítka, které lze použít k identifikaci data a času, kdy byl záznam naposledy aktualizován.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="7dfa8-184">Pomocí této techniky je sloupec časového razítka zahrnut do definice tabulky.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="7dfa8-185">Při každé aktualizaci záznamu je časové razítko aktualizováno tak, aby odráželo aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="7dfa8-186">V testu pro optimistické porušení souběžnosti sloupec časového razítka je vrácena s libovolný dotaz na obsah tabulky.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="7dfa8-187">Při pokusu o aktualizaci je hodnota časového razítka v databázi porovnána s původní hodnotou časového razítka obsaženou v upraveném řádku.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="7dfa8-188">Pokud se shodují, aktualizace se provede a sloupec časového razítka se aktualizuje s aktuálním časem tak, aby odrážely aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="7dfa8-189">Pokud se neshodují, došlo k narušení optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="7dfa8-190">Další technika pro testování pro narušení optimistické souběžnosti je ověřit, že všechny původní hodnoty sloupců v řádku stále odpovídají těm, které jsou nalezeny v databázi.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="7dfa8-191">Zvažte například následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="7dfa8-191">For example, consider the following query:</span></span>  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="7dfa8-192">Chcete-li otestovat optimistické porušení souběžnosti při aktualizaci řádku v **tabulce1**, vydáte následující příkaz UPDATE:</span><span class="sxs-lookup"><span data-stu-id="7dfa8-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="7dfa8-193">Tak dlouho, dokud původní hodnoty odpovídají hodnotám v databázi, aktualizace se provádí.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="7dfa8-194">Pokud byla změněna hodnota, aktualizace nebude měnit řádek, protože klauzule WHERE nenajde shodu.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="7dfa8-195">Všimněte si, že se doporučuje vždy vrátit jedinečnou hodnotu primárního klíče v dotazu.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="7dfa8-196">V opačném případě předchozí příkaz UPDATE může aktualizovat více než jeden řádek, což nemusí být váš záměr.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="7dfa8-197">Pokud sloupec ve zdroji dat umožňuje null, bude pravděpodobně nutné rozšířit klauzuli WHERE, abyste zkontrolovali odpovídající nulový odkaz v místní tabulce a ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="7dfa8-198">Například následující příkaz UPDATE ověří, zda nulový odkaz v místním řádku stále odpovídá nulovému odkazu ve zdroji dat nebo že hodnota v místním řádku stále odpovídá hodnotě ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="7dfa8-199">Můžete také použít méně omezující kritéria při použití optimistického modelu souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="7dfa8-200">Například použití pouze sloupce primárníklíč v where klauzule způsobí, že data přepsat bez ohledu na to, zda ostatní sloupce byly aktualizovány od posledního dotazu.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="7dfa8-201">Klauzuli WHERE můžete také použít pouze pro určité sloupce, což vede k přepsání dat, pokud nebyla od posledního dotazování aktualizována určitá pole.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="7dfa8-202">Událost DataAdapter.RowUpdated</span><span class="sxs-lookup"><span data-stu-id="7dfa8-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="7dfa8-203">**RowUpdated** událost objektu <xref:System.Data.Common.DataAdapter> lze použít ve spojení s technikami popsanými výše, poskytnout oznámení o použití optimistické porušení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="7dfa8-204">**RowUpdated** dochází po každém pokusu o **aktualizaci upravený** řádek z **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="7dfa8-205">To umožňuje přidat speciální kód zpracování, včetně zpracování, když dojde k výjimce, přidání vlastní chudinských informací, přidání logiky opakování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="7dfa8-206">Objekt <xref:System.Data.Common.RowUpdatedEventArgs> vrátí **vlastnost RecordsAffected** obsahující počet řádků ovlivněných určitým příkazem aktualizace pro upravený řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="7dfa8-207">Nastavením příkazu update pro testování optimistické souběžnosti vrátí vlastnost **RecordsAffected** hodnotu 0, když došlo k narušení optimistické souběžnosti, protože nebyly aktualizovány žádné záznamy.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="7dfa8-208">Pokud se jedná o tento případ, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="7dfa8-209">Událost **RowUpdated** umožňuje zpracovat tento výskyt a vyhnout se výjimce nastavením příslušné hodnoty **RowUpdatedEventArgs.Status,** například **UpdateStatus.SkipCurrentRow**.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="7dfa8-210">Další informace o události **RowUpdated** naleznete v [tématu Zpracování událostí datového adaptéru](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="7dfa8-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="7dfa8-211">Volitelně můžete nastavit **DataAdapter.ContinueUpdateOnError** na **true**, před voláním **Update**a reagovat na informace o chybě uložené ve vlastnosti **RowError** určitého řádku po dokončení **aktualizace.**</span><span class="sxs-lookup"><span data-stu-id="7dfa8-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="7dfa8-212">Další informace naleznete v [tématu Informace o chybě řádku](./dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="7dfa8-212">For more information, see [Row Error Information](./dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="7dfa8-213">Optimistický příklad souběžnosti</span><span class="sxs-lookup"><span data-stu-id="7dfa8-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="7dfa8-214">Následuje jednoduchý příklad, který nastaví **UpdateCommand** **DataAdapter** otestovat optimistické souběžnosti a potom používá **RowUpdated** událost k testování optimistických porušení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="7dfa8-215">Při výskytu narušení optimistické souběžnosti aplikace nastaví **RowError** řádku, který byla vydána aktualizace tak, aby odrážela optimistické porušení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="7dfa8-216">Všimněte si, že hodnoty parametrů předané klauzuli WHERE příkazu UPDATE jsou mapovány na **původní** hodnoty příslušných sloupců.</span><span class="sxs-lookup"><span data-stu-id="7dfa8-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7dfa8-217">Viz také</span><span class="sxs-lookup"><span data-stu-id="7dfa8-217">See also</span></span>

- [<span data-ttu-id="7dfa8-218">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7dfa8-218">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="7dfa8-219">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="7dfa8-219">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="7dfa8-220">Informace o chybě na řádku</span><span class="sxs-lookup"><span data-stu-id="7dfa8-220">Row Error Information</span></span>](./dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="7dfa8-221">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="7dfa8-221">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="7dfa8-222">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7dfa8-222">ADO.NET Overview</span></span>](ado-net-overview.md)
