---
title: "Optimistickou metodu souběžného zpracování"
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
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4cc1ac0446f13bcc6bc1c8262eae5716302c3e2d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="b8970-102">Optimistickou metodu souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="b8970-102">Optimistic Concurrency</span></span>
<span data-ttu-id="b8970-103">V prostředí, jsou dva modely pro aktualizace dat v databázi: optimistickou metodu souběžného a pesimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="b8970-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="b8970-104"><xref:System.Data.DataSet> Objekt je navržen pro podporu použití optimistickou metodu souběžného pro dlouho běžící aktivity, jako je vzdálené komunikace dat a práce s daty.</span><span class="sxs-lookup"><span data-stu-id="b8970-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="b8970-105">Pesimistické souběžnosti zahrnuje uzamčení řádků ve zdroji dat k ostatním uživatelům zabránit upravovat data způsobem, který ovlivňuje aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="b8970-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="b8970-106">V pesimistické modelu když uživatel provede akci, která způsobí zámek má být použita, nelze jiní uživatelé provádět akce, které by byl v konfliktu s zámek dokud uvolněním vlastníka zámku.</span><span class="sxs-lookup"><span data-stu-id="b8970-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="b8970-107">Tento model se používá hlavně v prostředích, kde je těžká kolizí pro data, aby náklady na ochranu dat s zámky je menší než náklady na transakce vrácení zpět, jestliže dojde ke konfliktu souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="b8970-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="b8970-108">Proto v modelu pesimistické souběžnosti vytvoří uživatel, který aktualizuje řádek zámek.</span><span class="sxs-lookup"><span data-stu-id="b8970-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="b8970-109">Dokud se uživatel má dokončení aktualizace a vydání zámek, nikdo jiný, můžete změnit příslušném řádku.</span><span class="sxs-lookup"><span data-stu-id="b8970-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="b8970-110">Z tohoto důvodu je pesimistické souběžnosti nejlépe implementována, pokud doby uzamčení bude krátký jako programový zpracování záznamů.</span><span class="sxs-lookup"><span data-stu-id="b8970-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="b8970-111">Pesimistické souběžnosti není škálovatelné možnost, když jsou uživatelé interakci s daty a způsobuje záznamů se uzamkne za relativně velké období.</span><span class="sxs-lookup"><span data-stu-id="b8970-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8970-112">Pokud je potřeba aktualizovat více řádků v rámci jedné operace, pak vytvoření transakce je více škálovatelného než použití pesimistické zamykání.</span><span class="sxs-lookup"><span data-stu-id="b8970-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="b8970-113">Uživatelé, kteří používají optimistickou metodu souběžného naopak neblokují řádku při jeho čtení.</span><span class="sxs-lookup"><span data-stu-id="b8970-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="b8970-114">Pokud chce uživatel o aktualizaci řádku, aplikace musí určit, zda jiný uživatel změnil řádek od čtení.</span><span class="sxs-lookup"><span data-stu-id="b8970-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="b8970-115">Optimistickou metodu souběžného se obvykle používá v prostředích s nízkou kolizí pro data.</span><span class="sxs-lookup"><span data-stu-id="b8970-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="b8970-116">Optimistickou metodu souběžného zvyšuje výkon, protože se vyžaduje žádné uzamčení záznamů a zamykání záznamů vyžaduje další server prostředků.</span><span class="sxs-lookup"><span data-stu-id="b8970-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="b8970-117">Aby byla zachována uzamčení záznamů, je taky požadované trvalé připojení k databázovému serveru.</span><span class="sxs-lookup"><span data-stu-id="b8970-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="b8970-118">Protože to není případu v modelu optimistickou metodu souběžného, připojení k serveru jsou zdarma k obsluze větší počet klientů v méně času.</span><span class="sxs-lookup"><span data-stu-id="b8970-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="b8970-119">Ve model optimistickou metodu souběžného narušení je považován za došlo, pokud po uživatel obdrží hodnotu z databáze, jiný uživatel změní hodnotu před první uživatel se pokusil upravit.</span><span class="sxs-lookup"><span data-stu-id="b8970-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="b8970-120">Jak server přeloží narušení souběžného zpracování se zobrazí nejlépe prostřednictvím první popisu v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b8970-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="b8970-121">V následujících tabulkách použijte příklad optimistickou metodu souběžného.</span><span class="sxs-lookup"><span data-stu-id="b8970-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="b8970-122">Uživatel1 v 13:00:00, čte řádek z databáze s následujícími hodnotami:</span><span class="sxs-lookup"><span data-stu-id="b8970-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="b8970-123">**CustID příjmení jméno**</span><span class="sxs-lookup"><span data-stu-id="b8970-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="b8970-124">101 Bob Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="b8970-125">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="b8970-125">Column name</span></span>|<span data-ttu-id="b8970-126">Původní hodnotu</span><span class="sxs-lookup"><span data-stu-id="b8970-126">Original value</span></span>|<span data-ttu-id="b8970-127">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="b8970-127">Current value</span></span>|<span data-ttu-id="b8970-128">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="b8970-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="b8970-129">CustID</span><span class="sxs-lookup"><span data-stu-id="b8970-129">CustID</span></span>|<span data-ttu-id="b8970-130">101</span><span class="sxs-lookup"><span data-stu-id="b8970-130">101</span></span>|<span data-ttu-id="b8970-131">101</span><span class="sxs-lookup"><span data-stu-id="b8970-131">101</span></span>|<span data-ttu-id="b8970-132">101</span><span class="sxs-lookup"><span data-stu-id="b8970-132">101</span></span>|  
|<span data-ttu-id="b8970-133">LastName</span><span class="sxs-lookup"><span data-stu-id="b8970-133">LastName</span></span>|<span data-ttu-id="b8970-134">Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-134">Smith</span></span>|<span data-ttu-id="b8970-135">Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-135">Smith</span></span>|<span data-ttu-id="b8970-136">Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-136">Smith</span></span>|  
|<span data-ttu-id="b8970-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="b8970-137">FirstName</span></span>|<span data-ttu-id="b8970-138">Bob</span><span class="sxs-lookup"><span data-stu-id="b8970-138">Bob</span></span>|<span data-ttu-id="b8970-139">Bob</span><span class="sxs-lookup"><span data-stu-id="b8970-139">Bob</span></span>|<span data-ttu-id="b8970-140">Bob</span><span class="sxs-lookup"><span data-stu-id="b8970-140">Bob</span></span>|  
  
 <span data-ttu-id="b8970-141">V 13:01:00 uživatel2 přečte na stejném řádku.</span><span class="sxs-lookup"><span data-stu-id="b8970-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="b8970-142">V 13:03:00, uživatel2 změny **FirstName** z "Bob" na "Robert" a aktualizaci databáze.</span><span class="sxs-lookup"><span data-stu-id="b8970-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="b8970-143">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="b8970-143">Column name</span></span>|<span data-ttu-id="b8970-144">Původní hodnotu</span><span class="sxs-lookup"><span data-stu-id="b8970-144">Original value</span></span>|<span data-ttu-id="b8970-145">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="b8970-145">Current value</span></span>|<span data-ttu-id="b8970-146">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="b8970-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="b8970-147">CustID</span><span class="sxs-lookup"><span data-stu-id="b8970-147">CustID</span></span>|<span data-ttu-id="b8970-148">101</span><span class="sxs-lookup"><span data-stu-id="b8970-148">101</span></span>|<span data-ttu-id="b8970-149">101</span><span class="sxs-lookup"><span data-stu-id="b8970-149">101</span></span>|<span data-ttu-id="b8970-150">101</span><span class="sxs-lookup"><span data-stu-id="b8970-150">101</span></span>|  
