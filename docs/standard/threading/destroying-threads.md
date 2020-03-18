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
ms.openlocfilehash: 842ca4ff17f9cbab3a1518d2dea37436c9b23f9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155929"
---
# <a name="destroying-threads"></a><span data-ttu-id="97156-102">Zničení vláken</span><span class="sxs-lookup"><span data-stu-id="97156-102">Destroying threads</span></span>

<span data-ttu-id="97156-103">Chcete-li ukončit provádění podprocesu, obvykle používáte [model zrušení spolupráce](cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="97156-103">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="97156-104">Někdy není možné zastavit vlákno kooperativně, protože spustí kód třetí strany, který není určen pro kooperativní zrušení.</span><span class="sxs-lookup"><span data-stu-id="97156-104">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="97156-105">Metodu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> v rozhraní .NET Framework lze použít k násilnému ukončení spravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="97156-105">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="97156-106">Při volání <xref:System.Threading.Thread.Abort%2A>, common language runtime <xref:System.Threading.ThreadAbortException> vyvolá v cílovévlákno, které může zachytit cílové vlákno.</span><span class="sxs-lookup"><span data-stu-id="97156-106">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="97156-107">Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97156-107">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="97156-108">Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> není podporována v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="97156-108">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET Core.</span></span> <span data-ttu-id="97156-109">Pokud potřebujete ukončit provádění kódu třetí strany násilně v .NET Core, spusťte jej v samostatném procesu a použijte <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97156-109">If you need to terminate the execution of third-party code forcibly in .NET Core, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="97156-110">Pokud vlákno provádí nespravovaný <xref:System.Threading.Thread.Abort%2A> kód při volání jeho <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>metody, modul runtime jej označí .</span><span class="sxs-lookup"><span data-stu-id="97156-110">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="97156-111">Výjimka je vyvolána, když se vlákno vrátí do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="97156-111">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="97156-112">Jakmile je vlákno přerušeno, nelze jej restartovat.</span><span class="sxs-lookup"><span data-stu-id="97156-112">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="97156-113">Metoda <xref:System.Threading.Thread.Abort%2A> nezpůsobí vlákno přerušit okamžitě, protože cílové vlákno <xref:System.Threading.ThreadAbortException> můžete zachytit a spustit libovolné `finally` množství kódu v bloku.</span><span class="sxs-lookup"><span data-stu-id="97156-113">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="97156-114">Můžete volat, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> pokud potřebujete počkat, dokud vlákno skončí.</span><span class="sxs-lookup"><span data-stu-id="97156-114">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="97156-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>je blokující volání, které se nevrátí, dokud vlákno skutečně zastavilo provádění nebo neuplynul volitelný časový limit.</span><span class="sxs-lookup"><span data-stu-id="97156-115"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="97156-116">Přerušené vlákno může <xref:System.Threading.Thread.ResetAbort%2A> volat metodu nebo provádět `finally` neomezené zpracování v bloku, takže pokud nezadáte časový čas, čekání není zaručeno ukončení.</span><span class="sxs-lookup"><span data-stu-id="97156-116">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="97156-117">Podprocesy, které čekají na <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> volání metody může být přerušena jinými vlákny, které volají <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97156-117">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="97156-118">Zpracování výjimky ThreadAbortException</span><span class="sxs-lookup"><span data-stu-id="97156-118">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="97156-119">Pokud očekáváte, že vaše vlákno bude přerušeno, buď v důsledku <xref:System.Threading.Thread.Abort%2A> volání z vlastního kódu, nebo v<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> důsledku <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> uvolnění domény aplikace, ve <xref:System.Threading.ThreadAbortException> které je vlákno spuštěno (používá k ukončení podprocesů), musí vlákno zpracovat a provést konečné zpracování v `finally` klauzuli, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="97156-119">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="97156-120">Váš kód pro vyčištění musí `catch` být `finally` v klauzuli <xref:System.Threading.ThreadAbortException> nebo klauzuli, protože je znovu `finally` vyvolánsystémem na konci `catch` klauzule nebo `finally` na konci klauzule, pokud neexistuje žádná klauzule.</span><span class="sxs-lookup"><span data-stu-id="97156-120">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="97156-121">Můžete zabránit systému znovu vyvolání výjimky <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="97156-121">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="97156-122">Měli byste to však provést pouze <xref:System.Threading.ThreadAbortException>v případě, že vlastní kód způsobil .</span><span class="sxs-lookup"><span data-stu-id="97156-122">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97156-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="97156-123">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="97156-124">Použití vláken a zřetězení</span><span class="sxs-lookup"><span data-stu-id="97156-124">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
