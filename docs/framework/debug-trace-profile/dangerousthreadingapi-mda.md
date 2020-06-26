---
title: dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Dangerousthreadingapi – (MDA), který se aktivuje při volání Thread. Suspend v jiném vlákně, než je aktuální vlákno.
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: 9069ccb6f106c83db94f88bc464bc0888d28586c
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416002"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="a7561-103">dangerousThreadingAPI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="a7561-103">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="a7561-104">`dangerousThreadingAPI`Pokud <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> je metoda volána v jiném vlákně než v aktuálním vlákně, je aktivována pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="a7561-104">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a7561-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a7561-105">Symptoms</span></span>  
 <span data-ttu-id="a7561-106">Aplikace nereaguje nebo nereaguje na neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="a7561-106">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="a7561-107">Data systému nebo aplikací mohou být ponechána v nepředvídatelném stavu dočasně nebo i po vypnutí aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7561-107">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="a7561-108">Některé operace nejsou dokončeny podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="a7561-108">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="a7561-109">Příznaky se můžou výrazně lišit v důsledku náhodnosti podstaty problému.</span><span class="sxs-lookup"><span data-stu-id="a7561-109">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a7561-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="a7561-110">Cause</span></span>  
 <span data-ttu-id="a7561-111">Vlákno je asynchronně pozastaveno jiným vláknem pomocí <xref:System.Threading.Thread.Suspend%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a7561-111">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="a7561-112">Neexistuje žádný způsob, jak určit, kdy je bezpečné pozastavit jiné vlákno, které může být uprostřed operace.</span><span class="sxs-lookup"><span data-stu-id="a7561-112">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="a7561-113">Pozastavení vlákna může mít za následek poškození dat nebo rozdělení invariant.</span><span class="sxs-lookup"><span data-stu-id="a7561-113">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="a7561-114">Pokud by vlákno bylo umístěno do pozastaveného stavu a nikdy se neobnovilo pomocí <xref:System.Threading.Thread.Resume%2A> metody, může aplikace zablokovat neomezenou dobu a může poškodit data aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7561-114">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="a7561-115">Tyto metody byly označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="a7561-115">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="a7561-116">Pokud jsou prvky synchronizace uloženy cílovým vláknem, zůstanou při pozastavení uchovávány.</span><span class="sxs-lookup"><span data-stu-id="a7561-116">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="a7561-117">To může vést k zablokování by mělo jiné vlákno, například vlákno provádí <xref:System.Threading.Thread.Suspend%2A> , pokus o získání zámku na primitivním rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a7561-117">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="a7561-118">V takové situaci se problém projeví jako zablokování.</span><span class="sxs-lookup"><span data-stu-id="a7561-118">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a7561-119">Řešení</span><span class="sxs-lookup"><span data-stu-id="a7561-119">Resolution</span></span>  
 <span data-ttu-id="a7561-120">Vyhněte se návrhům, které vyžadují použití <xref:System.Threading.Thread.Suspend%2A> a <xref:System.Threading.Thread.Resume%2A> .</span><span class="sxs-lookup"><span data-stu-id="a7561-120">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="a7561-121">Pro spolupráci mezi vlákny použijte prvky synchronizace <xref:System.Threading.Monitor> , jako je, <xref:System.Threading.ReaderWriterLock> , <xref:System.Threading.Mutex> nebo příkaz jazyka C# `lock` .</span><span class="sxs-lookup"><span data-stu-id="a7561-121">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="a7561-122">Pokud je nutné použít tyto metody, omezte časový interval a minimalizujte množství kódu, který se spustí, když je vlákno v pozastaveném stavu.</span><span class="sxs-lookup"><span data-stu-id="a7561-122">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a7561-123">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="a7561-123">Effect on the Runtime</span></span>  
 <span data-ttu-id="a7561-124">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="a7561-124">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="a7561-125">Oznamuje pouze data o nebezpečných operacích vláken.</span><span class="sxs-lookup"><span data-stu-id="a7561-125">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a7561-126">Výstup</span><span class="sxs-lookup"><span data-stu-id="a7561-126">Output</span></span>  
 <span data-ttu-id="a7561-127">MDA identifikuje nebezpečnou metodu vláken, která způsobila, že je aktivována.</span><span class="sxs-lookup"><span data-stu-id="a7561-127">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a7561-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a7561-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="a7561-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7561-129">Example</span></span>  
 <span data-ttu-id="a7561-130">Následující příklad kódu ukazuje volání <xref:System.Threading.Thread.Suspend%2A> metody, která způsobuje aktivaci `dangerousThreadingAPI` .</span><span class="sxs-lookup"><span data-stu-id="a7561-130">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7561-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7561-131">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="a7561-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a7561-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a7561-133">lock – příkaz</span><span class="sxs-lookup"><span data-stu-id="a7561-133">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