|<span data-ttu-id="b8970-151">LastName</span><span class="sxs-lookup"><span data-stu-id="b8970-151">LastName</span></span>|<span data-ttu-id="b8970-152">Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-152">Smith</span></span>|<span data-ttu-id="b8970-153">Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-153">Smith</span></span>|<span data-ttu-id="b8970-154">Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-154">Smith</span></span>|  
|<span data-ttu-id="b8970-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="b8970-155">FirstName</span></span>|<span data-ttu-id="b8970-156">Bob</span><span class="sxs-lookup"><span data-stu-id="b8970-156">Bob</span></span>|<span data-ttu-id="b8970-157">Robert</span><span class="sxs-lookup"><span data-stu-id="b8970-157">Robert</span></span>|<span data-ttu-id="b8970-158">Bob</span><span class="sxs-lookup"><span data-stu-id="b8970-158">Bob</span></span>|  
  
 <span data-ttu-id="b8970-159">Aktualizace úspěšná, protože původní hodnoty, které má uživatel2 shodují s hodnotami v databázi v době aktualizace.</span><span class="sxs-lookup"><span data-stu-id="b8970-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="b8970-160">V 13:05:00 uživatel1 změny jméno "Bob" na "James" a pokus o aktualizaci řádku.</span><span class="sxs-lookup"><span data-stu-id="b8970-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="b8970-161">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="b8970-161">Column name</span></span>|<span data-ttu-id="b8970-162">Původní hodnotu</span><span class="sxs-lookup"><span data-stu-id="b8970-162">Original value</span></span>|<span data-ttu-id="b8970-163">Aktuální hodnota</span><span class="sxs-lookup"><span data-stu-id="b8970-163">Current value</span></span>|<span data-ttu-id="b8970-164">Hodnota v databázi</span><span class="sxs-lookup"><span data-stu-id="b8970-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="b8970-165">CustID</span><span class="sxs-lookup"><span data-stu-id="b8970-165">CustID</span></span>|<span data-ttu-id="b8970-166">101</span><span class="sxs-lookup"><span data-stu-id="b8970-166">101</span></span>|<span data-ttu-id="b8970-167">101</span><span class="sxs-lookup"><span data-stu-id="b8970-167">101</span></span>|<span data-ttu-id="b8970-168">101</span><span class="sxs-lookup"><span data-stu-id="b8970-168">101</span></span>|  
