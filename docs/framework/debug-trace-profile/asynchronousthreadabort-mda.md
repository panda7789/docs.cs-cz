---
title: "asynchronousThreadAbort – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6f7bfee4375a14a4456493333e65a953d406c732
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="b0355-102">asynchronousThreadAbort – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="b0355-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="b0355-103">`asynchronousThreadAbort` Pomocník spravovaného ladění (MDA) se aktivuje, když se pokusí vlákna zavést asynchronní přerušení do jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="b0355-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="b0355-104">Synchronní vlákno přerušení Neaktivujte `asynchronousThreadAbort` (mda).</span><span class="sxs-lookup"><span data-stu-id="b0355-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="b0355-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="b0355-105">Symptoms</span></span>
 <span data-ttu-id="b0355-106">Aplikace, dojde k chybě s neošetřenou <xref:System.Threading.ThreadAbortException> když byl přerušen hlavní vlákno aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0355-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="b0355-107">Pokud aplikace provést i nadále, může být zhoršení než aplikace chybám, což může způsobit další poškození dat důsledky.</span><span class="sxs-lookup"><span data-stu-id="b0355-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="b0355-108">Operace, měl by být atomic mít byla přerušena pravděpodobně po dokončení částečné ponechat data aplikací v nepředvídatelném stavu.</span><span class="sxs-lookup"><span data-stu-id="b0355-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="b0355-109">A <xref:System.Threading.ThreadAbortException> z zdánlivě náhodné body v provádění kódu, často v místech, ze kterých výjimku neočekává se, že jsou vyvolány lze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="b0355-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="b0355-110">Kód nemusí být schopen zpracování takové výjimky, což je v poškozeném stavu.</span><span class="sxs-lookup"><span data-stu-id="b0355-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="b0355-111">Příznaky může odlišovat kvůli náhodnost vyplývajících tento problém.</span><span class="sxs-lookup"><span data-stu-id="b0355-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="b0355-112">příčina</span><span class="sxs-lookup"><span data-stu-id="b0355-112">Cause</span></span>
 <span data-ttu-id="b0355-113">Kód v názvem jedno vlákno <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metoda ve vlákně cíl zavádět přerušení asynchronní vlákno.</span><span class="sxs-lookup"><span data-stu-id="b0355-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="b0355-114">Zrušení vláken je asynchronní, protože kód, který zpřístupňuje volání <xref:System.Threading.Thread.Abort%2A> běží v jiném podprocesu než cíl operace zrušení.</span><span class="sxs-lookup"><span data-stu-id="b0355-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="b0355-115">Synchronní vlákno přerušení by nemělo způsobit problém, protože provádí přístup z více vláken <xref:System.Threading.Thread.Abort%2A> by mít provedena, protože pouze bezpečné kontrolního bodu, kde je konzistentní stav aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0355-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="b0355-116">Asynchronní vlákno přerušení představovat problém vzhledem k tomu, že jsou zpracovávány v nepředvídatelným body v cílové vláken provádění.</span><span class="sxs-lookup"><span data-stu-id="b0355-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="b0355-117">Abyste tomu předešli, kód napsaný ke spuštění na vlákno, které může být tímto způsobem přerušena potřebovat pro zpracování <xref:System.Threading.ThreadAbortException> na téměř každý jednotlivý řádek kódu, aby byl vrátit data aplikací zpět do konzistentního stavu.</span><span class="sxs-lookup"><span data-stu-id="b0355-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="b0355-118">Není reálné očekávat kódu k zapsání pomocí tohoto problému v paměti nebo napsat kód, který chrání před všechny možné okolnosti.</span><span class="sxs-lookup"><span data-stu-id="b0355-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="b0355-119">Volání nespravovaného kódu a `finally` bloky nebude přerušena asynchronně ale ihned po ukončení z jedné z těchto kategorií.</span><span class="sxs-lookup"><span data-stu-id="b0355-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="b0355-120">Příčinou může být obtížné určit, z důvodu náhodnost vyplývajících tento problém.</span><span class="sxs-lookup"><span data-stu-id="b0355-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="b0355-121">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="b0355-121">Resolution</span></span>
 <span data-ttu-id="b0355-122">Vyhněte se návrh kód, který vyžaduje použití asynchronní vlákno přerušení.</span><span class="sxs-lookup"><span data-stu-id="b0355-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="b0355-123">Existuje několik přístupů vhodnější pro přerušení cíl vlákno, které nevyžadují volání <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0355-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="b0355-124">Nejbezpečnější je zavedení mechanismus, jako jsou běžnou vlastností, která signalizuje vlákno cíl požádat o přerušení.</span><span class="sxs-lookup"><span data-stu-id="b0355-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="b0355-125">Cíl vlákno kontroluje signál v určitých bezpečné kontrolní body.</span><span class="sxs-lookup"><span data-stu-id="b0355-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="b0355-126">Pokud je oznámení, že bylo vyzváno přerušení, ho můžete řádné ukončení.</span><span class="sxs-lookup"><span data-stu-id="b0355-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="b0355-127">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="b0355-127">Effect on the Runtime</span></span>
 <span data-ttu-id="b0355-128">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b0355-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="b0355-129">Pouze sestavy data o přerušení asynchronní vlákno.</span><span class="sxs-lookup"><span data-stu-id="b0355-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="b0355-130">Výstup</span><span class="sxs-lookup"><span data-stu-id="b0355-130">Output</span></span>
 <span data-ttu-id="b0355-131">MDA hlásí ID vlákna provádění přerušení a ID vlákna, která je cílem přerušení.</span><span class="sxs-lookup"><span data-stu-id="b0355-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="b0355-132">Tyto nebude nikdy ve stejné vzhledem k tomu, že toto je omezený na asynchronní přerušení.</span><span class="sxs-lookup"><span data-stu-id="b0355-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="b0355-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b0355-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="b0355-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0355-134">Example</span></span>
 <span data-ttu-id="b0355-135">Aktivace `asynchronousThreadAbort` MDA vyžaduje pouze volání <xref:System.Threading.Thread.Abort%2A> na samostatné spuštěných vláken.</span><span class="sxs-lookup"><span data-stu-id="b0355-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="b0355-136">Je-li obsah vlákno spuštění funkce byly sadu složitějších operací, které může dojít k přerušení libovolný kdykoli podle přerušení, zvažte důsledky.</span><span class="sxs-lookup"><span data-stu-id="b0355-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a><span data-ttu-id="b0355-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0355-137">See Also</span></span>
 <span data-ttu-id="b0355-138"><xref:System.Threading.Thread>[Diagnostikování chyb pomocí Pomocníci spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)</span><span class="sxs-lookup"><span data-stu-id="b0355-138"><xref:System.Threading.Thread> [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)</span></span>
