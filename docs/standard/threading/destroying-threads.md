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
ms.openlocfilehash: 8e6eff0caa76349ce441a662428e37e25e2a6518
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582927"
---
# <a name="destroying-threads"></a><span data-ttu-id="6eb49-102">Zničení vláken</span><span class="sxs-lookup"><span data-stu-id="6eb49-102">Destroying Threads</span></span>
<span data-ttu-id="6eb49-103"><xref:System.Threading.Thread.Abort%2A> Metoda se používá k zastavení spravované vlákno trvale.</span><span class="sxs-lookup"><span data-stu-id="6eb49-103">The <xref:System.Threading.Thread.Abort%2A> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="6eb49-104">Při volání <xref:System.Threading.Thread.Abort%2A>, vyvolá modul common language runtime <xref:System.Threading.ThreadAbortException> ve vláknu cíl, který může zachytit vlákno cíl.</span><span class="sxs-lookup"><span data-stu-id="6eb49-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="6eb49-105">Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6eb49-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6eb49-106">Pokud vlákno provádí nespravovaného kódu při jeho <xref:System.Threading.Thread.Abort%2A> metoda je volána, modul runtime označí je <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6eb49-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6eb49-107">Když se vrátí vlákno do spravovaného kódu, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="6eb49-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="6eb49-108">Jakmile vlákno byl přerušen, nelze ji restartovat.</span><span class="sxs-lookup"><span data-stu-id="6eb49-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="6eb49-109"><xref:System.Threading.Thread.Abort%2A> Metoda nezpůsobí vlákno k přerušení okamžitě, protože cíl vlákno může zachytit <xref:System.Threading.ThreadAbortException> a provést libovolné množství kód `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="6eb49-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="6eb49-110">Můžete volat <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Pokud potřebujete Počkejte, dokud vlákno skončila.</span><span class="sxs-lookup"><span data-stu-id="6eb49-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="6eb49-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> je blokování volání, která nevrátí dokud vlákno ve skutečnosti byla zastavena, provádění nebo vypršení časového limitu volitelné intervalu.</span><span class="sxs-lookup"><span data-stu-id="6eb49-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="6eb49-112">Přerušené vlákno může volat <xref:System.Threading.Thread.ResetAbort%2A> metoda nebo provádět bez vazby zpracování v `finally` blokovat, takže pokud nezadáte vypršení časového limitu, není zaručena čekání na konec.</span><span class="sxs-lookup"><span data-stu-id="6eb49-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="6eb49-113">Vláken, které čekají na volání <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metoda může být přerušeny jiná vlákna, které volají <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6eb49-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="6eb49-114">Výjimka ThreadAbortException zpracování</span><span class="sxs-lookup"><span data-stu-id="6eb49-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="6eb49-115">Pokud očekáváte, že vaše vlákno přerušení, buď v důsledku volání <xref:System.Threading.Thread.Abort%2A> z vlastního kódu nebo v důsledku uvolnění domény aplikace ve které je spuštěný vlákno (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> používá <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ukončit vláken), musí vaše podprocesu zpracování <xref:System.Threading.ThreadAbortException> a provést libovolné finální zpracování v `finally` klauzule, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6eb49-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="6eb49-116">Vyčištění kód musí být v `catch` klauzule nebo `finally` klauzule, protože <xref:System.Threading.ThreadAbortException> je znovu vyvolány v systému na konci `finally` klauzuli, nebo na konci `catch` klauzule, pokud je žádné `finally` klauzule.</span><span class="sxs-lookup"><span data-stu-id="6eb49-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="6eb49-117">Můžete zabránit v systému opětné vyvolání výjimky při volání <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="6eb49-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6eb49-118">Ale měli byste udělat tento jenom Pokud vlastní kód způsobila <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="6eb49-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb49-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6eb49-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="6eb49-120">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="6eb49-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