|<span data-ttu-id="b8970-169">LastName</span><span class="sxs-lookup"><span data-stu-id="b8970-169">LastName</span></span>|<span data-ttu-id="b8970-170">Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-170">Smith</span></span>|<span data-ttu-id="b8970-171">Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-171">Smith</span></span>|<span data-ttu-id="b8970-172">Smith</span><span class="sxs-lookup"><span data-stu-id="b8970-172">Smith</span></span>|  
|<span data-ttu-id="b8970-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="b8970-173">FirstName</span></span>|<span data-ttu-id="b8970-174">Bob</span><span class="sxs-lookup"><span data-stu-id="b8970-174">Bob</span></span>|<span data-ttu-id="b8970-175">James</span><span class="sxs-lookup"><span data-stu-id="b8970-175">James</span></span>|<span data-ttu-id="b8970-176">Robert</span><span class="sxs-lookup"><span data-stu-id="b8970-176">Robert</span></span>|  
  
 <span data-ttu-id="b8970-177">V tomto okamžiku uživatel1 zaznamená porušení optimistickou metodu souběžného, protože hodnota v databázi ("Robert") už odpovídá původní hodnotu Uživatel1 byl očekáván ("Bob").</span><span class="sxs-lookup"><span data-stu-id="b8970-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="b8970-178">Porušení souběžnosti jednoduše umožňuje vědět, že aktualizace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="b8970-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="b8970-179">Teď rozhodnutí musí být zda přepsat změny poskytl uživatel2 se změnami poskytl uživatel1, nebo zrušit změny provedené User1.</span><span class="sxs-lookup"><span data-stu-id="b8970-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="b8970-180">Testování pro porušení optimistickou metodu souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="b8970-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="b8970-181">Existuje několik postupů pro testování pro porušení optimistickou metodu souběžného.</span><span class="sxs-lookup"><span data-stu-id="b8970-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="b8970-182">Jeden zahrnuje, včetně sloupec časového razítka v tabulce.</span><span class="sxs-lookup"><span data-stu-id="b8970-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="b8970-183">Databáze obvykle poskytují funkce časové razítko, které lze použít k identifikaci datum a čas poslední aktualizace záznamu.</span><span class="sxs-lookup"><span data-stu-id="b8970-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="b8970-184">Touto technikou sloupec časového razítka je součástí definice tabulky.</span><span class="sxs-lookup"><span data-stu-id="b8970-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="b8970-185">Při každé aktualizaci záznamu časové razítko je aktualizována tak, aby odrážela aktuální datum a čas.</span><span class="sxs-lookup"><span data-stu-id="b8970-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="b8970-186">V testu pro optimistickou metodu souběžného narušení je vrácena sloupec časového razítka s jakýkoli dotaz obsahu tabulky.</span><span class="sxs-lookup"><span data-stu-id="b8970-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="b8970-187">Při pokusu o aktualizaci, hodnota časového razítka v databázi se porovná na původní hodnotu časové razítko, které jsou obsažené v upravené řádek.</span><span class="sxs-lookup"><span data-stu-id="b8970-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="b8970-188">Pokud se shodují, se provádí aktualizace a sloupec časového razítka je aktualizována tak, aby odrážela aktualizace aktuální čas.</span><span class="sxs-lookup"><span data-stu-id="b8970-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="b8970-189">Pokud se neshodují, došlo k porušení optimistickou metodu souběžného.</span><span class="sxs-lookup"><span data-stu-id="b8970-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="b8970-190">Jiné technika pro testování pro porušení optimistickou metodu souběžného je ověřit, jestli všechny původní hodnoty sloupce v řádku stále shodují s těmi nalezen v databázi.</span><span class="sxs-lookup"><span data-stu-id="b8970-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="b8970-191">Zvažte například následující dotaz:</span><span class="sxs-lookup"><span data-stu-id="b8970-191">For example, consider the following query:</span></span>  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="b8970-192">Chcete otestovat porušení optimistickou metodu souběžného při aktualizaci řádek v **tabulky1**, by vydat příkaz následující aktualizace:</span><span class="sxs-lookup"><span data-stu-id="b8970-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="b8970-193">Tak dlouho, dokud původní hodnoty shodují s hodnotami v databázi, se provádí aktualizace.</span><span class="sxs-lookup"><span data-stu-id="b8970-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="b8970-194">Pokud byla hodnota změněna, aktualizace nebude řádek upravit, protože klauzule WHERE nebude možné najít shoda.</span><span class="sxs-lookup"><span data-stu-id="b8970-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="b8970-195">Všimněte si, že se doporučuje se vždy vrátit jedinečné hodnoty primárního klíče v dotazu.</span><span class="sxs-lookup"><span data-stu-id="b8970-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="b8970-196">Předchozí příkaz UPDATE, jinak může aktualizovat více než jeden řádek, který nemusí být vašich představ.</span><span class="sxs-lookup"><span data-stu-id="b8970-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="b8970-197">Pokud sloupec na zdroj dat umožňuje hodnoty Null, musíte rozšířit vaše klauzule WHERE Zkontrolujte odpovídající odkaz s hodnotou null v místní tabulky a ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="b8970-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="b8970-198">Například následující příkaz UPDATE ověřuje, že odkaz s hodnotou null v místní řádku stále odpovídá odkaz na zdroj dat s hodnotou null, nebo hodnotu v místní řádku stále odpovídá hodnotě ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="b8970-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="b8970-199">Můžete také použít obecnější kritéria při použití model optimistickou metodu souběžného.</span><span class="sxs-lookup"><span data-stu-id="b8970-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="b8970-200">Například použití pouze primární klíčových sloupců v klauzuli WHERE způsobí, že data, která mají být přepsány bez ohledu na to, jestli ostatních sloupců byly aktualizovány od posledního dotazu.</span><span class="sxs-lookup"><span data-stu-id="b8970-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="b8970-201">Klauzule WHERE můžete taky použít pouze na konkrétní sloupce, výsledkem dat přepsáním Pokud konkrétní pole byly aktualizovány od jejich poslední dotaz.</span><span class="sxs-lookup"><span data-stu-id="b8970-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="b8970-202">Událost DataAdapter.RowUpdated</span><span class="sxs-lookup"><span data-stu-id="b8970-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="b8970-203">**RowUpdated** události <xref:System.Data.Common.DataAdapter> objekt lze použít ve spojení s technik popsaných výše, k poskytování oznámení do vaší aplikace optimistickou metodu souběžného porušení zásad.</span><span class="sxs-lookup"><span data-stu-id="b8970-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="b8970-204">**RowUpdated** dojde po každém pokusu o aktualizaci **změněné** řádek z **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="b8970-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="b8970-205">To umožňuje přidat kód pro zvláštní zpracování, včetně zpracováním, když dojde k výjimce, přidání informace o vlastní chybě, přidání logika opakovaných pokusů a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b8970-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="b8970-206"><xref:System.Data.Common.RowUpdatedEventArgs> Objektu vrátí **RecordsAffected** vlastnost obsahující počet řádků, které jsou ovlivněné příkaz konkrétní aktualizace pro upravené řádek v tabulce.</span><span class="sxs-lookup"><span data-stu-id="b8970-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="b8970-207">Příkaz update chcete otestovat optimistickou metodu souběžného nastavením **RecordsAffected** vlastnost, výsledkem je, vrátí hodnotu 0 při došlo k porušení optimistickou metodu souběžného, protože žádné záznamy se aktualizovaly.</span><span class="sxs-lookup"><span data-stu-id="b8970-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="b8970-208">Pokud je to tento případ, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b8970-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="b8970-209">**RowUpdated** událostí umožňuje zpracovávat tento výskyt a vyhnout se výjimka nastavením odpovídající **RowUpdatedEventArgs.Status** hodnotu, jako například  **UpdateStatus.SkipCurrentRow**.</span><span class="sxs-lookup"><span data-stu-id="b8970-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="b8970-210">Další informace o **RowUpdated** událostí, najdete v části [zpracování události DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="b8970-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="b8970-211">Volitelně můžete nastavit **DataAdapter.ContinueUpdateOnError** k **true**, před voláním **aktualizace**a reagovat na informace o chybě uložené v **RowError** vlastnost konkrétní řádek, kdy **aktualizace** byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="b8970-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="b8970-212">Další informace najdete v tématu [informace o chybě řádek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="b8970-212">For more information, see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="b8970-213">Příklad optimistickou metodu souběžného zpracování</span><span class="sxs-lookup"><span data-stu-id="b8970-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="b8970-214">Tady je jednoduchý příklad, který nastaví **vlastnost UpdateCommand** z **DataAdapter** chcete otestovat optimistickou metodu souběžného a použije je **RowUpdated** událostí k testování pro optimistickou metodu souběžného porušení.</span><span class="sxs-lookup"><span data-stu-id="b8970-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="b8970-215">Když dojde k porušení optimistickou metodu souběžného, nastaví aplikace **RowError** řádku, který aktualizace byl vydán pro tak, aby odrážela porušení optimistickou metodu souběžného.</span><span class="sxs-lookup"><span data-stu-id="b8970-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="b8970-216">Všimněte si, že hodnoty parametru předána do klauzule WHERE příkazu UPDATE jsou namapované na **původní** hodnoty jejich odpovídajících sloupců.</span><span class="sxs-lookup"><span data-stu-id="b8970-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
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
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
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
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName, connection);  
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
  
## <a name="see-also"></a><span data-ttu-id="b8970-217">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8970-217">See Also</span></span>  
 [<span data-ttu-id="b8970-218">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b8970-218">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="b8970-219">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="b8970-219">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="b8970-220">Informace o chybě na řádku</span><span class="sxs-lookup"><span data-stu-id="b8970-220">Row Error Information</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [<span data-ttu-id="b8970-221">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="b8970-221">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="b8970-222">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="b8970-222">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
