---
title: Integrace System.Transactions s SQL Serverem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 25b443d8234909a4d8525c2ce2b4e70c3baa337b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965222"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="2d4cc-102">Integrace System.Transactions s SQL Serverem</span><span class="sxs-lookup"><span data-stu-id="2d4cc-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="2d4cc-103">.NET Framework verze 2,0 představila transakční rozhraní, ke kterému lze přistupovat <xref:System.Transactions> prostřednictvím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="2d4cc-104">Toto rozhraní zpřístupňuje transakce způsobem, který je plně integrovaný do .NET Framework, včetně ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="2d4cc-105">Kromě vylepšení <xref:System.Transactions> programovatelnosti a ADO.NET můžou při práci s transakcemi spolupracovat při koordinaci optimalizací.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="2d4cc-106">Transakce promoící je odlehčená (místní) transakce, kterou lze automaticky zvýšit na plně distribuovanou transakci podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="2d4cc-107">Počínaje verzí ADO.NET 2,0 <xref:System.Data.SqlClient> podporuje transakce promoící při práci s SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="2d4cc-108">Transakce promoící nevyvolává přidanou režii distribuované transakce, pokud není nutná přidaná režie.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="2d4cc-109">Transakce s propagačními akcemi jsou automatické a od vývojářů nevyžadují žádný zásah.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="2d4cc-110">Transakce s přístupnými transakcemi jsou k dispozici, pouze pokud používáte`SqlClient`.NET Framework Zprostředkovatel dat pro SQL Server () s SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="2d4cc-111">Vytváření transakcí promoce</span><span class="sxs-lookup"><span data-stu-id="2d4cc-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="2d4cc-112">Poskytovatel .NET Framework pro SQL Server poskytuje podporu pro transakce, které jsou zpracovávány prostřednictvím tříd v oboru názvů .NET Framework <xref:System.Transactions> .</span><span class="sxs-lookup"><span data-stu-id="2d4cc-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="2d4cc-113">Transakce Promote optimalizuje distribuované transakce odložením vytvoření distribuované transakce, dokud ji nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="2d4cc-114">Pokud je vyžadován pouze jeden správce prostředků, neprobíhá žádná distribuovaná transakce.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d4cc-115">V částečně důvěryhodném scénáři <xref:System.Transactions.DistributedTransactionPermission> je vyžadován při povýšení transakce na distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="2d4cc-116">Scénáře transakcí s možností použití</span><span class="sxs-lookup"><span data-stu-id="2d4cc-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="2d4cc-117">Distribuované transakce obvykle využívají významné systémové prostředky spravované službou Microsoft DTC (Distributed Transaction Coordinator) (MS DTC), která integruje všechny správce prostředků, ke kterým se přistupovalo v transakci.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="2d4cc-118">Transakce typu promoe je speciální forma <xref:System.Transactions> transakce, která efektivně deleguje práci do jednoduché transakce SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="2d4cc-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>a SQL Server koordinovat práci, která je zapojená do zpracování transakce, a podle potřeby ji propagovat na úplnou distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="2d4cc-120">Výhodou použití transakcí s více instancemi je, že když je připojení otevřeno pomocí aktivní <xref:System.Transactions.TransactionScope> transakce a žádné jiné připojení není otevřeno, transakce je považována za odlehčenou transakci místo toho, aby vyplatila další Režie plné distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="2d4cc-121">Klíčová slova připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="2d4cc-121">Connection String Keywords</span></span>  
 <span data-ttu-id="2d4cc-122">Vlastnost podporuje klíčové slovo, které označuje, zda <xref:System.Data.SqlClient> bude detekovat transakční kontexty a automaticky zařadit připojení v distribuované transakci. `Enlist` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A></span><span class="sxs-lookup"><span data-stu-id="2d4cc-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="2d4cc-123">Pokud `Enlist=true`se připojení automaticky zařadí do kontextu aktuálního transakce otevřeného vlákna.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="2d4cc-124">Pokud `Enlist=false`připojenínekomunikuje sdistribuovanoutransakcí.`SqlClient`</span><span class="sxs-lookup"><span data-stu-id="2d4cc-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="2d4cc-125">Výchozí hodnota pro `Enlist` je true.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="2d4cc-126">Pokud `Enlist` není zadán v připojovacím řetězci, připojení je automaticky zařazeno do distribuované transakce, pokud je zjištěno při otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="2d4cc-127">Klíčová slova <xref:System.Data.SqlClient.SqlConnection> v připojovacím řetězci řídí `System.Transactions` přidružení připojení k zařazené transakci. `Transaction Binding`</span><span class="sxs-lookup"><span data-stu-id="2d4cc-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="2d4cc-128">Je také k dispozici prostřednictvím <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> vlastnosti. <xref:System.Data.SqlClient.SqlConnectionStringBuilder></span><span class="sxs-lookup"><span data-stu-id="2d4cc-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="2d4cc-129">Následující tabulka popisuje možné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="2d4cc-130">Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="2d4cc-130">Keyword</span></span>|<span data-ttu-id="2d4cc-131">Popis</span><span class="sxs-lookup"><span data-stu-id="2d4cc-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d4cc-132">Implicitní zrušení vazby</span><span class="sxs-lookup"><span data-stu-id="2d4cc-132">Implicit Unbind</span></span>|<span data-ttu-id="2d4cc-133">Výchozí nastavení</span><span class="sxs-lookup"><span data-stu-id="2d4cc-133">The default.</span></span> <span data-ttu-id="2d4cc-134">Připojení se odpojí z transakce, když skončí, a přepne zpět do režimu autocommit.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="2d4cc-135">Explicitní zrušení vazby</span><span class="sxs-lookup"><span data-stu-id="2d4cc-135">Explicit Unbind</span></span>|<span data-ttu-id="2d4cc-136">Připojení zůstane připojené k transakci, dokud transakce není uzavřená.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="2d4cc-137">Pokud není přidružená transakce aktivní nebo se neshoduje <xref:System.Transactions.Transaction.Current%2A>, připojení se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="2d4cc-138">Použití TransactionScope</span><span class="sxs-lookup"><span data-stu-id="2d4cc-138">Using TransactionScope</span></span>  
 <span data-ttu-id="2d4cc-139"><xref:System.Transactions.TransactionScope> Třída vytváří transakční blok kódu implicitně zařazováním připojení v distribuované transakci.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="2d4cc-140">Před zavoláním <xref:System.Transactions.TransactionScope.Complete%2A> metody je nutné volat metodu na <xref:System.Transactions.TransactionScope> konci bloku.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="2d4cc-141">Ukončení bloku vyvolá <xref:System.Transactions.TransactionScope.Dispose%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="2d4cc-142">Pokud byla vyvolána výjimka, která způsobí, že kód opustí rozsah, transakce je považována za přerušenou.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="2d4cc-143">Doporučujeme, abyste pomocí `using` bloku zajistili, že <xref:System.Transactions.TransactionScope.Dispose%2A> se zavolá na <xref:System.Transactions.TransactionScope> objekt při ukončení bloku using.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="2d4cc-144">Nepovedlo se zapsat nebo vrátit zpět nevyřízené transakce může významně poškodit výkon, protože výchozí časový limit <xref:System.Transactions.TransactionScope> je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="2d4cc-145">Pokud nepoužijete `using` příkaz, musíte provést veškerou práci `Try` v <xref:System.Transactions.TransactionScope.Dispose%2A> bloku a explicitně `Finally` volat metodu v bloku.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="2d4cc-146">Pokud dojde k výjimce v <xref:System.Transactions.TransactionScope>, transakce je označena jako nekonzistentní a je opuštěna.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="2d4cc-147">Bude vrácena zpět, jakmile <xref:System.Transactions.TransactionScope> bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="2d4cc-148">Pokud nedojde k žádné výjimce, připustí se účastnící se transakce.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d4cc-149">Třída vytvoří `Serializable` ve výchozím nastavení transakci s <xref:System.Transactions.Transaction.IsolationLevel%2A>hodnotou. `TransactionScope`</span><span class="sxs-lookup"><span data-stu-id="2d4cc-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="2d4cc-150">V závislosti na vaší aplikaci můžete zvážit snížení úrovně izolace, abyste se vyhnuli vysokému kolizí ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d4cc-151">Doporučujeme, abyste v rámci distribuovaných transakcí prováděli pouze aktualizace, vkládání a odstraňování, protože využívají významné databázové prostředky.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="2d4cc-152">Příkazy SELECT můžou nenutně uzamknout databázové prostředky a v některých scénářích může být nutné použít transakce pro výběr.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="2d4cc-153">Jakákoli nedatabázová práce by se měla provádět mimo rozsah transakce, pokud nezahrnuje další správce prostředků s podporou transakcí.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="2d4cc-154">I když výjimka v oboru transakce brání v potvrzení transakce, třída nemá žádné zřízení pro vrácení <xref:System.Transactions.TransactionScope> zpět všech změn, které kód provedl mimo rozsah samotné transakce.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="2d4cc-155">Pokud je nutné provést určitou akci při vrácení transakce zpět, musíte napsat vlastní implementaci <xref:System.Transactions.IEnlistmentNotification> rozhraní a explicitně uvést do transakce.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d4cc-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d4cc-156">Example</span></span>  
 <span data-ttu-id="2d4cc-157">Práce s <xref:System.Transactions> vyžaduje odkaz na System. Transactions. dll.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="2d4cc-158">Následující funkce ukazuje, jak vytvořit transakci typu promoce na dvou různých instancích SQL Server reprezentovaných dvěma různými <xref:System.Data.SqlClient.SqlConnection> objekty, které jsou zabaleny <xref:System.Transactions.TransactionScope> do bloku.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="2d4cc-159">Kód vytvoří <xref:System.Transactions.TransactionScope> blok `using` s příkazem a otevře první připojení, které je automaticky <xref:System.Transactions.TransactionScope>zařadí do.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="2d4cc-160">Transakce je zpočátku zařazena jako odlehčená transakce, nikoli plná distribuovaná transakce.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="2d4cc-161">Druhé připojení je zařazeno <xref:System.Transactions.TransactionScope> pouze v případě, že příkaz v prvním připojení nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="2d4cc-162">Když je otevřeno druhé připojení, transakce je automaticky povýšena na úplnou distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="2d4cc-163"><xref:System.Transactions.TransactionScope.Complete%2A> Metoda je vyvolána, která provádí transakci pouze v případě, že nebyly vyvolány žádné výjimky.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="2d4cc-164">Pokud byla výjimka vyvolána <xref:System.Transactions.TransactionScope> v jakémkoli bodě bloku, `Complete` nebude volána a distribuovaná transakce <xref:System.Transactions.TransactionScope> bude vrácena zpět, když je uvolněna na konci svého `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="2d4cc-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d4cc-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d4cc-165">See also</span></span>

- [<span data-ttu-id="2d4cc-166">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="2d4cc-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="2d4cc-167">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="2d4cc-167">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
