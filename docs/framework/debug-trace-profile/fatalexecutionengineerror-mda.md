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
ms.openlocfilehash: f12b94198b88111d559cfe372c28bdbf4b37e3fe
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257474"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="cfe2d-102">fatalExecutionEngineError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="cfe2d-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="cfe2d-103">`fatalExecutionEngineError` Pomocníka spravovaného ladění (MDA) se aktivuje, když byla zjištěna závažná chyba v modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="cfe2d-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="cfe2d-104">Proces bude ukončen.</span><span class="sxs-lookup"><span data-stu-id="cfe2d-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="cfe2d-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="cfe2d-105">Symptoms</span></span>  
 <span data-ttu-id="cfe2d-106">Ukončení procesu pro neočekávané.</span><span class="sxs-lookup"><span data-stu-id="cfe2d-106">Unexpected process termination.</span></span> <span data-ttu-id="cfe2d-107">Další příznaky nelze určit, protože může dojít k selhání modulu CLR pro celou řadu důvodů.</span><span class="sxs-lookup"><span data-stu-id="cfe2d-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="cfe2d-108">příčina</span><span class="sxs-lookup"><span data-stu-id="cfe2d-108">Cause</span></span>  
 <span data-ttu-id="cfe2d-109">Modul CLR byl fatálně poškozen.</span><span class="sxs-lookup"><span data-stu-id="cfe2d-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="cfe2d-110">To je často způsobeno poškození dat, která může být způsobeno různé problémy, jako například volání na poškozené platformu vyvolání funkce a předáním neplatná data modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="cfe2d-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="cfe2d-111">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="cfe2d-111">Resolution</span></span>  
 <span data-ttu-id="cfe2d-112">Povolení dalších mda mohou pomoci při identifikaci problému.</span><span class="sxs-lookup"><span data-stu-id="cfe2d-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="cfe2d-113">Následující mda může být zvláště užitečné při diagnostice problému:</span><span class="sxs-lookup"><span data-stu-id="cfe2d-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
-   [<span data-ttu-id="cfe2d-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="cfe2d-114">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)  
  
-   [<span data-ttu-id="cfe2d-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="cfe2d-115">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)  
  
-   [<span data-ttu-id="cfe2d-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="cfe2d-116">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)  
  
-   [<span data-ttu-id="cfe2d-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="cfe2d-117">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)  
  
-   [<span data-ttu-id="cfe2d-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="cfe2d-118">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
  
-   [<span data-ttu-id="cfe2d-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="cfe2d-119">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)  
  
-   [<span data-ttu-id="cfe2d-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="cfe2d-120">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)  
  
-   [<span data-ttu-id="cfe2d-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="cfe2d-121">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)  
  
-   [<span data-ttu-id="cfe2d-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="cfe2d-122">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)  
  
-   [<span data-ttu-id="cfe2d-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="cfe2d-123">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)  
  
-   [<span data-ttu-id="cfe2d-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="cfe2d-124">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)  
  
-   [<span data-ttu-id="cfe2d-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="cfe2d-125">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="cfe2d-126">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="cfe2d-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="cfe2d-127">Toto MDA nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="cfe2d-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="cfe2d-128">Výstup</span><span class="sxs-lookup"><span data-stu-id="cfe2d-128">Output</span></span>  
 <span data-ttu-id="cfe2d-129">Adresa funkce modulu CLR, která způsobila závažná chyba a ID vlákna, kde došlo k chybě, kód chyby.</span><span class="sxs-lookup"><span data-stu-id="cfe2d-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="cfe2d-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="cfe2d-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfe2d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfe2d-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution.Cer>  
 [<span data-ttu-id="cfe2d-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="cfe2d-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
