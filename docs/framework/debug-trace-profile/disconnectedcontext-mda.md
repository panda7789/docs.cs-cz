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
ms.openlocfilehash: 8f125d322a5a3e2841d6b1ba1f2f8d5fe9745870
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569700"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="78aba-102">disconnectedContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="78aba-102">disconnectedContext MDA</span></span>
<span data-ttu-id="78aba-103">`disconnectedContext` Pomocníka spravovaného ladění (MDA) se aktivuje, když modul CLR se pokusí o přechod do odpojeného oddílu nebo kontextu během obsluhy žádost o objekt modelu COM.</span><span class="sxs-lookup"><span data-stu-id="78aba-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="78aba-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="78aba-104">Symptoms</span></span>  
 <span data-ttu-id="78aba-105">Volání [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) se doručí nadřazená komponenta modelu COM v aktuálním oddílu nebo kontextu místo ten, ve kterém existují.</span><span class="sxs-lookup"><span data-stu-id="78aba-105">Calls made on a [Runtime Callable Wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="78aba-106">To může způsobit poškození a nebo ztrátu nejsou-li komponenta modelu COM s více vlákny, stejně jako v případě komponenty jednovláknový apartment (STA).</span><span class="sxs-lookup"><span data-stu-id="78aba-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="78aba-107">Případně, pokud Obálka RCW je samotný proxy serveru, volání může vést vyvolání sady <xref:System.Runtime.InteropServices.COMException> s HRESULT RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="78aba-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="78aba-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="78aba-108">Cause</span></span>  
 <span data-ttu-id="78aba-109">OLE oddílu nebo kontextu má byla ukončena, když modul CLR se pokusí přejít do něj.</span><span class="sxs-lookup"><span data-stu-id="78aba-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="78aba-110">To je nejčastěji způsobeno objekty apartment STA vypíná před všechny komponenty modelu COM typu apartment vlastněné byly zcela to může nastat v důsledku explicitního volání z uživatelského kódu na obálky RCW, nebo když samotný modul CLR je manipulace s komponenty modelu COM , třeba když CLR vydává komponenty modelu COM při přidružené RCW byla uvolněna z paměti.</span><span class="sxs-lookup"><span data-stu-id="78aba-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="78aba-111">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="78aba-111">Resolution</span></span>  
 <span data-ttu-id="78aba-112">K tomuto problému vyhnout, zajistěte, aby vlákno, které vlastní STA nebyl ukončen před dokončením příkazu se u všech objektů, kteří žijí v typu apartment aplikace.</span><span class="sxs-lookup"><span data-stu-id="78aba-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="78aba-113">Totéž platí i pro kontexty; Zajistěte, aby kontexty nevypnou, než se aplikace úplně dokončená všechny komponenty modelu COM, kteří žijí v kontextu.</span><span class="sxs-lookup"><span data-stu-id="78aba-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="78aba-114">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="78aba-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="78aba-115">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="78aba-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="78aba-116">Sestavy pouze data o odpojený kontext.</span><span class="sxs-lookup"><span data-stu-id="78aba-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="78aba-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="78aba-117">Output</span></span>  
 <span data-ttu-id="78aba-118">Sestavy soubor cookie kontextu odpojeného oddílu nebo kontextu.</span><span class="sxs-lookup"><span data-stu-id="78aba-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="78aba-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="78aba-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78aba-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78aba-120">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="78aba-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="78aba-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="78aba-122">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="78aba-122">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
