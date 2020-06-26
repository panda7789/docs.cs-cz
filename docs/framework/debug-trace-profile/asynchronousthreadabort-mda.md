---
title: asynchronousThreadAbort – pomocník spravovaného ladění (MDA)
description: Přečtěte si, jak se aktivuje Pomocník pro asynchronousThreadAbort – spravované ladění (MDA), když se vlákno pokusí vložit asynchronní přerušení do jiného vlákna.
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
ms.openlocfilehash: 469372d57d9c21198353d171fec16458691eb25d
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415664"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="c06b4-103">asynchronousThreadAbort – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="c06b4-103">asynchronousThreadAbort MDA</span></span>
<span data-ttu-id="c06b4-104">`asynchronousThreadAbort`Pokud se vlákno pokusí zavést asynchronní přerušení do jiného vlákna, aktivuje se pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="c06b4-104">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="c06b4-105">Synchronní přerušení vlákna neaktivují modul `asynchronousThreadAbort` MDA.</span><span class="sxs-lookup"><span data-stu-id="c06b4-105">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="c06b4-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="c06b4-106">Symptoms</span></span>
 <span data-ttu-id="c06b4-107">Dojde k selhání aplikace s neošetřenou <xref:System.Threading.ThreadAbortException> při přerušení hlavního vlákna aplikace.</span><span class="sxs-lookup"><span data-stu-id="c06b4-107">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="c06b4-108">Pokud by aplikace pokračovala v provádění, může to být horší než selhání aplikace, což může vést k dalšímu poškození dat.</span><span class="sxs-lookup"><span data-stu-id="c06b4-108">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="c06b4-109">Operace, které mají být atomické, byly pravděpodobně přerušeny po částečném dokončení a data aplikace budou ponechána v nepředvídatelném stavu.</span><span class="sxs-lookup"><span data-stu-id="c06b4-109">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="c06b4-110"><xref:System.Threading.ThreadAbortException>Může být vygenerován z zdánlivě náhodných bodů při provádění kódu, často v místech, ze kterých není očekávána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c06b4-110">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="c06b4-111">Kód nemusí být schopen zpracovat takovou výjimku, což vede k poškozenému stavu.</span><span class="sxs-lookup"><span data-stu-id="c06b4-111">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="c06b4-112">Příznaky se můžou výrazně lišit v důsledku náhodnosti podstaty problému.</span><span class="sxs-lookup"><span data-stu-id="c06b4-112">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="c06b4-113">Příčina</span><span class="sxs-lookup"><span data-stu-id="c06b4-113">Cause</span></span>
 <span data-ttu-id="c06b4-114">Kód v jednom vlákně, který se nazývá <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metoda v cílovém vláknu k zavedení asynchronního přerušení vlákna.</span><span class="sxs-lookup"><span data-stu-id="c06b4-114">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="c06b4-115">Přerušení vlákna je asynchronní, protože kód, který provádí volání, <xref:System.Threading.Thread.Abort%2A> je spuštěn v jiném vlákně, než je cílem operace Abort.</span><span class="sxs-lookup"><span data-stu-id="c06b4-115">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="c06b4-116">Synchronní přerušení vlákna by neměla způsobovat problém, protože vlákno, které provádí, <xref:System.Threading.Thread.Abort%2A> by mělo být provedeno pouze v bezpečném kontrolním bodu, kde je stav aplikace konzistentní.</span><span class="sxs-lookup"><span data-stu-id="c06b4-116">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="c06b4-117">Asynchronní vlákno přerušuje problém, protože jsou zpracovávány v nepředvídatelných bodech v provádění cílového vlákna.</span><span class="sxs-lookup"><span data-stu-id="c06b4-117">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="c06b4-118">Aby k tomu nedocházelo, kód napsaný pro spuštění ve vlákně, který může být přerušen tímto způsobem, by musel zpracovat <xref:System.Threading.ThreadAbortException> téměř každý řádek kódu a přitom zajistit, aby se data aplikace vrátila do konzistentního stavu.</span><span class="sxs-lookup"><span data-stu-id="c06b4-118">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="c06b4-119">Nejedná se o realistickou situaci, kdy očekáváte, že se kód bude zapisovat s tímto problémem, nebo jestli chcete napsat kód, který chrání před všemi možnými okolnostmi.</span><span class="sxs-lookup"><span data-stu-id="c06b4-119">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="c06b4-120">Volání do nespravovaného kódu a `finally` bloky nebudou asynchronně přerušeny, ale okamžitě po ukončení jedné z těchto kategorií.</span><span class="sxs-lookup"><span data-stu-id="c06b4-120">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="c06b4-121">Příčina může být obtížné určit z důvodu náhodnosti podstaty problému.</span><span class="sxs-lookup"><span data-stu-id="c06b4-121">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="c06b4-122">Řešení</span><span class="sxs-lookup"><span data-stu-id="c06b4-122">Resolution</span></span>
 <span data-ttu-id="c06b4-123">Vyhněte se návrhu kódu, který vyžaduje použití asynchronního přerušení vlákna.</span><span class="sxs-lookup"><span data-stu-id="c06b4-123">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="c06b4-124">Existuje několik přístupů, které jsou vhodnější pro přerušení cílového vlákna, které nevyžadují volání <xref:System.Threading.Thread.Abort%2A> .</span><span class="sxs-lookup"><span data-stu-id="c06b4-124">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="c06b4-125">Nejbezpečnější je zavedení mechanismu, jako je například společná vlastnost, která signalizuje cílovému vláknu, aby požadoval přerušení.</span><span class="sxs-lookup"><span data-stu-id="c06b4-125">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="c06b4-126">Cílové vlákno kontroluje signál u určitých bezpečných kontrolních bodů.</span><span class="sxs-lookup"><span data-stu-id="c06b4-126">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="c06b4-127">Pokud si vyžádá, že bylo vyžadováno přerušení, může se řádně vypnout.</span><span class="sxs-lookup"><span data-stu-id="c06b4-127">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="c06b4-128">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="c06b4-128">Effect on the Runtime</span></span>
 <span data-ttu-id="c06b4-129">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="c06b4-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="c06b4-130">Pouze hlásí data o přerušení asynchronního vlákna.</span><span class="sxs-lookup"><span data-stu-id="c06b4-130">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="c06b4-131">Výstup</span><span class="sxs-lookup"><span data-stu-id="c06b4-131">Output</span></span>
 <span data-ttu-id="c06b4-132">MDA hlásí ID vlákna, které provádí přerušení, a ID vlákna, které je cílem přerušení.</span><span class="sxs-lookup"><span data-stu-id="c06b4-132">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="c06b4-133">Nebudou nikdy stejné, protože to je omezeno na asynchronní přerušení.</span><span class="sxs-lookup"><span data-stu-id="c06b4-133">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="c06b4-134">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="c06b4-134">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="c06b4-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="c06b4-135">Example</span></span>
 <span data-ttu-id="c06b4-136">Aktivace služby `asynchronousThreadAbort` MDA vyžaduje pouze volání do <xref:System.Threading.Thread.Abort%2A> samostatného běžícího vlákna.</span><span class="sxs-lookup"><span data-stu-id="c06b4-136">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="c06b4-137">Zvažte důsledky, pokud je obsah funkce spuštění vlákna množinou složitějších operací, které mohou být přerušeny v libovolném okamžiku přerušení.</span><span class="sxs-lookup"><span data-stu-id="c06b4-137">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c06b4-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="c06b4-138">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="c06b4-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c06b4-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
