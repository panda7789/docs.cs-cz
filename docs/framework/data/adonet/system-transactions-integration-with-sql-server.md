---
title: Integrace System.Transactions s SQL Serverem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 42007dafbdc9f61b9fc0776e0aaa2987551b704a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174235"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="3146f-102">Integrace System.Transactions s SQL Serverem</span><span class="sxs-lookup"><span data-stu-id="3146f-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="3146f-103">Rozhraní .NET Framework verze 2.0 zavedlo transakční architekturu, ke které lze přistupovat prostřednictvím oboru <xref:System.Transactions> názvů.</span><span class="sxs-lookup"><span data-stu-id="3146f-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="3146f-104">Tento rámec zveřejňuje transakce způsobem, který je plně integrován v rozhraní .NET Framework, včetně ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="3146f-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="3146f-105">Kromě vylepšení programovatelnosti <xref:System.Transactions> a ADO.NET mohou spolupracovat na koordinaci optimalizací při práci s transakcemi.</span><span class="sxs-lookup"><span data-stu-id="3146f-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="3146f-106">Promotable transakce je lehký (místní) transakce, která může být automaticky povýšen na plně distribuované transakce podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="3146f-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="3146f-107">Počínaje ADO.NET 2.0 <xref:System.Data.SqlClient> podporuje promotable transakce při práci s SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3146f-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="3146f-108">Promotable transakce nevyvolá přidané režie distribuované transakce, pokud je požadováno přidané režie.</span><span class="sxs-lookup"><span data-stu-id="3146f-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="3146f-109">Promotable transakce jsou automatické a nevyžadují žádný zásah od vývojáře.</span><span class="sxs-lookup"><span data-stu-id="3146f-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="3146f-110">Promotable transakce jsou k dispozici pouze v případě, že`SqlClient`používáte zprostředkovatele dat rozhraní .NET Framework pro SQL Server ( ) s SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3146f-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="3146f-111">Vytváření promotable transakcí</span><span class="sxs-lookup"><span data-stu-id="3146f-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="3146f-112">Zprostředkovatel rozhraní .NET Framework pro SQL Server poskytuje podporu pro promotable transakce, <xref:System.Transactions> které jsou zpracovány prostřednictvím tříd v oboru názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3146f-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="3146f-113">Promotable transakce optimalizovat distribuované transakce odložením vytvoření distribuované transakce, dokud je potřeba.</span><span class="sxs-lookup"><span data-stu-id="3146f-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="3146f-114">Pokud je vyžadován pouze jeden správce prostředků, nedojde k žádné distribuované transakci.</span><span class="sxs-lookup"><span data-stu-id="3146f-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3146f-115">V částečně důvěryhodném <xref:System.Transactions.DistributedTransactionPermission> scénáři je vyžadováno při povýšení transakce na distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="3146f-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="3146f-116">Scénáře promotable transakcí</span><span class="sxs-lookup"><span data-stu-id="3146f-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="3146f-117">Distribuované transakce obvykle spotřebovávají významné systémové prostředky spravované koordinátorem Microsoft Distributed Transaction Coordinator (MS DTC), který integruje všechny správce prostředků, ke kterým se v transakci přistupuje.</span><span class="sxs-lookup"><span data-stu-id="3146f-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="3146f-118">Promotable transakce je zvláštní forma <xref:System.Transactions> transakce, která účinně deleguje práci na jednoduchou transakci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3146f-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="3146f-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>a SQL Server koordinovat práci spojenou se zpracováním transakce a podle potřeby ji povýšit na celou distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="3146f-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="3146f-120">Výhodou použití promotable transakce je, že při otevření připojení <xref:System.Transactions.TransactionScope> pomocí aktivní transakce a žádná další připojení jsou otevřeny, transakce potvrdí jako zjednodušené transakce, namísto vzniku další režii úplné distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="3146f-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="3146f-121">Klíčová slova připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="3146f-121">Connection String Keywords</span></span>  
 <span data-ttu-id="3146f-122">Vlastnost <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> podporuje klíčové `Enlist`slovo , <xref:System.Data.SqlClient> které označuje, zda bude detekovat transakční kontexty a automaticky zařadit připojení v distribuované transakce.</span><span class="sxs-lookup"><span data-stu-id="3146f-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="3146f-123">Pokud `Enlist=true`je připojení automaticky zapsáno v aktuálním kontextu transakce v počátečním vlákně.</span><span class="sxs-lookup"><span data-stu-id="3146f-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="3146f-124">Pokud `Enlist=false` `SqlClient` připojení nespolupracuje s distribuovanou transakcí.</span><span class="sxs-lookup"><span data-stu-id="3146f-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="3146f-125">Výchozí hodnota `Enlist` pro je true.</span><span class="sxs-lookup"><span data-stu-id="3146f-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="3146f-126">Pokud `Enlist` není zadán v připojovacím řetězci, připojení je automaticky zapsáno do distribuované transakce, pokud je při otevření připojení rozpoznáno.</span><span class="sxs-lookup"><span data-stu-id="3146f-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="3146f-127">Klíčová `Transaction Binding` slova v <xref:System.Data.SqlClient.SqlConnection> připojovacím řetězci řídí `System.Transactions` přidružení připojení k zapisované transakci.</span><span class="sxs-lookup"><span data-stu-id="3146f-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="3146f-128">Je také k <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> dispozici prostřednictvím nemovitosti <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="3146f-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="3146f-129">Následující tabulka popisuje možné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3146f-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="3146f-130">Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="3146f-130">Keyword</span></span>|<span data-ttu-id="3146f-131">Popis</span><span class="sxs-lookup"><span data-stu-id="3146f-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3146f-132">Implicitní zrušení vazby</span><span class="sxs-lookup"><span data-stu-id="3146f-132">Implicit Unbind</span></span>|<span data-ttu-id="3146f-133">Výchozí nastavení</span><span class="sxs-lookup"><span data-stu-id="3146f-133">The default.</span></span> <span data-ttu-id="3146f-134">Připojení se odpojí od transakce po jeho ukončení a přepne zpět do režimu automatického potvrzení.</span><span class="sxs-lookup"><span data-stu-id="3146f-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="3146f-135">Explicitní zrušení vazby</span><span class="sxs-lookup"><span data-stu-id="3146f-135">Explicit Unbind</span></span>|<span data-ttu-id="3146f-136">Připojení zůstane připojeno k transakci, dokud není transakce uzavřena.</span><span class="sxs-lookup"><span data-stu-id="3146f-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="3146f-137">Připojení se nezdaří, pokud přidružená transakce <xref:System.Transactions.Transaction.Current%2A>není aktivní nebo neodpovídá .</span><span class="sxs-lookup"><span data-stu-id="3146f-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="3146f-138">Použití oboru transakcí</span><span class="sxs-lookup"><span data-stu-id="3146f-138">Using TransactionScope</span></span>  
 <span data-ttu-id="3146f-139">Třída <xref:System.Transactions.TransactionScope> provede blok kódu transakční implicitně zapisovat připojení v distribuované transakci.</span><span class="sxs-lookup"><span data-stu-id="3146f-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="3146f-140">Před opuštěním <xref:System.Transactions.TransactionScope.Complete%2A> <xref:System.Transactions.TransactionScope> je nutné volat metodu na konci bloku.</span><span class="sxs-lookup"><span data-stu-id="3146f-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="3146f-141">Opuštění bloku vyvolá <xref:System.Transactions.TransactionScope.Dispose%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="3146f-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="3146f-142">Pokud byla vyvolána výjimka, která způsobí, že kód opustit obor, transakce je považována za přerušeno.</span><span class="sxs-lookup"><span data-stu-id="3146f-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="3146f-143">Doporučujeme použít `using` blok a ujistěte <xref:System.Transactions.TransactionScope.Dispose%2A> se, <xref:System.Transactions.TransactionScope> že je volána na objekt při ukončení using bloku.</span><span class="sxs-lookup"><span data-stu-id="3146f-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="3146f-144">Selhání potvrzení nebo vrácení zpět čekající transakce může výrazně poškodit výkon, protože výchozí časový limit pro je jedna minuta. <xref:System.Transactions.TransactionScope></span><span class="sxs-lookup"><span data-stu-id="3146f-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="3146f-145">Pokud nepoužijete `using` příkaz, musíte provést veškerou `Try` práci v <xref:System.Transactions.TransactionScope.Dispose%2A> bloku a `Finally` explicitně volat metodu v bloku.</span><span class="sxs-lookup"><span data-stu-id="3146f-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="3146f-146">Pokud dojde k výjimce <xref:System.Transactions.TransactionScope>v , transakce je označena jako nekonzistentní a je opuštěná.</span><span class="sxs-lookup"><span data-stu-id="3146f-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="3146f-147">Bude vrácena zpět, <xref:System.Transactions.TransactionScope> když je vyřazen.</span><span class="sxs-lookup"><span data-stu-id="3146f-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="3146f-148">Pokud nedojde k žádné výjimce, zúčastněné transakce potvrdí.</span><span class="sxs-lookup"><span data-stu-id="3146f-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3146f-149">Třída `TransactionScope` vytvoří transakci s <xref:System.Transactions.Transaction.IsolationLevel%2A> `Serializable` standardně.</span><span class="sxs-lookup"><span data-stu-id="3146f-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="3146f-150">V závislosti na vaší aplikaci můžete zvážit snížení úrovně izolace, abyste se vyhnuli vysokým konfliktům ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3146f-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3146f-151">Doporučujeme provádět pouze aktualizace, vloží a odstraní v rámci distribuovaných transakcí, protože spotřebovávají významné databázové prostředky.</span><span class="sxs-lookup"><span data-stu-id="3146f-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="3146f-152">Příkazy Select mohou zbytečně uzamknout databázové prostředky a v některých scénářích může být nutné použít transakce pro výběry.</span><span class="sxs-lookup"><span data-stu-id="3146f-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="3146f-153">Všechny práce mimo databázi by měla být provedena mimo rozsah transakce, pokud zahrnuje jiné transakční správce prostředků.</span><span class="sxs-lookup"><span data-stu-id="3146f-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="3146f-154">Přestože výjimka v rozsahu transakce brání transakce potvrzení, <xref:System.Transactions.TransactionScope> třída nemá žádné ustanovení pro vrácení zpět všechny změny, které váš kód provedl mimo rozsah samotné transakce.</span><span class="sxs-lookup"><span data-stu-id="3146f-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="3146f-155">Pokud máte provést nějakou akci při transakce je vrácena zpět, <xref:System.Transactions.IEnlistmentNotification> je nutné napsat vlastní implementaci rozhraní a explicitně zařadit do transakce.</span><span class="sxs-lookup"><span data-stu-id="3146f-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3146f-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="3146f-156">Example</span></span>  
 <span data-ttu-id="3146f-157">Práce <xref:System.Transactions> s vyžaduje, abyste měli odkaz na System.Transactions.dll.</span><span class="sxs-lookup"><span data-stu-id="3146f-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="3146f-158">Následující funkce ukazuje, jak vytvořit promotable transakce proti dvěma různými instancemi SERVERU SQL, reprezentované dvěma různými <xref:System.Data.SqlClient.SqlConnection> objekty, které jsou zabaleny do <xref:System.Transactions.TransactionScope> bloku.</span><span class="sxs-lookup"><span data-stu-id="3146f-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="3146f-159">Kód vytvoří <xref:System.Transactions.TransactionScope> blok s `using` příkazem a otevře první připojení, které <xref:System.Transactions.TransactionScope>jej automaticky zařadí do .</span><span class="sxs-lookup"><span data-stu-id="3146f-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="3146f-160">Transakce je zpočátku zapsána jako zjednodušená transakce, nikoli jako úplná distribuovaná transakce.</span><span class="sxs-lookup"><span data-stu-id="3146f-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="3146f-161">Druhé připojení je zapsán <xref:System.Transactions.TransactionScope> a pouze v případě, že příkaz v prvním připojení nevyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="3146f-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="3146f-162">Při otevření druhého připojení je transakce automaticky povýšena na úplnou distribuovanou transakci.</span><span class="sxs-lookup"><span data-stu-id="3146f-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="3146f-163">Metoda <xref:System.Transactions.TransactionScope.Complete%2A> je vyvolána, která potvrdí transakci pouze v případě, že nebyly vyvolány žádné výjimky.</span><span class="sxs-lookup"><span data-stu-id="3146f-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="3146f-164">Pokud byla vyvolána výjimka v <xref:System.Transactions.TransactionScope> libovolném `Complete` bodě v bloku, nebude volána a <xref:System.Transactions.TransactionScope> distribuovaná transakce `using` se vrátí zpět, jakmile je uvolněn na konci jeho bloku.</span><span class="sxs-lookup"><span data-stu-id="3146f-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3146f-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="3146f-165">See also</span></span>

- [<span data-ttu-id="3146f-166">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="3146f-166">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="3146f-167">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3146f-167">ADO.NET Overview</span></span>](ado-net-overview.md)
