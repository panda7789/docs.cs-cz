---
title: overlappedFreeError – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění overlappedFreeError – (MDA) v rozhraní .NET, který se může aktivovat při narušení přístupu nebo poškození haldy uvolňování paměti.
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
ms.openlocfilehash: 9be33c59723ecb2743f2bc610d7fb69d24ff388c
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803909"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="82e7f-103">overlappedFreeError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="82e7f-103">overlappedFreeError MDA</span></span>
<span data-ttu-id="82e7f-104">`overlappedFreeError`Pokud <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> je metoda volána před dokončením překryté operace, je aktivována funkce pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="82e7f-104">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="82e7f-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="82e7f-105">Symptoms</span></span>  
 <span data-ttu-id="82e7f-106">Narušení přístupu nebo poškození haldy uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="82e7f-106">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="82e7f-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="82e7f-107">Cause</span></span>  
 <span data-ttu-id="82e7f-108">Překrytá struktura byla uvolněna před dokončením operace.</span><span class="sxs-lookup"><span data-stu-id="82e7f-108">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="82e7f-109">Funkce, která používá překrytý ukazatel, může zapisovat do struktury později poté, co byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="82e7f-109">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="82e7f-110">To může způsobit poškození haldy, protože teď jiný objekt může tuto oblast zabírat.</span><span class="sxs-lookup"><span data-stu-id="82e7f-110">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="82e7f-111">V případě, že se překrytá operace nezačala úspěšně, tato aplikace MDA nemusí představovat chybu.</span><span class="sxs-lookup"><span data-stu-id="82e7f-111">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="82e7f-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="82e7f-112">Resolution</span></span>  
 <span data-ttu-id="82e7f-113">Před voláním metody zajistěte, aby byla vstupně-výstupní operace s použitím překryté struktury dokončená <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> .</span><span class="sxs-lookup"><span data-stu-id="82e7f-113">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="82e7f-114">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="82e7f-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="82e7f-115">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="82e7f-115">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="82e7f-116">Výstup</span><span class="sxs-lookup"><span data-stu-id="82e7f-116">Output</span></span>  
 <span data-ttu-id="82e7f-117">Níže je ukázkový výstup pro tento MDA.</span><span class="sxs-lookup"><span data-stu-id="82e7f-117">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="82e7f-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="82e7f-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82e7f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82e7f-119">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="82e7f-120">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="82e7f-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="82e7f-121">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="82e7f-121">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
