---
title: "System.Transactions – integrace s SQL serverem"
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
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2299a974fc9c6af9e5fba0de6e16ab72de8b5e10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="9130e-102">System.Transactions – integrace s SQL serverem</span><span class="sxs-lookup"><span data-stu-id="9130e-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="9130e-103">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Verze 2.0 zavedená rozhraní transakce, které je přístupné prostřednictvím <xref:System.Transactions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9130e-103">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="9130e-104">Toto rozhraní zpřístupní transakce způsobem, který je v plně integrovaná [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], včetně [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9130e-104">This framework exposes transactions in a way that is fully integrated in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], including [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 <span data-ttu-id="9130e-105">Kromě těchto vylepšení programovatelnosti <xref:System.Transactions> a [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] můžou spolupracovat a koordinovat optimalizace při práci s transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-105">In addition to the programmability enhancements, <xref:System.Transactions> and [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="9130e-106">Je možné zvýšit transakce lightweight (místní) transakci, která bude automaticky povýšen na plně distribuovanou transakci na podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="9130e-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="9130e-107">Počínaje [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> podporuje možné zvýšit transakce při práci s [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9130e-107">Starting with [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9130e-108">Možné zvýšit transakce nevyvolá přidaném starat se o distribuované transakce Pokud přidaném režie není nutné.</span><span class="sxs-lookup"><span data-stu-id="9130e-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="9130e-109">Jsou možné zvýšit transakce automatické vyžadují bez zásahu od vývojáře.</span><span class="sxs-lookup"><span data-stu-id="9130e-109">Promotable transactions are automatic require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="9130e-110">Možné zvýšit transakce jsou k dispozici pouze při použití [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server (`SqlClient`) s [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9130e-110">Promotable transactions are only available when you use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for SQL Server (`SqlClient`) with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="9130e-111">Vytváření možné zvýšit transakcí</span><span class="sxs-lookup"><span data-stu-id="9130e-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="9130e-112">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider pro SQL Server poskytuje podporu pro možné zvýšit transakce, které jsou zpracovány prostřednictvím třídy v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9130e-112">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="9130e-113">Možné zvýšit transakce optimalizovat distribuované transakce odložit vytváření distribuované transakce, dokud nebude potřeba.</span><span class="sxs-lookup"><span data-stu-id="9130e-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="9130e-114">Pokud jen jeden správce prostředků se vyžaduje, dojde k žádné distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9130e-115">Ve scénáři částečně důvěryhodné <xref:System.Transactions.DistributedTransactionPermission> je požadován při transakci je povýšit na distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="9130e-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="9130e-116">Scénáře možné zvýšit transakce</span><span class="sxs-lookup"><span data-stu-id="9130e-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="9130e-117">Distribuované transakce obvykle využívají významné systémové prostředky, je spravováno nástrojem Microsoft Distributed Transaction Coordinator (MS DTC), která integruje všechny správce prostředků získat přístup v rámci transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="9130e-118">Je možné zvýšit transakce speciální formu <xref:System.Transactions> transakci, která efektivně deleguje práce, kterou je jednoduchý [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] transaction.</span></span> <span data-ttu-id="9130e-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, a [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] koordinaci pracovní zahrnuté ve zpracování transakcí, podle potřeby zvýšení jeho úrovně na úplné distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="9130e-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="9130e-120">Výhodou použití možné zvýšit transakcí je, že po otevření připojení pomocí aktivní <xref:System.Transactions.TransactionScope> transakce a žádná další připojení jsou otevřené, potvrzení transakce jako lightweight transakce, místo by docházelo k další Režijní náklady na úplné distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="9130e-121">Klíčová slova řetězec připojení</span><span class="sxs-lookup"><span data-stu-id="9130e-121">Connection String Keywords</span></span>  
 <span data-ttu-id="9130e-122"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> Vlastnost podporuje klíčové slovo, `Enlist`, což znamená, zda <xref:System.Data.SqlClient> rozpozná transakční kontexty a automaticky zařazení připojení v distribuované transakci.</span><span class="sxs-lookup"><span data-stu-id="9130e-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="9130e-123">Pokud `Enlist=true`, je připojení automaticky zařadit v aktuálním kontextu transakce otevírání vlákno.</span><span class="sxs-lookup"><span data-stu-id="9130e-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="9130e-124">Pokud `Enlist=false`, `SqlClient` připojení nekomunikuje s distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="9130e-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="9130e-125">Výchozí hodnota pro `Enlist` hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="9130e-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="9130e-126">Pokud `Enlist` není zadaný v připojovacím řetězci, toto připojení je automaticky uvedené v distribuované transakci, pokud se jeden detekuje po otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="9130e-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="9130e-127">`Transaction Binding` Klíčová slova v <xref:System.Data.SqlClient.SqlConnection> připojovací řetězec řízení připojení přidružení zařazené `System.Transactions` transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="9130e-128">Je také k dispozici prostřednictvím <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> vlastnost <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="9130e-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="9130e-129">Následující tabulka popisuje možné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9130e-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="9130e-130">– Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="9130e-130">Keyword</span></span>|<span data-ttu-id="9130e-131">Popis</span><span class="sxs-lookup"><span data-stu-id="9130e-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9130e-132">Implicitní odpojení</span><span class="sxs-lookup"><span data-stu-id="9130e-132">Implicit Unbind</span></span>|<span data-ttu-id="9130e-133">Výchozí nastavení</span><span class="sxs-lookup"><span data-stu-id="9130e-133">The default.</span></span> <span data-ttu-id="9130e-134">Připojení odpojí od transakce, až skončí, přepnutí zpět do režimu automatického zápisu režimu.</span><span class="sxs-lookup"><span data-stu-id="9130e-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="9130e-135">Explicitní odpojení</span><span class="sxs-lookup"><span data-stu-id="9130e-135">Explicit Unbind</span></span>|<span data-ttu-id="9130e-136">Připojení zůstane připojený k transakci, dokud nezavře transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="9130e-137">Připojení se nezdaří, pokud přidružené transakce není aktivní nebo neodpovídá <xref:System.Transactions.Transaction.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="9130e-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="9130e-138">Pomocí TransactionScope</span><span class="sxs-lookup"><span data-stu-id="9130e-138">Using TransactionScope</span></span>  
 <span data-ttu-id="9130e-139"><xref:System.Transactions.TransactionScope> Třída provede blok kódu transakční pomocí implicitně zapsání připojení v distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="9130e-140">Je třeba zavolat <xref:System.Transactions.TransactionScope.Complete%2A> metoda na konci <xref:System.Transactions.TransactionScope> blok před zároveň je nechává.</span><span class="sxs-lookup"><span data-stu-id="9130e-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="9130e-141">Opouštění bloku vyvolá <xref:System.Transactions.TransactionScope.Dispose%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9130e-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="9130e-142">Pokud byla vyvolána výjimka, že příčiny, které se považuje za kód, který nechte oboru, transakce zrušena.</span><span class="sxs-lookup"><span data-stu-id="9130e-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="9130e-143">Doporučujeme vám, že používáte `using` blok k Ujistěte se, že <xref:System.Transactions.TransactionScope.Dispose%2A> se volá na <xref:System.Transactions.TransactionScope> objekt při použití blokovat je byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="9130e-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="9130e-144">Selhání potvrzení nebo vrácení čekající transakce může výrazně poškodit výkon, protože výchozí časový limit pro <xref:System.Transactions.TransactionScope> je jedna minuta.</span><span class="sxs-lookup"><span data-stu-id="9130e-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="9130e-145">Pokud nepoužijete `using` příkaz, je třeba provést všechny pracovní v `Try` blokovat a explicitně volání <xref:System.Transactions.TransactionScope.Dispose%2A> metoda v `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="9130e-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="9130e-146">Pokud dojde k výjimce v <xref:System.Transactions.TransactionScope>, transakce je označena jako nekonzistentní a opuštění.</span><span class="sxs-lookup"><span data-stu-id="9130e-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="9130e-147">Bude vrácena zpět, když <xref:System.Transactions.TransactionScope> je zrušen.</span><span class="sxs-lookup"><span data-stu-id="9130e-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="9130e-148">Pokud dojde k žádná výjimka, potvrzení zúčastněných transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9130e-149">`TransactionScope` Třída vytvoří transakce s <xref:System.Transactions.Transaction.IsolationLevel%2A> z `Serializable` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="9130e-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="9130e-150">V závislosti na vaší aplikace můžete chtít zvažte snížení úrovně izolace, aby se zabránilo vysoké kolizí ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9130e-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9130e-151">Doporučujeme provádět jenom aktualizace, vložení, a odstraní v rámci distribuované transakce, protože jejich spotřebovávat prostředky významné databáze.</span><span class="sxs-lookup"><span data-stu-id="9130e-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="9130e-152">Příkazy SELECT může zbytečně zamknout databáze prostředků, a v některých scénářích možná budete muset použít transakce pro vybere.</span><span class="sxs-lookup"><span data-stu-id="9130e-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="9130e-153">Všechny pracovní databáze by mělo být provedeno v oboru transakce, pokud se týká jiných správci zpracovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="9130e-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="9130e-154">I když k výjimce v oboru transakce zabraňují transakce potvrzení, <xref:System.Transactions.TransactionScope> třídy nemá vybavení pro vrácení zpět všechny změny kódu udělal mimo obor vlastní transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="9130e-155">Pokud máte určitou akci při transakce je vrácena zpět, je nutné napsat vlastní implementaci <xref:System.Transactions.IEnlistmentNotification> rozhraní a explicitně uvést v transakci.</span><span class="sxs-lookup"><span data-stu-id="9130e-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9130e-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="9130e-156">Example</span></span>  
 <span data-ttu-id="9130e-157">Práce s <xref:System.Transactions> vyžaduje, abyste měli odkaz na System.Transactions.dll.</span><span class="sxs-lookup"><span data-stu-id="9130e-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="9130e-158">Následující funkce ukazuje, jak vytvořit možné zvýšit transakce proti dva různé instance systému SQL Server, reprezentována dva různé <xref:System.Data.SqlClient.SqlConnection> objekty, které jsou uzavřen do <xref:System.Transactions.TransactionScope> bloku.</span><span class="sxs-lookup"><span data-stu-id="9130e-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="9130e-159">Kód vytvoří <xref:System.Transactions.TransactionScope> blokovat s `using` příkaz a otevře první připojení, které automaticky využívá ho <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="9130e-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="9130e-160">Transakce je původně uvedené jako lightweight transakce, není úplná distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="9130e-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="9130e-161">Druhé připojení je v uvedené <xref:System.Transactions.TransactionScope> pouze v případě, že příkaz v prvním připojení nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="9130e-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="9130e-162">Po otevření druhé připojení transakce automaticky povýšen na úplné distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="9130e-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="9130e-163"><xref:System.Transactions.TransactionScope.Complete%2A> Je volána metoda, která potvrdí transakce pouze v případě, že byly vyvolány žádné výjimky.</span><span class="sxs-lookup"><span data-stu-id="9130e-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="9130e-164">Pokud byla vyvolána výjimka v libovolném bodě <xref:System.Transactions.TransactionScope> bloku `Complete` bude nebyla volána a bude distribuované transakce vrácení zpět, když <xref:System.Transactions.TransactionScope> je zveřejněn. na konci jeho `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="9130e-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="9130e-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="9130e-165">See Also</span></span>  
 [<span data-ttu-id="9130e-166">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="9130e-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="9130e-167">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="9130e-167">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
