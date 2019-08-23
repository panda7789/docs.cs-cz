---
title: Zničení vláken
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 986b4dee17c41928327e7b2672d641bbb8b16f1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960092"
---
# <a name="destroying-threads"></a><span data-ttu-id="c0015-102">Zničení vláken</span><span class="sxs-lookup"><span data-stu-id="c0015-102">Destroying threads</span></span>
<span data-ttu-id="c0015-103"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Metoda se používá k trvalému zastavení spravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="c0015-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="c0015-104">Když zavoláte <xref:System.Threading.Thread.Abort%2A>, modul CLR (Common Language <xref:System.Threading.ThreadAbortException> Runtime) vyvolá v cílovém vlákně, které může zachytit cílové vlákno.</span><span class="sxs-lookup"><span data-stu-id="c0015-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="c0015-105">Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c0015-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0015-106">Pokud vlákno spouští nespravovaný kód, když je <xref:System.Threading.Thread.Abort%2A> jeho metoda volána, modul runtime ho <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>označí.</span><span class="sxs-lookup"><span data-stu-id="c0015-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c0015-107">Výjimka je vyvolána, když se vlákno vrátí do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="c0015-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="c0015-108">Jakmile je vlákno přerušeno, nelze jej restartovat.</span><span class="sxs-lookup"><span data-stu-id="c0015-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="c0015-109">Metoda nezpůsobí okamžité přerušení vlákna, protože cílové vlákno může <xref:System.Threading.ThreadAbortException> zachytit a spustit libovolné `finally` množství kódu v bloku. <xref:System.Threading.Thread.Abort%2A></span><span class="sxs-lookup"><span data-stu-id="c0015-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="c0015-110">Můžete zavolat <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> , pokud potřebujete počkat, dokud vlákno neskončí.</span><span class="sxs-lookup"><span data-stu-id="c0015-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="c0015-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>je blokující volání, které nevrací až do doby, kdy bylo vlákno skutečně zastaveno nebo byl ukončen nepovinný časový limit.</span><span class="sxs-lookup"><span data-stu-id="c0015-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="c0015-112">Přerušené vlákno může zavolat <xref:System.Threading.Thread.ResetAbort%2A> metodu nebo provést neohraničené zpracování `finally` v bloku, takže pokud nezadáte časový limit, není zaručeno ukončení čekání.</span><span class="sxs-lookup"><span data-stu-id="c0015-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="c0015-113">Vlákna, která čekají na volání <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody, lze přerušit jinými vlákny, které volají. <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c0015-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="c0015-114">Zpracování ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="c0015-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="c0015-115">Pokud očekáváte, že vlákno bude přerušeno, buď v důsledku volání <xref:System.Threading.Thread.Abort%2A> z vlastního kódu nebo v důsledku uvolnění domény aplikace, ve které je vlákno spuštěno (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> používá <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> se k ukončení vláken), vlákno musí zpracovat a provede libovolné konečné zpracování `finally` v klauzuli, jak je znázorněno v následujícím kódu. <xref:System.Threading.ThreadAbortException></span><span class="sxs-lookup"><span data-stu-id="c0015-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 <span data-ttu-id="c0015-116">Váš kód pro vyčištění musí být v `catch` klauzuli `finally` nebo v klauzuli, protože <xref:System.Threading.ThreadAbortException> je znovu vyvolána systémem na konci `finally` klauzule `finally` nebo na konci `catch` klauzule, pokud neexistuje klauzule.</span><span class="sxs-lookup"><span data-stu-id="c0015-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="c0015-117">Můžete zabránit, aby systém znovu vyvolal výjimku, voláním <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c0015-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c0015-118">Měli byste to však provést pouze v <xref:System.Threading.ThreadAbortException>případě, že váš vlastní kód způsobil.</span><span class="sxs-lookup"><span data-stu-id="c0015-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0015-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0015-119">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="c0015-120">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="c0015-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
