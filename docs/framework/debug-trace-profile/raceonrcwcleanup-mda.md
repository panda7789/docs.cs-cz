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
ms.openlocfilehash: 628790bb8229dc519589c122235f07a38ba57c1c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100233"
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="8809d-102">raceOnRCWCleanup – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="8809d-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="8809d-103">`raceOnRCWCleanup` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) zjistí, že [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) se používá v Pokud je uskutečněn hovor pro uvolnění, například příkazem<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>metody.</span><span class="sxs-lookup"><span data-stu-id="8809d-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="8809d-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="8809d-104">Symptoms</span></span>  
 <span data-ttu-id="8809d-105">Narušení přístupu nebo poškození paměti během nebo po jeho uvolnění obálky RCW pomocí <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> nebo podobné metody.</span><span class="sxs-lookup"><span data-stu-id="8809d-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="8809d-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="8809d-106">Cause</span></span>  
 <span data-ttu-id="8809d-107">Obálka RCW je používána jiným vláknem nebo uvolnění zásobníku vlákna.</span><span class="sxs-lookup"><span data-stu-id="8809d-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="8809d-108">Nelze uvolnit obálky RCW, která se používá.</span><span class="sxs-lookup"><span data-stu-id="8809d-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="8809d-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="8809d-109">Resolution</span></span>  
 <span data-ttu-id="8809d-110">Neuvolní obálky RCW, která může být používán v aktuální nebo v jiných vláken.</span><span class="sxs-lookup"><span data-stu-id="8809d-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="8809d-111">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="8809d-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="8809d-112">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="8809d-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="8809d-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="8809d-113">Output</span></span>  
 <span data-ttu-id="8809d-114">Zpráva popisující chybu.</span><span class="sxs-lookup"><span data-stu-id="8809d-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="8809d-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8809d-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8809d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8809d-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="8809d-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="8809d-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8809d-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="8809d-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
