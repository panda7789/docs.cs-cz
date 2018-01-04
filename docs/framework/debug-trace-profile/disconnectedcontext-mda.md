---
title: "disconnectedContext – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90e840fc24361735b65879702293daadce0bc90e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="43dcd-102">disconnectedContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="43dcd-102">disconnectedContext MDA</span></span>
<span data-ttu-id="43dcd-103">`disconnectedContext` Pomocník spravovaného ladění (MDA) se aktivuje, když se modul CLR pokusí o přechod do odpojeného oddílu nebo kontextu během obsluhy žádost týkající se objektu COM.</span><span class="sxs-lookup"><span data-stu-id="43dcd-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="43dcd-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="43dcd-104">Symptoms</span></span>  
 <span data-ttu-id="43dcd-105">Volání na [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) budou doručeny do základní komponenty modelu COM v aktuálním oddílu nebo kontextu místo jeden, ve které existují.</span><span class="sxs-lookup"><span data-stu-id="43dcd-105">Calls made on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="43dcd-106">To může způsobit poškození a nebo ztráty dat, pokud není součást COM s více vlákny, jako v případě součásti single-threaded apartment (STA).</span><span class="sxs-lookup"><span data-stu-id="43dcd-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="43dcd-107">Případně, pokud RCW se proxy server, volání může dojít k vyvolání z <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="43dcd-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="43dcd-108">příčina</span><span class="sxs-lookup"><span data-stu-id="43dcd-108">Cause</span></span>  
 <span data-ttu-id="43dcd-109">OLE oddílu nebo kontextu byla vypnuta při modulu CLR pokusí o přechod do ní.</span><span class="sxs-lookup"><span data-stu-id="43dcd-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="43dcd-110">To je nejčastěji způsobeno STA bytů, které právě vypíná před všechny komponenty modelu COM, které vlastní typu apartment úplně byly vydané to může nastat v důsledku explicitní volání z uživatelského kódu RCW nebo při CLR samotné je manipulace s komponenty modelu COM , například když modulu CLR vydává komponenty modelu COM při přidružené RCW byl uvolnění z paměti.</span><span class="sxs-lookup"><span data-stu-id="43dcd-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="43dcd-111">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="43dcd-111">Resolution</span></span>  
 <span data-ttu-id="43dcd-112">K tomuto problému nedošlo, zajistěte, aby vlákno, které vlastní STA nezavře aplikaci ještě před ukončením se všemi objekty, které existují v typu apartment.</span><span class="sxs-lookup"><span data-stu-id="43dcd-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="43dcd-113">Totéž platí i pro kontexty; Zkontrolujte, zda nejsou kontexty vypne, než je zcela dokončení všech součástí modelu COM, které za provozu v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="43dcd-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="43dcd-114">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="43dcd-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="43dcd-115">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="43dcd-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="43dcd-116">Pouze sestavy data o odpojený kontext.</span><span class="sxs-lookup"><span data-stu-id="43dcd-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="43dcd-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="43dcd-117">Output</span></span>  
 <span data-ttu-id="43dcd-118">Sestavy soubor cookie kontextu odpojeného oddílu nebo kontextu.</span><span class="sxs-lookup"><span data-stu-id="43dcd-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="43dcd-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="43dcd-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43dcd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="43dcd-120">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="43dcd-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="43dcd-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="43dcd-122">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="43dcd-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
