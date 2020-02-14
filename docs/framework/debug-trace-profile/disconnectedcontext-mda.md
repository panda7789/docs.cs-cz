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
ms.openlocfilehash: 3d04e304a6b30fe6fd4deeda5a97007f11ee7b13
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216535"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="83892-102">disconnectedContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="83892-102">disconnectedContext MDA</span></span>
<span data-ttu-id="83892-103">Pokud se modul CLR pokusí přejít do odpojeného izolovaného modelu nebo kontextu a současně obsluhuje požadavek týkající se objektu COM, aktivuje se Pomocník s `disconnectedContext` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="83892-103">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="83892-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="83892-104">Symptoms</span></span>  
 <span data-ttu-id="83892-105">Volání na obálku s voláním [za běhu](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) se doručí do základní komponenty modelu COM v aktuálním objektu Apartment nebo kontextu, nikoli v takovém případě, ve kterém existují.</span><span class="sxs-lookup"><span data-stu-id="83892-105">Calls made on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="83892-106">To může způsobit poškození nebo ztrátu dat, pokud komponenta modelu COM není Vícevláknová, jako v případě komponent typu STA (Single-threaded Apartment).</span><span class="sxs-lookup"><span data-stu-id="83892-106">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="83892-107">Alternativně, pokud je RCW samotný proxy, volání může způsobit vyvolání <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="83892-107">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="83892-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="83892-108">Cause</span></span>  
 <span data-ttu-id="83892-109">Objekt Apartment nebo kontext OLE byl vypnut, když se modul CLR pokusí přejít do něj.</span><span class="sxs-lookup"><span data-stu-id="83892-109">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="83892-110">To je nejčastěji způsobeno tím, že se neukončí všechny komponenty modelu COM vlastněné objektem Apartment. Tato situace může nastat jako výsledek explicitního volání z uživatelského kódu na RCW nebo v případě, že samotný CLR pracuje s komponentou COM. , například když modul CLR uvolňuje komponentu COM, když je přidružený RCW uvolněn z paměti.</span><span class="sxs-lookup"><span data-stu-id="83892-110">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="83892-111">Řešení</span><span class="sxs-lookup"><span data-stu-id="83892-111">Resolution</span></span>  
 <span data-ttu-id="83892-112">Chcete-li se tomuto problému vyhnout, zajistěte, aby vlákno, které vlastní STA, neukončilo před dokončením aplikace všemi objekty, které jsou v objektu Apartment v provozu.</span><span class="sxs-lookup"><span data-stu-id="83892-112">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="83892-113">Totéž platí pro kontexty; Ujistěte se, že kontexty nejsou vypnuté předtím, než se aplikace kompletně dokončí všemi komponentami modelu COM, které jsou v daném kontextu aktivní.</span><span class="sxs-lookup"><span data-stu-id="83892-113">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="83892-114">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="83892-114">Effect on the Runtime</span></span>  
 <span data-ttu-id="83892-115">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="83892-115">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="83892-116">Pouze hlásí data o odpojeném kontextu.</span><span class="sxs-lookup"><span data-stu-id="83892-116">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="83892-117">Výstup</span><span class="sxs-lookup"><span data-stu-id="83892-117">Output</span></span>  
 <span data-ttu-id="83892-118">Oznamuje kontextový soubor cookie odpojeného objektu Apartment nebo kontextu.</span><span class="sxs-lookup"><span data-stu-id="83892-118">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="83892-119">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="83892-119">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="83892-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="83892-120">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="83892-121">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="83892-121">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="83892-122">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="83892-122">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
