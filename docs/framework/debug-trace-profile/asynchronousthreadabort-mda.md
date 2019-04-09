---
title: asynchronousThreadAbort – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08f67ad363d0bd3efcc7a1eeedd1f48d3bae9407
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114884"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="a8cd4-102">asynchronousThreadAbort – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="a8cd4-102">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="a8cd4-103">`asynchronousThreadAbort` Pomocníka spravovaného ladění (MDA) se aktivuje, když vlákno pokusí zavést asynchronnímu přerušení do jiného vlákna.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-103">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="a8cd4-104">Synchronní vlákno přeruší neaktivovat `asynchronousThreadAbort` MDA.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-104">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="a8cd4-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a8cd4-105">Symptoms</span></span>
 <span data-ttu-id="a8cd4-106">Dojde k chybě aplikace s neošetřenou <xref:System.Threading.ThreadAbortException> při hlavního vlákna aplikace je přerušeno.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-106">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="a8cd4-107">Pokud aplikace i nadále provádí, může být horší, než aplikace k chybám, což může způsobit poškození dat další důsledky.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-107">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="a8cd4-108">Má být atomické operace mají byla přerušena pravděpodobně po dokončení částečně, ponechání dat aplikace v nepředvídatelném stavu.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-108">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="a8cd4-109">A <xref:System.Threading.ThreadAbortException> se dá vygenerovat na zdánlivě náhodných intervalech v provádění kódu, často v místech, ze kterých se neočekává vzniknout výjimky.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-109">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="a8cd4-110">Kód nemusí být schopna zpracovávat takové výjimky, což v poškozeném stavu.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-110">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="a8cd4-111">Příznaky můžou výrazně lišit kvůli náhodnost přináší problém.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-111">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="a8cd4-112">Příčina</span><span class="sxs-lookup"><span data-stu-id="a8cd4-112">Cause</span></span>
 <span data-ttu-id="a8cd4-113">Kód v jednom vlákně volána <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodu na zavést přerušení asynchronní vlákno s cílovým vláknem.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-113">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="a8cd4-114">Přerušení vlákna je asynchronní, protože kód, který provádí volání do <xref:System.Threading.Thread.Abort%2A> běží na jiném vlákně než cílová operaci zrušení udělat.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-114">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="a8cd4-115">Synchronní vlákno přeruší by neměly způsobit potíže, protože vlákno provádění <xref:System.Threading.Thread.Abort%2A> by mělo mít provedeno pouze na bezpečné kontrolní bod, ve kterém je konzistentní stav aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-115">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="a8cd4-116">Asynchronní vlákno přeruší představovat problém, protože jsou zpracovávány v nepředvídatelné body v cílové vlákno provádění.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-116">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="a8cd4-117">Abyste tomu předešli, by kód napsaný pro spuštění na vlákno, které může být přerušeno tímto způsobem potřeba zpracovat <xref:System.Threading.ThreadAbortException> v téměř každý jednotlivý řádek kódu, nezapomeňte vrátit data aplikací do konzistentního stavu.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-117">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="a8cd4-118">Není reálné očekávat kódu má být zapsán s tímto problémem v paměti nebo napsat kód, který chrání před všechny možné okolnosti.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-118">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="a8cd4-119">Volání nespravovaného kódu a `finally` bloky nebude přerušena asynchronně, ale hned po ukončení z jedné z těchto kategorií.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-119">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="a8cd4-120">Důvodem může být obtížné určit z důvodu náhodnost přináší problém.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-120">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="a8cd4-121">Řešení</span><span class="sxs-lookup"><span data-stu-id="a8cd4-121">Resolution</span></span>
 <span data-ttu-id="a8cd4-122">Vyhněte se návrh kódu, který vyžaduje použití asynchronního podprocesu přeruší.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-122">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="a8cd4-123">Existuje několik přístupů vhodnější pro přerušení s cílovým vláknem, které nevyžadují volání <xref:System.Threading.Thread.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-123">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="a8cd4-124">Nejbezpečnější je zavést mechanismus, jako je například běžné vlastnosti, která signalizuje cílové vlákno požádat o přerušení.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-124">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="a8cd4-125">Cílové vlákno kontroluje signál v určitých bezpečné kontrolní body.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-125">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="a8cd4-126">Zjistí-li to požádal přerušení, ho můžete vypnout bez výpadku.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-126">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="a8cd4-127">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="a8cd4-127">Effect on the Runtime</span></span>
 <span data-ttu-id="a8cd4-128">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="a8cd4-129">Sestavy pouze data o přerušení asynchronní vlákna.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-129">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="a8cd4-130">Výstup</span><span class="sxs-lookup"><span data-stu-id="a8cd4-130">Output</span></span>
 <span data-ttu-id="a8cd4-131">MDA sestavy ID vlákna provádění přerušení a ID vlákna, která je cílem přerušení.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-131">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="a8cd4-132">Nikdy budou stejné vzhledem k tomu, že tento požadavek omezuje na asynchronní přerušení.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-132">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="a8cd4-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a8cd4-133">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="a8cd4-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8cd4-134">Example</span></span>
 <span data-ttu-id="a8cd4-135">Aktivace `asynchronousThreadAbort` MDA vyžaduje pouze volání <xref:System.Threading.Thread.Abort%2A> na samostatném vlákně spuštěné.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-135">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="a8cd4-136">Pokud obsah vlákno spustit funkci, byly sady složitějších operací, které může dojít k přerušení libovolného kdykoli podle abort vezměte v úvahu důsledky.</span><span class="sxs-lookup"><span data-stu-id="a8cd4-136">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a8cd4-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8cd4-137">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="a8cd4-138">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a8cd4-138">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
