---
title: raceOnRCWCleanup – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09e3b275bfaa5743c0271578df97f92269ac7c86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386893"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="972a6-102">raceOnRCWCleanup – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="972a6-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="972a6-103">`raceOnRCWCleanup` Pomocník spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) rozpozná, že [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) je v použijte, pokud je uskutečněn hovor pro uvolnění, například příkazem<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>metoda.</span><span class="sxs-lookup"><span data-stu-id="972a6-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="972a6-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="972a6-104">Symptoms</span></span>  
 <span data-ttu-id="972a6-105">Narušení přístupu nebo poškození paměti během nebo po uvolnění k RCW pomocí <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> nebo podobné metody.</span><span class="sxs-lookup"><span data-stu-id="972a6-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="972a6-106">příčina</span><span class="sxs-lookup"><span data-stu-id="972a6-106">Cause</span></span>  
 <span data-ttu-id="972a6-107">RCW se používá na jiné vlákno nebo na uvolnění zásobníku přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="972a6-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="972a6-108">Nelze uvolnit RCW, která je používána.</span><span class="sxs-lookup"><span data-stu-id="972a6-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="972a6-109">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="972a6-109">Resolution</span></span>  
 <span data-ttu-id="972a6-110">Není bez RCW, které by mohly být v aktuální nebo jiná vlákna.</span><span class="sxs-lookup"><span data-stu-id="972a6-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="972a6-111">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="972a6-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="972a6-112">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="972a6-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="972a6-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="972a6-113">Output</span></span>  
 <span data-ttu-id="972a6-114">Zpráva popisující chybu.</span><span class="sxs-lookup"><span data-stu-id="972a6-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="972a6-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="972a6-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="972a6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="972a6-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="972a6-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="972a6-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="972a6-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="972a6-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
