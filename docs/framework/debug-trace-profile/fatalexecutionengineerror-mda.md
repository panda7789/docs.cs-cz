---
title: fatalExecutionEngineError – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- corrupted CLR
- fatal execution error
- terminated processes
- unexpected terminations
- fatal errors
- MDAs (managed debugging assistants), fatal errors
- process termination
- FatalExecutionEngineError MDA
- managed debugging assistants (MDAs), fatal errors
ms.assetid: 8b559e44-2393-4e4e-8160-7558d37a4a89
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4595049d4ea71de30cf13334e32cd4bb2699f2ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392535"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="63e73-102">fatalExecutionEngineError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="63e73-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="63e73-103">`fatalExecutionEngine``Error` Pomocník spravovaného ladění (MDA) se aktivuje, když byla zjištěna závažná chyba v common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="63e73-103">The `fatalExecutionEngine``Error` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="63e73-104">Proces bude ukončen.</span><span class="sxs-lookup"><span data-stu-id="63e73-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="63e73-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="63e73-105">Symptoms</span></span>  
 <span data-ttu-id="63e73-106">Neočekávané proces dokončen.</span><span class="sxs-lookup"><span data-stu-id="63e73-106">Unexpected process termination.</span></span> <span data-ttu-id="63e73-107">Ostatní příznaky nelze určit, protože selhání CLR může dojít z různých důvodů.</span><span class="sxs-lookup"><span data-stu-id="63e73-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="63e73-108">příčina</span><span class="sxs-lookup"><span data-stu-id="63e73-108">Cause</span></span>  
 <span data-ttu-id="63e73-109">Modul CLR je smrtelně poškozená.</span><span class="sxs-lookup"><span data-stu-id="63e73-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="63e73-110">Nejčastěji je to způsobeno poškození dat, který může být způsobeno několika problémy, jako například volání poškozený platformy vyvolání funkce a předání neplatná data do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="63e73-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="63e73-111">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="63e73-111">Resolution</span></span>  
 <span data-ttu-id="63e73-112">Povolení dalších mda mohou pomoci problém identifikovat.</span><span class="sxs-lookup"><span data-stu-id="63e73-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="63e73-113">Následující mda může být zvláště užitečné při diagnostikování problému:</span><span class="sxs-lookup"><span data-stu-id="63e73-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="63e73-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="63e73-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="63e73-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="63e73-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="63e73-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="63e73-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="63e73-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="63e73-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="63e73-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="63e73-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="63e73-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="63e73-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="63e73-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="63e73-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="63e73-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="63e73-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="63e73-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="63e73-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="63e73-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="63e73-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="63e73-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="63e73-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="63e73-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="63e73-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="63e73-126">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="63e73-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="63e73-127">Tato MDA nemá žádný vliv na modul runtime chování.</span><span class="sxs-lookup"><span data-stu-id="63e73-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="63e73-128">Výstup</span><span class="sxs-lookup"><span data-stu-id="63e73-128">Output</span></span>  
 <span data-ttu-id="63e73-129">Adresa funkce CLR, která způsobila, že závažná chyba a ID vlákna, kde došlo k chybě, kód chyby.</span><span class="sxs-lookup"><span data-stu-id="63e73-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="63e73-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="63e73-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63e73-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="63e73-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution.Cer>  
 [<span data-ttu-id="63e73-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="63e73-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
