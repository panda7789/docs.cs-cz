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
ms.openlocfilehash: 1bfc3aa2bb7d1819f5f6221154ba1d276e0c202c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149364"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="1f22e-102">dangerousThreadingAPI – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="1f22e-102">dangerousThreadingAPI MDA</span></span>
<span data-ttu-id="1f22e-103">`dangerousThreadingAPI` Pomocníka spravovaného ladění (MDA) se aktivuje při <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> metoda je volána ve vlákně než aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="1f22e-103">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1f22e-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="1f22e-104">Symptoms</span></span>  
 <span data-ttu-id="1f22e-105">Aplikace nereaguje nebo se zablokuje po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="1f22e-105">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="1f22e-106">Systém nebo aplikace, data můžou zůstat v nepředvídatelném stavu dočasně, nebo i po aplikace se ukončila.</span><span class="sxs-lookup"><span data-stu-id="1f22e-106">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="1f22e-107">Některé operace nejsou dokončení podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="1f22e-107">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="1f22e-108">Příznaky můžou výrazně lišit kvůli náhodnost přináší problém.</span><span class="sxs-lookup"><span data-stu-id="1f22e-108">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1f22e-109">příčina</span><span class="sxs-lookup"><span data-stu-id="1f22e-109">Cause</span></span>  
 <span data-ttu-id="1f22e-110">Vlákno je pozastaveno asynchronně pomocí jiného vlákna <xref:System.Threading.Thread.Suspend%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1f22e-110">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="1f22e-111">Neexistuje žádný způsob, jak určit, kdy je bezpečné pozastavit jiným vláknem, jež může být provádí operaci.</span><span class="sxs-lookup"><span data-stu-id="1f22e-111">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="1f22e-112">Pozastavení vlákno může způsobit poškození dat nebo zásadní výstupních podmínek.</span><span class="sxs-lookup"><span data-stu-id="1f22e-112">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="1f22e-113">Vlákno umístit do pozastaveného stavu a nikdy obnovenou pomocí <xref:System.Threading.Thread.Resume%2A> metodu, aplikace může neomezenou dobu zaseknout a případně poškodit data aplikací.</span><span class="sxs-lookup"><span data-stu-id="1f22e-113">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="1f22e-114">Tyto metody jsou označené jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="1f22e-114">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="1f22e-115">Pokud cílové vlákno drží synchronizací primitiv, zůstanou vlastněnou během pozastavení.</span><span class="sxs-lookup"><span data-stu-id="1f22e-115">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="1f22e-116">To může vést k zablokování by měl jiného vlákna, třeba vlákno provádění <xref:System.Threading.Thread.Suspend%2A>, pokus o získání zámku na primitivní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1f22e-116">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="1f22e-117">V takovém případě problém projevuje jako zablokování.</span><span class="sxs-lookup"><span data-stu-id="1f22e-117">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1f22e-118">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="1f22e-118">Resolution</span></span>  
 <span data-ttu-id="1f22e-119">Vyhněte se návrhům, které vyžadují použití <xref:System.Threading.Thread.Suspend%2A> a <xref:System.Threading.Thread.Resume%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f22e-119">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="1f22e-120">Spolupráce mezi vlákny pomocí synchronizace primitiv <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, nebo C# `lock` příkazu.</span><span class="sxs-lookup"><span data-stu-id="1f22e-120">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="1f22e-121">Pokud je nutné použít tyto metody, snížit časové okno a minimalizovat množství kódu, který se spustí během zobrazení vlákna v pozastaveném stavu.</span><span class="sxs-lookup"><span data-stu-id="1f22e-121">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1f22e-122">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="1f22e-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="1f22e-123">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="1f22e-123">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="1f22e-124">Sestavy pouze data o nebezpečné operace vláken.</span><span class="sxs-lookup"><span data-stu-id="1f22e-124">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1f22e-125">Výstup</span><span class="sxs-lookup"><span data-stu-id="1f22e-125">Output</span></span>  
 <span data-ttu-id="1f22e-126">MDA identifikuje nebezpečné vláken metodu, která způsobila jeho aktivaci.</span><span class="sxs-lookup"><span data-stu-id="1f22e-126">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1f22e-127">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1f22e-127">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="1f22e-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f22e-128">Example</span></span>  
 <span data-ttu-id="1f22e-129">Následující příklad kódu ukazuje volání <xref:System.Threading.Thread.Suspend%2A> metodu, která způsobí aktivaci `dangerousThreadingAPI`.</span><span class="sxs-lookup"><span data-stu-id="1f22e-129">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1f22e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f22e-130">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="1f22e-131">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="1f22e-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="1f22e-132">lock – příkaz</span><span class="sxs-lookup"><span data-stu-id="1f22e-132">lock Statement</span></span>](~/docs/csharp/language-reference/keywords/lock-statement.md)
