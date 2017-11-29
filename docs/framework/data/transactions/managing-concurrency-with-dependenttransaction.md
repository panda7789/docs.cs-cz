---
title: "Správa souběžnosti s DependentTransaction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cb0fa7f328b158613836e6ab20bd33545dc3a5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="managing-concurrency-with-dependenttransaction"></a>Správa souběžnosti s DependentTransaction
<xref:System.Transactions.Transaction> Objekt je vytvořen pomocí <xref:System.Transactions.Transaction.DependentClone%2A> metody. Jejím jediným účelem je zajistit, že transakci nelze potvrdit při některých jiných částí kódu (například pracovní podproces) jsou stále provede práci na transakci. Při práci v rámci naklonované transakce je dokončena a připravena k potvrzené, jej můžete upozornit na transakci pomocí Tvůrce <xref:System.Transactions.DependentTransaction.Complete%2A> metody. Proto můžete zachovat konzistence a správností data.  
  
 <xref:System.Transactions.DependentTransaction> Třídu lze použít také ke správě souběžnosti mezi asynchronní úlohy. V tomto případě mohou i nadále nadřazeného provést všechny kódu v době, kdy závislá kopie pracuje na své vlastní úlohy. Jinými slovy provádění nadřazeného objektu není blokován, dokud nebude dokončena závislé osoby.  
  
## <a name="creating-a-dependent-clone"></a>Vytváření závislá kopie  
 Chcete-li vytvořit závislé transakci, zavolejte <xref:System.Transactions.Transaction.DependentClone%2A> a předáte <xref:System.Transactions.DependentCloneOption> výčet jako parametr. Tento parametr definuje chování transakce, pokud `Commit` je volána v nadřazené transakce před závislá kopie udává, zda je připravena k potvrzení transakce (voláním <xref:System.Transactions.DependentTransaction.Complete%2A> metoda). Následující hodnoty jsou platné pro tento parametr:  
  
-   <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>Vytvoří závislé transakce, která blokuje procesu potvrzení nadřazené transakce až do nadřazeného časy transakcí limit, nebo až do <xref:System.Transactions.DependentTransaction.Complete%2A> je volán na všechny položky závislé na určující jejich dokončení. To je užitečné, když klient nechce nadřazené transakce se zapsat, dokud závislé transakce byl dokončen. Je-li nadřazené dokončí svou práci starších než závislé transakce a volání <xref:System.Transactions.CommittableTransaction.Commit%2A> na transakci, je blokován procesu potvrzení ve stavu, kde další práce lze provést v transakci a nelze vytvořit nové zařazení, dokud všechny položky závislé na volání <xref:System.Transactions.DependentTransaction.Complete%2A>. Jakmile je všechny dokončí jejich práce a volání <xref:System.Transactions.DependentTransaction.Complete%2A>, začne procesu potvrzení pro transakci.  
  
-   <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, na druhé straně vytvoří závislé transakcí, která automaticky zruší-li <xref:System.Transactions.CommittableTransaction.Commit%2A> je volána v nadřazené transakce před <xref:System.Transactions.DependentTransaction.Complete%2A> je volána. V takovém případě všechny práci v závislé transakce je beze změny v rámci jedné transakce životnost a nemá nikdo příležitost dobře se zapsat jen jejich část.  
  
 <xref:System.Transactions.DependentTransaction.Complete%2A> Metoda musí být volána pouze jednou, pokud vaše aplikace dokončí svou práci na závislé transakce. v opačném <xref:System.InvalidOperationException> je vyvolána. Po zavolání toto volání nesmí provedením jakékoli další práce na transakci, nebo je vyvolána výjimka.  
  
 Následující příklad kódu ukazuje, jak vytvořit závislé transakci pro správu dvou souběžných úloh klonování závislé transakce a předáním k pracovní podproces.  
  
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
  
 Klientský kód vytvoří transakční obor, který nastaví také okolí transakce. Pracovní podproces by neměla předat okolí transakce. Namísto toho by měl klonovat aktuální (okolního) transakci voláním <xref:System.Transactions.Transaction.DependentClone%2A> metodu na aktuální transakci a předejte rolích dependent pracovní podproces.  
  
 `ThreadMethod` Metoda provádí u nového vlákna. Klient spustí nového vlákna, předávání závislé transakce, jako `ThreadMethod` parametru.  
  
 Vzhledem k tomu, že závislé transakce je vytvořen s <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, zaručuje, že transakci nelze zapsat do všech transakční práce vykonané na druhou po dokončení vlákna a <xref:System.Transactions.DependentTransaction.Complete%2A> je volán na závislé transakce. To znamená, že pokud skončí obor klienta (při pokusu o odstranění transakční objekt na konci **pomocí** příkaz) před nové vlákno volání <xref:System.Transactions.DependentTransaction.Complete%2A> na závislé transakce, kód klienta blokuje dokud <xref:System.Transactions.DependentTransaction.Complete%2A> se volá na závislé položky. Poté můžete transakci dokončit potvrzení nebo přerušení.  
  
## <a name="concurrency-issues"></a>Problémy s souběžnosti  
 Existuje několik dalších souběžnosti problémy, které potřebujete vědět, používáte-li <xref:System.Transactions.DependentTransaction> třídy:  
  
-   Pokud pracovní podproces vrátí zpět transakce, ale nadřazeného pokusí o potvrzení, <xref:System.Transactions.TransactionAbortedException> je vyvolána.  
  
-   Je třeba vytvořit nové závislá kopie pro každý pracovní podproces v transakci. Nepředávejte stejné závislá kopie na více vláknech, protože pouze jeden z nich může volat <xref:System.Transactions.DependentTransaction.Complete%2A> v něm.  
  
-   Pokud pracovní podproces založí nový pracovní podproces, ujistěte se, k vytvoření závislá kopie z závislá kopie a předejte jí nové vlákno.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Transactions.DependentTransaction>
