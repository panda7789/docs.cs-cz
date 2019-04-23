---
title: disconnectedContext – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb42c04df6e02ff43421b7af6bf2d51b53aa3e69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181972"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="1eaec-102">disconnectedContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="1eaec-102">disconnectedContext MDA</span></span>
<span data-ttu-id="1eaec-103">`disconnectedContext` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR se pokusí o přechod do odpojeného oddílu nebo kontextu během obsluhy žádost o objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="1eaec-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1eaec-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="1eaec-104">Symptoms</span></span>  
 <span data-ttu-id="1eaec-105">Volání [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) se doručí nadřazená komponenta modelu COM v aktuálním oddílu nebo kontextu místo ten, ve kterém existují.</span><span class="sxs-lookup"><span data-stu-id="1eaec-105">Calls made on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="1eaec-106">To může způsobit poškození a nebo ztrátu nejsou-li komponenta modelu COM s více vlákny, stejně jako v případě komponenty jednovláknový apartment (STA).</span><span class="sxs-lookup"><span data-stu-id="1eaec-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="1eaec-107">Případně, pokud Obálka RCW je samotný proxy serveru, volání může vést vyvolání sady <xref:System.Runtime.InteropServices.COMException> s HRESULT RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="1eaec-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1eaec-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="1eaec-108">Cause</span></span>  
 <span data-ttu-id="1eaec-109">OLE oddílu nebo kontextu má byla ukončena, když modul CLR se pokusí přejít do něj.</span><span class="sxs-lookup"><span data-stu-id="1eaec-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="1eaec-110">To je nejčastěji způsobeno objekty apartment STA vypíná před všechny komponenty modelu COM typu apartment vlastněné byly zcela to může nastat v důsledku explicitního volání z uživatelského kódu na obálky RCW, nebo když samotný modul CLR je manipulace s komponenty modelu COM , třeba když CLR vydává komponenty modelu COM při přidružené RCW byla uvolněna z paměti.</span><span class="sxs-lookup"><span data-stu-id="1eaec-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1eaec-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="1eaec-111">Resolution</span></span>  
 <span data-ttu-id="1eaec-112">K tomuto problému vyhnout, zajistěte, aby vlákno, které vlastní STA nebyl ukončen před dokončením příkazu se u všech objektů, kteří žijí v typu apartment aplikace.</span><span class="sxs-lookup"><span data-stu-id="1eaec-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="1eaec-113">Totéž platí i pro kontexty; Zajistěte, aby kontexty nevypnou, než se aplikace úplně dokončená všechny komponenty modelu COM, kteří žijí v kontextu.</span><span class="sxs-lookup"><span data-stu-id="1eaec-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1eaec-114">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="1eaec-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="1eaec-115">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="1eaec-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="1eaec-116">Sestavy pouze data o odpojený kontext.</span><span class="sxs-lookup"><span data-stu-id="1eaec-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1eaec-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="1eaec-117">Output</span></span>  
 <span data-ttu-id="1eaec-118">Sestavy soubor cookie kontextu odpojeného oddílu nebo kontextu.</span><span class="sxs-lookup"><span data-stu-id="1eaec-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="1eaec-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1eaec-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1eaec-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1eaec-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1eaec-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="1eaec-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1eaec-122">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="1eaec-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
