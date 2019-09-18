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
ms.openlocfilehash: 3fd58ae8f73fd932df641ea96a44ff618dd139e2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052810"
---
# <a name="fatalexecutionengineerror-mda"></a><span data-ttu-id="26ae3-102">fatalExecutionEngineError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="26ae3-102">fatalExecutionEngineError MDA</span></span>
<span data-ttu-id="26ae3-103">Pokud byla zjištěna závažná chyba v modulu CLR (Common Language Runtime), je aktivována pomocník spravovanéholadění(MDA).`fatalExecutionEngineError`</span><span class="sxs-lookup"><span data-stu-id="26ae3-103">The `fatalExecutionEngineError` managed debugging assistant (MDA) is activated when a fatal error in the common language runtime (CLR) has been detected.</span></span> <span data-ttu-id="26ae3-104">Proces se ukončí.</span><span class="sxs-lookup"><span data-stu-id="26ae3-104">The process will be terminated.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="26ae3-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="26ae3-105">Symptoms</span></span>  
 <span data-ttu-id="26ae3-106">Neočekávané ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="26ae3-106">Unexpected process termination.</span></span> <span data-ttu-id="26ae3-107">Jiné příznaky nelze určit, protože k selhání CLR může dojít z nejrůznějších důvodů.</span><span class="sxs-lookup"><span data-stu-id="26ae3-107">Other symptoms cannot be determined because a CLR failure can occur for a variety of reasons.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="26ae3-108">příčina</span><span class="sxs-lookup"><span data-stu-id="26ae3-108">Cause</span></span>  
 <span data-ttu-id="26ae3-109">Modul CLR byl závažně poškozen.</span><span class="sxs-lookup"><span data-stu-id="26ae3-109">The CLR has been fatally corrupted.</span></span> <span data-ttu-id="26ae3-110">To je nejčastěji způsobeno poškozením dat, což může být způsobeno několika problémy, jako jsou volání funkcí vyvolání poškozené platformy a předání neplatných dat modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="26ae3-110">This is most often caused by data corruption, which can be caused by a number of problems, such as calls to malformed platform invoke functions and passing invalid data to the CLR.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="26ae3-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="26ae3-111">Resolution</span></span>  
 <span data-ttu-id="26ae3-112">Povolení dalších MDA může přispět k identifikaci problému.</span><span class="sxs-lookup"><span data-stu-id="26ae3-112">Enabling additional MDAs might help identify the problem.</span></span> <span data-ttu-id="26ae3-113">Následující MDA může být obzvláště užitečná při diagnostice tohoto problému:</span><span class="sxs-lookup"><span data-stu-id="26ae3-113">The following MDAs can be particularly helpful in diagnosing the issue:</span></span>  
  
- [<span data-ttu-id="26ae3-114">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="26ae3-114">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)  
  
- [<span data-ttu-id="26ae3-115">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="26ae3-115">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)  
  
- [<span data-ttu-id="26ae3-116">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="26ae3-116">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)  
  
- [<span data-ttu-id="26ae3-117">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="26ae3-117">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)  
  
- [<span data-ttu-id="26ae3-118">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="26ae3-118">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)  
  
- [<span data-ttu-id="26ae3-119">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="26ae3-119">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)  
  
- [<span data-ttu-id="26ae3-120">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="26ae3-120">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)  
  
- [<span data-ttu-id="26ae3-121">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="26ae3-121">invalidVariant</span></span>](invalidvariant-mda.md)  
  
- [<span data-ttu-id="26ae3-122">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="26ae3-122">invalidIUnknown</span></span>](invalidiunknown-mda.md)  
  
- [<span data-ttu-id="26ae3-123">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="26ae3-123">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)  
  
- [<span data-ttu-id="26ae3-124">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="26ae3-124">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)  
  
- [<span data-ttu-id="26ae3-125">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="26ae3-125">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="26ae3-126">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="26ae3-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="26ae3-127">Tento MDA nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="26ae3-127">This MDA has no effect on the runtime's behavior.</span></span>  
  
## <a name="output"></a><span data-ttu-id="26ae3-128">Výstup</span><span class="sxs-lookup"><span data-stu-id="26ae3-128">Output</span></span>  
 <span data-ttu-id="26ae3-129">Adresa funkce CLR, která způsobila závažnou chybu, ID vlákna, ve kterém došlo k chybě, a kód chyby.</span><span class="sxs-lookup"><span data-stu-id="26ae3-129">The address of the CLR function that caused the fatal error, the ID of the thread where the error occurred, and the error code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="26ae3-130">Konfiguraci</span><span class="sxs-lookup"><span data-stu-id="26ae3-130">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <fatalExecutionEngineError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26ae3-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26ae3-131">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution.Cer>
- [<span data-ttu-id="26ae3-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="26ae3-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
