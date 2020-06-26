---
title: disconnectedContext – pomocník spravovaného ladění (MDA)
description: Přečtěte si pomocníka spravovaného ladění Disconnectedcontext – v rozhraní .NET, který je vyvolán, když se CLR pokusí přejít do odpojeného izolovaného prostředí nebo kontextu.
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 0b24aadefab7a7cb2a5294f25e674d188beec814
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416080"
---
# <a name="disconnectedcontext-mda"></a><span data-ttu-id="78565-103">disconnectedContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="78565-103">disconnectedContext MDA</span></span>
<span data-ttu-id="78565-104">`disconnectedContext`Pomocník spravovaného ladění (MDA) se aktivuje, když se modul CLR pokusí přejít do odpojeného izolovaného modelu nebo kontextu a přitom obsluhuje požadavek týkající se objektu com.</span><span class="sxs-lookup"><span data-stu-id="78565-104">The `disconnectedContext` managed debugging assistant (MDA) is activated when the CLR attempts to transition into a disconnected apartment or context while servicing a request concerning a COM object.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="78565-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="78565-105">Symptoms</span></span>  
 <span data-ttu-id="78565-106">Volání na obálku s voláním [za běhu](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) se doručí do základní komponenty modelu COM v aktuálním objektu Apartment nebo kontextu, nikoli v takovém případě, ve kterém existují.</span><span class="sxs-lookup"><span data-stu-id="78565-106">Calls made on a [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) are delivered to the underlying COM component in the current apartment or context instead of the one in which they exist.</span></span> <span data-ttu-id="78565-107">To může způsobit poškození nebo ztrátu dat, pokud komponenta modelu COM není Vícevláknová, jako v případě komponent typu STA (Single-threaded Apartment).</span><span class="sxs-lookup"><span data-stu-id="78565-107">This can cause corruption and or data loss if the COM component is not multithreaded, as in the case of single-threaded apartment (STA) components.</span></span> <span data-ttu-id="78565-108">Alternativně, pokud je RCW samotný proxy, volání může způsobit vyvolání a <xref:System.Runtime.InteropServices.COMException> s hodnotou HRESULT RPC_E_WRONG_THREAD.</span><span class="sxs-lookup"><span data-stu-id="78565-108">Alternatively, if the RCW is itself a proxy, the call might result in the throwing of a <xref:System.Runtime.InteropServices.COMException> with an HRESULT of RPC_E_WRONG_THREAD.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="78565-109">Příčina</span><span class="sxs-lookup"><span data-stu-id="78565-109">Cause</span></span>  
 <span data-ttu-id="78565-110">Objekt Apartment nebo kontext OLE byl vypnut, když se modul CLR pokusí přejít do něj.</span><span class="sxs-lookup"><span data-stu-id="78565-110">The OLE apartment or context has been shut down when the CLR attempts to transition into it.</span></span> <span data-ttu-id="78565-111">To je nejčastěji způsobeno tím, že se neukončí všechny komponenty modelu COM, které jsou vlastněny objektem Apartment, a to v důsledku explicitního volání z uživatelského kódu na RCW nebo v případě, že samotný CLR pracuje s komponentou modelu COM, například když modul CLR uvolňuje komponentu COM, když je přidružený RCW uvolněn z paměti.</span><span class="sxs-lookup"><span data-stu-id="78565-111">This is most commonly caused by STA apartments being shut down before all the COM components owned by the apartment were completely released This can occur as a result of an explicit call from user code on an RCW or while the CLR itself is manipulating the COM component, for example when the CLR is releasing the COM component when the associated RCW has been garbage collected.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="78565-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="78565-112">Resolution</span></span>  
 <span data-ttu-id="78565-113">Chcete-li se tomuto problému vyhnout, zajistěte, aby vlákno, které vlastní STA, neukončilo před dokončením aplikace všemi objekty, které jsou v objektu Apartment v provozu.</span><span class="sxs-lookup"><span data-stu-id="78565-113">To avoid this problem, ensure the thread that owns the STA does not terminate before the application has finished with all the objects that live in the apartment.</span></span> <span data-ttu-id="78565-114">Totéž platí pro kontexty; Ujistěte se, že kontexty nejsou vypnuté předtím, než se aplikace kompletně dokončí všemi komponentami modelu COM, které jsou v daném kontextu aktivní.</span><span class="sxs-lookup"><span data-stu-id="78565-114">The same applies to contexts; ensure contexts are not shut down before the application is completely finished with any COM components that live inside the context.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="78565-115">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="78565-115">Effect on the Runtime</span></span>  
 <span data-ttu-id="78565-116">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="78565-116">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="78565-117">Pouze hlásí data o odpojeném kontextu.</span><span class="sxs-lookup"><span data-stu-id="78565-117">It only reports data about the disconnected context.</span></span>  
  
## <a name="output"></a><span data-ttu-id="78565-118">Výstup</span><span class="sxs-lookup"><span data-stu-id="78565-118">Output</span></span>  
 <span data-ttu-id="78565-119">Oznamuje kontextový soubor cookie odpojeného objektu Apartment nebo kontextu.</span><span class="sxs-lookup"><span data-stu-id="78565-119">Reports the context cookie of the disconnected apartment or context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="78565-120">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="78565-120">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78565-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="78565-121">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="78565-122">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="78565-122">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="78565-123">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="78565-123">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
