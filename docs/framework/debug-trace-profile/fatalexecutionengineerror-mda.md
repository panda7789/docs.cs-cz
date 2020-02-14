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
ms.openlocfilehash: e25c9ef6ec43089f1d85479d1afe301232ed1d4f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217494"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="a4dc6-102">fatalExecutionEngineError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="a4dc6-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="a4dc6-103">Pokud byla zjištěna závažná chyba v modulu CLR (Common Language Runtime), je aktivována pomocná aplikace `fatalExecutionEngineError` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="a4dc6-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="a4dc6-104">Proces se ukončí.</span><span class="sxs-lookup"><span data-stu-id="a4dc6-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a4dc6-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a4dc6-105">Symptoms</span></span>  
 <span data-ttu-id="a4dc6-106">Neočekávané ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="a4dc6-106">Unexpected process termination.</span></span> <span data-ttu-id="a4dc6-107">Jiné příznaky nelze určit, protože k selhání CLR může dojít z nejrůznějších důvodů.</span><span class="sxs-lookup"><span data-stu-id="a4dc6-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a4dc6-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="a4dc6-108">Cause</span></span>  
 <span data-ttu-id="a4dc6-109">Modul CLR byl závažně poškozen.</span><span class="sxs-lookup"><span data-stu-id="a4dc6-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="a4dc6-110">To je nejčastěji způsobeno poškozením dat, což může být způsobeno několika problémy, jako jsou volání funkcí vyvolání poškozené platformy a předání neplatných dat modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="a4dc6-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a4dc6-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="a4dc6-111">Resolution</span></span>  
 <span data-ttu-id="a4dc6-112">Povolení dalších MDA může přispět k identifikaci problému.</span><span class="sxs-lookup"><span data-stu-id="a4dc6-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="a4dc6-113">Následující MDA může být obzvláště užitečná při diagnostice tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="a4dc6-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="a4dc6-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="a4dc6-114">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="a4dc6-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="a4dc6-115">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="a4dc6-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="a4dc6-116">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="a4dc6-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="a4dc6-117">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="a4dc6-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="a4dc6-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="a4dc6-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="a4dc6-119">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="a4dc6-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="a4dc6-120">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="a4dc6-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="a4dc6-121">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="a4dc6-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="a4dc6-122">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="a4dc6-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="a4dc6-123">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="a4dc6-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="a4dc6-124">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="a4dc6-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="a4dc6-125">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a4dc6-126">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="a4dc6-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="a4dc6-127">Tento MDA nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a4dc6-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a4dc6-128">Výstup</span><span class="sxs-lookup"><span data-stu-id="a4dc6-128">Output</span></span>  
 <span data-ttu-id="a4dc6-129">Adresa funkce CLR, která způsobila závažnou chybu, ID vlákna, ve kterém došlo k chybě, a kód chyby.</span><span class="sxs-lookup"><span data-stu-id="a4dc6-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a4dc6-130">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a4dc6-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4dc6-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4dc6-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="a4dc6-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a4dc6-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
