---
title: fatalExecutionEngineError – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění FatalExecutionEngineError – (MDA) v rozhraní .NET, který se může aktivovat kvůli neočekávanému ukončení procesu.
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
ms.openlocfilehash: 0806d2eaa1752c88bebd03304fbe5c8094416a48
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415924"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="599ef-103">fatalExecutionEngineError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="599ef-103">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="599ef-104">`fatalExecutionEngineError`Pokud byla zjištěna závažná chyba v modulu CLR (Common Language Runtime), je aktivována pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="599ef-104">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="599ef-105">Proces se ukončí.</span><span class="sxs-lookup"><span data-stu-id="599ef-105">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="599ef-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="599ef-106">Symptoms</span></span>  
 <span data-ttu-id="599ef-107">Neočekávané ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="599ef-107">Unexpected process termination.</span></span> <span data-ttu-id="599ef-108">Jiné příznaky nelze určit, protože k selhání CLR může dojít z nejrůznějších důvodů.</span><span class="sxs-lookup"><span data-stu-id="599ef-108">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="599ef-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="599ef-109">Cause</span></span>  
 <span data-ttu-id="599ef-110">Modul CLR byl závažně poškozen.</span><span class="sxs-lookup"><span data-stu-id="599ef-110">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="599ef-111">To je nejčastěji způsobeno poškozením dat, což může být způsobeno několika problémy, jako jsou volání funkcí vyvolání poškozené platformy a předání neplatných dat modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="599ef-111">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="599ef-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="599ef-112">Resolution</span></span>  
 <span data-ttu-id="599ef-113">Povolení dalších MDA může přispět k identifikaci problému.</span><span class="sxs-lookup"><span data-stu-id="599ef-113">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="599ef-114">Následující MDA může být obzvláště užitečná při diagnostice tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="599ef-114">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="599ef-115">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="599ef-115">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="599ef-116">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="599ef-116">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="599ef-117">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="599ef-117">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="599ef-118">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="599ef-118">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="599ef-119">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="599ef-119">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="599ef-120">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="599ef-120">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="599ef-121">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="599ef-121">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="599ef-122">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="599ef-122">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="599ef-123">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="599ef-123">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="599ef-124">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="599ef-124">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="599ef-125">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="599ef-125">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="599ef-126">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="599ef-126">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="599ef-127">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="599ef-127">Effect on the Runtime</span></span>  
 <span data-ttu-id="599ef-128">Tento MDA nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="599ef-128">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="599ef-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="599ef-129">Output</span></span>  
 <span data-ttu-id="599ef-130">Adresa funkce CLR, která způsobila závažnou chybu, ID vlákna, ve kterém došlo k chybě, a kód chyby.</span><span class="sxs-lookup"><span data-stu-id="599ef-130">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="599ef-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="599ef-131">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="599ef-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="599ef-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="599ef-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="599ef-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
