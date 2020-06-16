---
title: Zničení vláken
description: Zjistěte, jaké máte možnosti, pokud potřebujete zničit vlákno v rozhraní .NET, jako je například kooperativní zrušení nebo metoda Thread. Abort. Naučte se zvládnout ThreadAbortException.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: baf9289413de0e99533f121eb2a404ff0d873511
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768505"
---
# <a name="destroying-threads"></a><span data-ttu-id="7c329-104">Zničení vláken</span><span class="sxs-lookup"><span data-stu-id="7c329-104">Destroying threads</span></span>

<span data-ttu-id="7c329-105">Chcete-li ukončit provádění vlákna, obvykle používáte [model zrušení spolupráce](cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="7c329-105">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="7c329-106">V některých případech není možné vlákno zastavovat spolupracuje, protože spouští kód třetí strany, který není navržen pro kooperativní zrušení.</span><span class="sxs-lookup"><span data-stu-id="7c329-106">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="7c329-107"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metodu v .NET Framework lze použít k vynucenému ukončení spravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="7c329-107">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="7c329-108">Když zavoláte <xref:System.Threading.Thread.Abort%2A> , modul CLR (Common Language Runtime) vyvolá <xref:System.Threading.ThreadAbortException> v cílovém vlákně, které může zachytit cílové vlákno.</span><span class="sxs-lookup"><span data-stu-id="7c329-108">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="7c329-109">Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7c329-109">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7c329-110"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metoda není v rozhraní .NET Core podporována.</span><span class="sxs-lookup"><span data-stu-id="7c329-110">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET Core.</span></span> <span data-ttu-id="7c329-111">Pokud potřebujete ukončit provádění kódu třetí strany vynuceně v .NET Core, spusťte ho v samostatném procesu a použijte <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7c329-111">If you need to terminate the execution of third-party code forcibly in .NET Core, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="7c329-112">Pokud vlákno spouští nespravovaný kód <xref:System.Threading.Thread.Abort%2A> , když je jeho metoda volána, modul runtime ho označí <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7c329-112">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7c329-113">Výjimka je vyvolána, když se vlákno vrátí do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7c329-113">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="7c329-114">Jakmile je vlákno přerušeno, nelze jej restartovat.</span><span class="sxs-lookup"><span data-stu-id="7c329-114">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="7c329-115"><xref:System.Threading.Thread.Abort%2A>Metoda nezpůsobí okamžité přerušení vlákna, protože cílové vlákno může zachytit <xref:System.Threading.ThreadAbortException> a spustit libovolné množství kódu v `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="7c329-115">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="7c329-116">Můžete zavolat, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Pokud potřebujete počkat, dokud vlákno neskončí.</span><span class="sxs-lookup"><span data-stu-id="7c329-116">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="7c329-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>je blokující volání, které nevrací až do doby, kdy bylo vlákno skutečně zastaveno nebo byl ukončen nepovinný časový limit.</span><span class="sxs-lookup"><span data-stu-id="7c329-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="7c329-118">Přerušené vlákno může zavolat <xref:System.Threading.Thread.ResetAbort%2A> metodu nebo provést neohraničené zpracování v `finally` bloku, takže pokud nezadáte časový limit, není zaručeno ukončení čekání.</span><span class="sxs-lookup"><span data-stu-id="7c329-118">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="7c329-119">Vlákna, která čekají na volání <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody, lze přerušit jinými vlákny, které volají <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7c329-119">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="7c329-120">Zpracování ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="7c329-120">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="7c329-121">Pokud očekáváte, že vlákno bude přerušeno, buď v důsledku volání <xref:System.Threading.Thread.Abort%2A> z vlastního kódu nebo v důsledku uvolnění domény aplikace, ve které je vlákno spuštěno ( <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> používá <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> se k ukončení vlákna), vlákno musí zpracovat <xref:System.Threading.ThreadAbortException> a provést jakékoliv konečné zpracování v `finally` klauzuli, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7c329-121">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="7c329-122">Váš kód pro vyčištění musí být v `catch` klauzuli nebo v `finally` klauzuli, protože <xref:System.Threading.ThreadAbortException> je znovu vyvolána systémem na konci `finally` klauzule nebo na konci `catch` klauzule, pokud neexistuje `finally` klauzule.</span><span class="sxs-lookup"><span data-stu-id="7c329-122">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="7c329-123">Můžete zabránit, aby systém znovu vyvolal výjimku, voláním <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="7c329-123">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7c329-124">Měli byste to však provést pouze v případě, že váš vlastní kód způsobil <xref:System.Threading.ThreadAbortException> .</span><span class="sxs-lookup"><span data-stu-id="7c329-124">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c329-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c329-125">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="7c329-126">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="7c329-126">Using Threads and Threading</span></span>](using-threads-and-threading.md)
