---
title: overlappedFreeError – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 675e2e4d5022f0260450f9f0b2025f215b3ead7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708283"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="819c7-102">overlappedFreeError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="819c7-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="819c7-103">`overlappedFreeError` Pomocníka spravovaného ladění (MDA) se aktivuje při <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> metoda je volána před dokončením překrytá operace.</span><span class="sxs-lookup"><span data-stu-id="819c7-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="819c7-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="819c7-104">Symptoms</span></span>  
 <span data-ttu-id="819c7-105">Narušení přístupu nebo poškození haldy uvolňování.</span><span class="sxs-lookup"><span data-stu-id="819c7-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="819c7-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="819c7-106">Cause</span></span>  
 <span data-ttu-id="819c7-107">Překryté struktury byl uvolněn před operace se dokončila.</span><span class="sxs-lookup"><span data-stu-id="819c7-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="819c7-108">Funkce, která používá překrytý ukazatel může zapisovat do struktury později, jakmile byl uvolněn.</span><span class="sxs-lookup"><span data-stu-id="819c7-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="819c7-109">To může způsobit poškození haldy, protože jiný objekt může zabírat teď tuto oblast.</span><span class="sxs-lookup"><span data-stu-id="819c7-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="819c7-110">Toto MDA nemusí reprezentovat chybu, pokud překrytá operace nebyla úspěšně spuštěna.</span><span class="sxs-lookup"><span data-stu-id="819c7-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="819c7-111">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="819c7-111">Resolution</span></span>  
 <span data-ttu-id="819c7-112">Ujistěte se, že dokončení vstupně-výstupní operace pomocí překryté struktury před voláním <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> metody.</span><span class="sxs-lookup"><span data-stu-id="819c7-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="819c7-113">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="819c7-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="819c7-114">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="819c7-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="819c7-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="819c7-115">Output</span></span>  
 <span data-ttu-id="819c7-116">Zde je ukázkový výstup pro toto MDA.</span><span class="sxs-lookup"><span data-stu-id="819c7-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="819c7-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="819c7-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="819c7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="819c7-118">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="819c7-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="819c7-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="819c7-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="819c7-120">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
