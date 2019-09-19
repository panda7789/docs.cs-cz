---
title: dangerousThreadingAPI – pomocník spravovaného ladění (MDA)
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 860f524820e6b92e58f4a593e2ddf651a5e7094d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052911"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="f5698-102">dangerousThreadingAPI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="f5698-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="f5698-103">Pokud je `dangerousThreadingAPI` metodavolánavjinémvlákněnežvaktuálnímvlákně,jeaktivovánapomocníkspravovanéholadění<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> (MDA).</span><span class="sxs-lookup"><span data-stu-id="f5698-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f5698-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="f5698-104">Symptoms</span></span>  
 <span data-ttu-id="f5698-105">Aplikace nereaguje nebo nereaguje na neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="f5698-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="f5698-106">Data systému nebo aplikací mohou být ponechána v nepředvídatelném stavu dočasně nebo i po vypnutí aplikace.</span><span class="sxs-lookup"><span data-stu-id="f5698-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="f5698-107">Některé operace nejsou dokončeny podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="f5698-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="f5698-108">Příznaky se můžou výrazně lišit v důsledku náhodnosti podstaty problému.</span><span class="sxs-lookup"><span data-stu-id="f5698-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f5698-109">příčina</span><span class="sxs-lookup"><span data-stu-id="f5698-109">Cause</span></span>  
 <span data-ttu-id="f5698-110">Vlákno je asynchronně pozastaveno jiným vláknem pomocí <xref:System.Threading.Thread.Suspend%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f5698-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="f5698-111">Neexistuje žádný způsob, jak určit, kdy je bezpečné pozastavit jiné vlákno, které může být uprostřed operace.</span><span class="sxs-lookup"><span data-stu-id="f5698-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="f5698-112">Pozastavení vlákna může mít za následek poškození dat nebo rozdělení invariant.</span><span class="sxs-lookup"><span data-stu-id="f5698-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="f5698-113">Pokud by vlákno bylo umístěno do pozastaveného stavu a nikdy se neobnovilo pomocí <xref:System.Threading.Thread.Resume%2A> metody, může aplikace zablokovat neomezenou dobu a může poškodit data aplikace.</span><span class="sxs-lookup"><span data-stu-id="f5698-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="f5698-114">Tyto metody byly označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f5698-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="f5698-115">Pokud jsou prvky synchronizace uloženy cílovým vláknem, zůstanou při pozastavení uchovávány.</span><span class="sxs-lookup"><span data-stu-id="f5698-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="f5698-116">To může vést k zablokování by mělo jiné vlákno, například vlákno provádí <xref:System.Threading.Thread.Suspend%2A>, pokus o získání zámku na primitivním rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f5698-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="f5698-117">V takové situaci se problém projeví jako zablokování.</span><span class="sxs-lookup"><span data-stu-id="f5698-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f5698-118">Řešení</span><span class="sxs-lookup"><span data-stu-id="f5698-118">Resolution</span></span>  
 <span data-ttu-id="f5698-119">Vyhněte se návrhům, které <xref:System.Threading.Thread.Suspend%2A> vyžadují <xref:System.Threading.Thread.Resume%2A>použití a.</span><span class="sxs-lookup"><span data-stu-id="f5698-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="f5698-120">Pro spolupráci <xref:System.Threading.Monitor>mezi vlákny použijte prvky synchronizace <xref:System.Threading.Mutex>, jako je, <xref:System.Threading.ReaderWriterLock>, nebo C# `lock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="f5698-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="f5698-121">Pokud je nutné použít tyto metody, omezte časový interval a minimalizujte množství kódu, který se spustí, když je vlákno v pozastaveném stavu.</span><span class="sxs-lookup"><span data-stu-id="f5698-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f5698-122">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="f5698-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="f5698-123">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="f5698-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="f5698-124">Oznamuje pouze data o nebezpečných operacích vláken.</span><span class="sxs-lookup"><span data-stu-id="f5698-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f5698-125">Výstup</span><span class="sxs-lookup"><span data-stu-id="f5698-125">Output</span></span>  
 <span data-ttu-id="f5698-126">MDA identifikuje nebezpečnou metodu vláken, která způsobila, že je aktivována.</span><span class="sxs-lookup"><span data-stu-id="f5698-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f5698-127">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="f5698-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="f5698-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5698-128">Example</span></span>  
 <span data-ttu-id="f5698-129">Následující příklad kódu ukazuje volání <xref:System.Threading.Thread.Suspend%2A> metody, která způsobuje aktivaci. `dangerousThreadingAPI`</span><span class="sxs-lookup"><span data-stu-id="f5698-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f5698-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5698-130">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="f5698-131">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f5698-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f5698-132">lock – příkaz</span><span class="sxs-lookup"><span data-stu-id="f5698-132">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
