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
ms.openlocfilehash: 8a0c72cf26ef8434719ff6661ef15a44f51c8740
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217253"
---
# <a name="overlappedfreeerror-mda"></a><span data-ttu-id="83640-102">overlappedFreeError – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="83640-102">overlappedFreeError MDA</span></span>
<span data-ttu-id="83640-103">Pokud je metoda <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> volána před dokončením překrývající se operace, je aktivována funkce Pomocník pro Managed debugginger (MDA) `overlappedFreeError`.</span><span class="sxs-lookup"><span data-stu-id="83640-103">The `overlappedFreeError` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> method is called before the overlapped operation has completed.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="83640-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="83640-104">Symptoms</span></span>  
 <span data-ttu-id="83640-105">Narušení přístupu nebo poškození haldy uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="83640-105">Access violations or corruption of the garbage-collected heap.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="83640-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="83640-106">Cause</span></span>  
 <span data-ttu-id="83640-107">Překrytá struktura byla uvolněna před dokončením operace.</span><span class="sxs-lookup"><span data-stu-id="83640-107">An overlapped structure was freed before the operation completed.</span></span> <span data-ttu-id="83640-108">Funkce, která používá překrytý ukazatel, může zapisovat do struktury později poté, co byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="83640-108">The function that is using the overlapped pointer might write to the structure later, after it has been freed.</span></span> <span data-ttu-id="83640-109">To může způsobit poškození haldy, protože teď jiný objekt může tuto oblast zabírat.</span><span class="sxs-lookup"><span data-stu-id="83640-109">That can cause heap corruption because another object might now occupy that region.</span></span>  
  
 <span data-ttu-id="83640-110">V případě, že se překrytá operace nezačala úspěšně, tato aplikace MDA nemusí představovat chybu.</span><span class="sxs-lookup"><span data-stu-id="83640-110">This MDA might not represent an error if the overlapped operation did not start successfully.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="83640-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="83640-111">Resolution</span></span>  
 <span data-ttu-id="83640-112">Před voláním metody <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> zajistěte, aby vstupně-výstupní operace s použitím překryté struktury byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="83640-112">Ensure that the I/O operation using the overlapped structure has completed before calling the <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="83640-113">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="83640-113">Effect on the Runtime</span></span>  
 <span data-ttu-id="83640-114">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="83640-114">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="83640-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="83640-115">Output</span></span>  
 <span data-ttu-id="83640-116">Níže je ukázkový výstup pro tento MDA.</span><span class="sxs-lookup"><span data-stu-id="83640-116">The following is sample output for this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="83640-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="83640-117">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="83640-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="83640-118">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="83640-119">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="83640-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="83640-120">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="83640-120">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
