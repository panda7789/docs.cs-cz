---
title: "raceOnRCWCleanup – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33d1c7d91c33c194353af43deed9329b9b4ec841
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="raceonrcwcleanup-mda"></a><span data-ttu-id="f998a-102">raceOnRCWCleanup – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="f998a-102">raceOnRCWCleanup MDA</span></span>
<span data-ttu-id="f998a-103">`raceOnRCWCleanup` Pomocník spravovaného ladění (MDA) se aktivuje, když modul CLR (CLR) rozpozná, že [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) je v použijte, pokud je uskutečněn hovor pro uvolnění, například příkazem<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>metoda.</span><span class="sxs-lookup"><span data-stu-id="f998a-103">The `raceOnRCWCleanup` managed debugging assistant (MDA) is activated when the common language runtime (CLR) detects that a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) is in use when a call to release it is made using a command such as the <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f998a-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="f998a-104">Symptoms</span></span>  
 <span data-ttu-id="f998a-105">Narušení přístupu nebo poškození paměti během nebo po uvolnění k RCW pomocí <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> nebo podobné metody.</span><span class="sxs-lookup"><span data-stu-id="f998a-105">Access violations or memory corruption during or after freeing an RCW using <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> or a similar method.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f998a-106">příčina</span><span class="sxs-lookup"><span data-stu-id="f998a-106">Cause</span></span>  
 <span data-ttu-id="f998a-107">RCW se používá na jiné vlákno nebo na uvolnění zásobníku přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="f998a-107">The RCW is in use on another thread or on the freeing thread stack.</span></span>  <span data-ttu-id="f998a-108">Nelze uvolnit RCW, která je používána.</span><span class="sxs-lookup"><span data-stu-id="f998a-108">An RCW that is in use cannot be released.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f998a-109">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="f998a-109">Resolution</span></span>  
 <span data-ttu-id="f998a-110">Není bez RCW, které by mohly být v aktuální nebo jiná vlákna.</span><span class="sxs-lookup"><span data-stu-id="f998a-110">Do not free an RCW that could be in use either in the current or in other threads.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f998a-111">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="f998a-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="f998a-112">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="f998a-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f998a-113">Výstup</span><span class="sxs-lookup"><span data-stu-id="f998a-113">Output</span></span>  
 <span data-ttu-id="f998a-114">Zpráva popisující chybu.</span><span class="sxs-lookup"><span data-stu-id="f998a-114">A message describing the error.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="f998a-115">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f998a-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f998a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f998a-116">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="f998a-117">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f998a-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="f998a-118">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="f998a-118">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
