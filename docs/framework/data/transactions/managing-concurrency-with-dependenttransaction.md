---
title: Správa souběžnosti s DependentTransaction
description: Spravujte souběžnou transakci, včetně asynchronních úloh, pomocí třídy funkce DependentTransaction v rozhraní .NET.
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: 9c825c977419718c8b9870b40699c4d3516e8533
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141885"
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="fcb8c-103">Správa souběžnosti s DependentTransaction</span><span class="sxs-lookup"><span data-stu-id="fcb8c-103">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="fcb8c-104"><xref:System.Transactions.Transaction> Objekt je vytvořen pomocí <xref:System.Transactions.Transaction.DependentClone%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-104">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="fcb8c-105">Jejím jediným účelem je zajistit, že transakci nelze potvrdit při některých jiných částí kódu (například pracovní podproces) jsou stále provede práci na transakci.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-105">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="fcb8c-106">Při práci v rámci naklonované transakce je dokončena a připravena k potvrzené, jej můžete upozornit na transakci pomocí Tvůrce <xref:System.Transactions.DependentTransaction.Complete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-106">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="fcb8c-107">Proto můžete zachovat konzistence a správností data.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-107">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="fcb8c-108"><xref:System.Transactions.DependentTransaction> Třídu lze použít také ke správě souběžnosti mezi asynchronní úlohy.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-108">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="fcb8c-109">V tomto případě mohou i nadále nadřazeného provést všechny kódu v době, kdy závislá kopie pracuje na své vlastní úlohy.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-109">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="fcb8c-110">Jinými slovy provádění nadřazeného objektu není blokován, dokud nebude dokončena závislé osoby.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-110">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="fcb8c-111">Vytváření závislá kopie</span><span class="sxs-lookup"><span data-stu-id="fcb8c-111">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="fcb8c-112">Chcete-li vytvořit závislé transakci, zavolejte <xref:System.Transactions.Transaction.DependentClone%2A> a předáte <xref:System.Transactions.DependentCloneOption> výčet jako parametr.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-112">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="fcb8c-113">Tento parametr definuje chování transakce, pokud `Commit` je volána v nadřazené transakce před závislá kopie udává, zda je připravena k potvrzení transakce (voláním <xref:System.Transactions.DependentTransaction.Complete%2A> metoda).</span><span class="sxs-lookup"><span data-stu-id="fcb8c-113">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="fcb8c-114">Následující hodnoty jsou platné pro tento parametr:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-114">The following values are valid for this parameter:</span></span>  
  
- <span data-ttu-id="fcb8c-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>Vytvoří závislou transakci, která blokuje proces potvrzení nadřazené transakce, dokud nevyprší časový limit nadřazené transakce, nebo dokud <xref:System.Transactions.DependentTransaction.Complete%2A> není volána na všech závislých objektech, které indikují jejich dokončení.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-115"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="fcb8c-116">To je užitečné, když klient nechce nadřazené transakce se zapsat, dokud závislé transakce byl dokončen.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-116">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="fcb8c-117">Je-li nadřazené dokončí svou práci starších než závislé transakce a volání <xref:System.Transactions.CommittableTransaction.Commit%2A> na transakci, je blokován procesu potvrzení ve stavu, kde další práce lze provést v transakci a nelze vytvořit nové zařazení, dokud všechny položky závislé na volání <xref:System.Transactions.DependentTransaction.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-117">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="fcb8c-118">Jakmile je všechny dokončí jejich práce a volání <xref:System.Transactions.DependentTransaction.Complete%2A>, začne procesu potvrzení pro transakci.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-118">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
- <span data-ttu-id="fcb8c-119"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>na druhé straně vytvoří závislou transakci, která automaticky přeruší, pokud <xref:System.Transactions.CommittableTransaction.Commit%2A> je volána v nadřazené transakci před <xref:System.Transactions.DependentTransaction.Complete%2A> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-119"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="fcb8c-120">V takovém případě všechny práci v závislé transakce je beze změny v rámci jedné transakce životnost a nemá nikdo příležitost dobře se zapsat jen jejich část.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-120">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="fcb8c-121"><xref:System.Transactions.DependentTransaction.Complete%2A> Metoda musí být volána pouze jednou, pokud vaše aplikace dokončí svou práci na závislé transakce. v opačném <xref:System.InvalidOperationException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-121">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="fcb8c-122">Po zavolání toto volání nesmí provedením jakékoli další práce na transakci, nebo je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-122">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="fcb8c-123">Následující příklad kódu ukazuje, jak vytvořit závislé transakci pro správu dvou souběžných úloh klonování závislé transakce a předáním k pracovní podproces.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-123">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);
    }  
  
    public void ThreadMethod(object transaction)
    {
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();
             dependentTransaction.Dispose();
        }  
    }  
  
//Client code
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 <span data-ttu-id="fcb8c-124">Klientský kód vytvoří transakční obor, který nastaví také okolí transakce.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-124">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="fcb8c-125">Pracovní podproces by neměla předat okolí transakce.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-125">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="fcb8c-126">Namísto toho by měl klonovat aktuální (okolního) transakci voláním <xref:System.Transactions.Transaction.DependentClone%2A> metodu na aktuální transakci a předejte rolích dependent pracovní podproces.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-126">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="fcb8c-127">`ThreadMethod` Metoda provádí u nového vlákna.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-127">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="fcb8c-128">Klient spustí nového vlákna, předávání závislé transakce, jako `ThreadMethod` parametru.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-128">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="fcb8c-129">Vzhledem k tomu, že závislé transakce je vytvořen s <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, zaručuje, že transakci nelze zapsat do všech transakční práce vykonané na druhou po dokončení vlákna a <xref:System.Transactions.DependentTransaction.Complete%2A> je volán na závislé transakce.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-129">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="fcb8c-130">To znamená, že pokud končí rozsah klienta (při pokusu o uvolnění transakčního objektu na konci `using` příkazu) před tím, než nové vlákno zavolá <xref:System.Transactions.DependentTransaction.Complete%2A> závislé transakce, klientský kód zablokuje, dokud se nevolá <xref:System.Transactions.DependentTransaction.Complete%2A> v závislosti.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-130">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the `using` statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="fcb8c-131">Poté můžete transakci dokončit potvrzení nebo přerušení.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-131">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="fcb8c-132">Problémy s souběžnosti</span><span class="sxs-lookup"><span data-stu-id="fcb8c-132">Concurrency Issues</span></span>  
 <span data-ttu-id="fcb8c-133">Existuje několik dalších souběžnosti problémy, které potřebujete vědět, používáte-li <xref:System.Transactions.DependentTransaction> třídy:</span><span class="sxs-lookup"><span data-stu-id="fcb8c-133">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
- <span data-ttu-id="fcb8c-134">Pokud pracovní podproces vrátí zpět transakce, ale nadřazeného pokusí o potvrzení, <xref:System.Transactions.TransactionAbortedException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-134">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
- <span data-ttu-id="fcb8c-135">Je třeba vytvořit nové závislá kopie pro každý pracovní podproces v transakci.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-135">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="fcb8c-136">Nepředávejte stejné závislá kopie na více vláknech, protože pouze jeden z nich může volat <xref:System.Transactions.DependentTransaction.Complete%2A> v něm.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-136">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
- <span data-ttu-id="fcb8c-137">Pokud pracovní podproces založí nový pracovní podproces, ujistěte se, k vytvoření závislá kopie z závislá kopie a předejte jí nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="fcb8c-137">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcb8c-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcb8c-138">See also</span></span>

- <xref:System.Transactions.DependentTransaction>
