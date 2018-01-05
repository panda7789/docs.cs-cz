---
title: "dangerousThreadingAPI – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b7c4e7f5612cb6a46f16b6e42327e8430d548e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="7b075-102">dangerousThreadingAPI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="7b075-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="7b075-103">`dangerousThreadingAPI` Pomocník spravovaného ladění (MDA) se aktivuje při <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> metoda je volána ve vlákně než aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="7b075-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="7b075-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="7b075-104">Symptoms</span></span>  
 <span data-ttu-id="7b075-105">Aplikace je reagovat, nebo přestane reagovat po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="7b075-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="7b075-106">Systém nebo aplikace, data mohou být ponecháno v nepředvídatelném stavu dočasně nebo i po aplikace byla vypnuta.</span><span class="sxs-lookup"><span data-stu-id="7b075-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="7b075-107">Některé operace nebudou dokončovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="7b075-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="7b075-108">Příznaky může odlišovat kvůli náhodnost vyplývajících tento problém.</span><span class="sxs-lookup"><span data-stu-id="7b075-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="7b075-109">příčina</span><span class="sxs-lookup"><span data-stu-id="7b075-109">Cause</span></span>  
 <span data-ttu-id="7b075-110">Vlákno je pozastaveno asynchronně pomocí jiné vlákno <xref:System.Threading.Thread.Suspend%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7b075-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="7b075-111">Neexistuje žádný způsob, jak zjistit, kdy je bezpečné pozastavit jiné vlákno, což může být uprostřed operace.</span><span class="sxs-lookup"><span data-stu-id="7b075-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="7b075-112">Pozastavení vlákno může způsobit poškození dat nebo přerušení výstupních podmínek.</span><span class="sxs-lookup"><span data-stu-id="7b075-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="7b075-113">Má umístit vlákno do pozastaveném stavu a nikdy obnovit pomocí <xref:System.Threading.Thread.Resume%2A> metody aplikace může na neomezenou dobu zaseknout a případně poškodit data aplikací.</span><span class="sxs-lookup"><span data-stu-id="7b075-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="7b075-114">Tyto metody byly označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="7b075-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="7b075-115">Synchronizace primitiv jsou uložené ve vlákně na cílový, zůstanou udržovaných během pozastavení.</span><span class="sxs-lookup"><span data-stu-id="7b075-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="7b075-116">To může vést k zablokování by měl jiného vlákna, například vlákno provádění <xref:System.Threading.Thread.Suspend%2A>, pokusí se získat zámek na primitivní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7b075-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="7b075-117">V takovém případě problém projevuje jako vzájemné zablokování.</span><span class="sxs-lookup"><span data-stu-id="7b075-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="7b075-118">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="7b075-118">Resolution</span></span>  
 <span data-ttu-id="7b075-119">Vyhněte se návrhy, které vyžadují použití <xref:System.Threading.Thread.Suspend%2A> a <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b075-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="7b075-120">Pro spolupráci mezi vlákny, použijte synchronizace primitiv <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, nebo jazyka C# `lock` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7b075-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="7b075-121">Pokud musíte použít tyto metody, zmenší okno čas a minimalizovat kód, který provede při vlákno je v pozastaveném stavu.</span><span class="sxs-lookup"><span data-stu-id="7b075-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="7b075-122">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="7b075-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="7b075-123">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7b075-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="7b075-124">Pouze sestavy data o nebezpečné operace vláken.</span><span class="sxs-lookup"><span data-stu-id="7b075-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="7b075-125">Výstup</span><span class="sxs-lookup"><span data-stu-id="7b075-125">Output</span></span>  
 <span data-ttu-id="7b075-126">MDA identifikuje metodu nebezpečná vláken, která způsobila, že její aktivaci.</span><span class="sxs-lookup"><span data-stu-id="7b075-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="7b075-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="7b075-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="7b075-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b075-128">Example</span></span>  
 <span data-ttu-id="7b075-129">Následující příklad kódu ukazuje volání <xref:System.Threading.Thread.Suspend%2A> metoda, která způsobí, že aktivace `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="7b075-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="7b075-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b075-130">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="7b075-131">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7b075-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="7b075-132">lock – příkaz</span><span class="sxs-lookup"><span data-stu-id="7b075-132">lock Statement</span></span>](~/docs/csharp/language-reference/keywords/lock-statement.md)
