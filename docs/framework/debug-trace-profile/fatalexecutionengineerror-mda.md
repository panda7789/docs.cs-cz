---
title: "fatalExecutionEngineError – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6eb091883f59302e195d1b49b84693815196a4b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="82bc1-102">fatalExecutionEngineError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="82bc1-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="82bc1-103">`fatalExecutionEngine``Error` Pomocník spravovaného ladění (MDA) se aktivuje, když byla zjištěna závažná chyba v common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="82bc1-103">The `fatalExecutionEngine``Error` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="82bc1-104">Proces bude ukončen.</span><span class="sxs-lookup"><span data-stu-id="82bc1-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="82bc1-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="82bc1-105">Symptoms</span></span>  
 <span data-ttu-id="82bc1-106">Neočekávané proces dokončen.</span><span class="sxs-lookup"><span data-stu-id="82bc1-106">Unexpected process termination.</span></span> <span data-ttu-id="82bc1-107">Ostatní příznaky nelze určit, protože selhání CLR může dojít z různých důvodů.</span><span class="sxs-lookup"><span data-stu-id="82bc1-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="82bc1-108">příčina</span><span class="sxs-lookup"><span data-stu-id="82bc1-108">Cause</span></span>  
 <span data-ttu-id="82bc1-109">Modul CLR je smrtelně poškozená.</span><span class="sxs-lookup"><span data-stu-id="82bc1-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="82bc1-110">Nejčastěji je to způsobeno poškození dat, který může být způsobeno několika problémy, jako například volání poškozený platformy vyvolání funkce a předání neplatná data do modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="82bc1-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="82bc1-111">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="82bc1-111">Resolution</span></span>  
 <span data-ttu-id="82bc1-112">Povolení dalších mda mohou pomoci problém identifikovat.</span><span class="sxs-lookup"><span data-stu-id="82bc1-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="82bc1-113">Následující mda může být zvláště užitečné při diagnostikování problému:</span><span class="sxs-lookup"><span data-stu-id="82bc1-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="82bc1-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="82bc1-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="82bc1-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="82bc1-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="82bc1-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="82bc1-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="82bc1-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="82bc1-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="82bc1-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="82bc1-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="82bc1-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="82bc1-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="82bc1-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="82bc1-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="82bc1-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="82bc1-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="82bc1-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="82bc1-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="82bc1-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="82bc1-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="82bc1-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="82bc1-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="82bc1-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="82bc1-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="82bc1-126">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="82bc1-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="82bc1-127">Tato MDA nemá žádný vliv na modul runtime chování.</span><span class="sxs-lookup"><span data-stu-id="82bc1-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="82bc1-128">Výstup</span><span class="sxs-lookup"><span data-stu-id="82bc1-128">Output</span></span>  
 <span data-ttu-id="82bc1-129">Adresa funkce CLR, která způsobila, že závažná chyba a ID vlákna, kde došlo k chybě, kód chyby.</span><span class="sxs-lookup"><span data-stu-id="82bc1-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="82bc1-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="82bc1-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82bc1-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="82bc1-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution.Cer>  
 [<span data-ttu-id="82bc1-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="82bc1-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
