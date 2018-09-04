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
ms.openlocfilehash: 5cd6e85dca7c4c32361b964573f318b165e8d683
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562934"
---
# <a name="destroying-threads"></a><span data-ttu-id="96bef-102">Zničení vláken</span><span class="sxs-lookup"><span data-stu-id="96bef-102">Destroying threads</span></span>
<span data-ttu-id="96bef-103"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Metoda se používá k zastavení spravovaným vláknem trvale.</span><span class="sxs-lookup"><span data-stu-id="96bef-103">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is used to stop a managed thread permanently.</span></span> <span data-ttu-id="96bef-104">Při volání <xref:System.Threading.Thread.Abort%2A>, modul common language runtime vyvolá výjimku <xref:System.Threading.ThreadAbortException> v cílové vlákno, které cílové vlákno může zachytit.</span><span class="sxs-lookup"><span data-stu-id="96bef-104">When you call <xref:System.Threading.Thread.Abort%2A>, the common language runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="96bef-105">Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="96bef-105">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96bef-106">Pokud je vlákno prováděno nespravovaného kódu při jeho <xref:System.Threading.Thread.Abort%2A> metoda je volána, modul runtime ho označí <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="96bef-106">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="96bef-107">Pokud se podproces vrací do spravovaného kódu, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="96bef-107">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="96bef-108">Jakmile je přerušeno vlákno, nelze restartovat.</span><span class="sxs-lookup"><span data-stu-id="96bef-108">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="96bef-109"><xref:System.Threading.Thread.Abort%2A> Metoda nezpůsobí vlákno pro přerušení okamžitě, protože cílové vlákno může zachytit <xref:System.Threading.ThreadAbortException> a provést libovolné množství kódu v `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="96bef-109">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="96bef-110">Můžete volat <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Pokud budete muset počkat až do ukončení vlákna.</span><span class="sxs-lookup"><span data-stu-id="96bef-110">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="96bef-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> je blokovacího hovoru, který nevrací, dokud vlákno je ve skutečnosti byl zastaven při provádění nebo volitelný časový limit uplynul.</span><span class="sxs-lookup"><span data-stu-id="96bef-111"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="96bef-112">Přerušené vlákno může volat <xref:System.Threading.Thread.ResetAbort%2A> metoda nebo provádět zpracování bez vazby v `finally` blokovat, takže pokud nezadáte vypršení časového limitu, čekání není zaručeno, že na konec.</span><span class="sxs-lookup"><span data-stu-id="96bef-112">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="96bef-113">Vlákna, která čekají na volání <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metoda může dojít k přerušení kvůli ostatní vlákna, které volají <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="96bef-113">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="96bef-114">ThreadAbortException zpracování</span><span class="sxs-lookup"><span data-stu-id="96bef-114">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="96bef-115">Pokud očekáváte, že vaše vlákno přerušeno, buď jako výsledek volání <xref:System.Threading.Thread.Abort%2A> z vlastního kódu nebo v důsledku uvolnění domény aplikace, ve kterém je spuštěn podproces (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> používá <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ukončení vlákna), musí umět zpracovat vašeho vlákna <xref:System.Threading.ThreadAbortException> a provést libovolné finální zpracování v `finally` klauzule, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="96bef-115">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="96bef-116">Čistícího kódu musí být v `catch` klauzule nebo `finally` klauzule, protože <xref:System.Threading.ThreadAbortException> je znovu vyvolána systém na konci `finally` klauzuli, nebo na konci `catch` klauzule dojde žádné `finally` klauzule.</span><span class="sxs-lookup"><span data-stu-id="96bef-116">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="96bef-117">Systém můžete zabránit voláním opětné vyvolání výjimky <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="96bef-117">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="96bef-118">Nicméně byste měli dělat tento pouze tehdy, pokud váš vlastní kód, který způsobil <xref:System.Threading.ThreadAbortException>.</span><span class="sxs-lookup"><span data-stu-id="96bef-118">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96bef-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="96bef-119">See Also</span></span>  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="96bef-120">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="96bef-120">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
