---
title: contextSwitchDeadlock – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
ms.openlocfilehash: e3fc4a2cb35cdcc713ba0ef362071083af08a27b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217557"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="3e248-102">contextSwitchDeadlock – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="3e248-102">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="3e248-103">Pokud se během přechodu kontextu modelu COM zjistí zablokování, aktivuje se Pomocník s `contextSwitchDeadlock` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="3e248-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="3e248-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="3e248-104">Symptoms</span></span>

<span data-ttu-id="3e248-105">Nejběžnějším příznakem je, že volání na nespravované součásti modelu COM ze spravovaného kódu nevrátí.</span><span class="sxs-lookup"><span data-stu-id="3e248-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="3e248-106">Dalším příznakem je využití paměti při nárůstu času.</span><span class="sxs-lookup"><span data-stu-id="3e248-106">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="3e248-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="3e248-107">Cause</span></span>

<span data-ttu-id="3e248-108">Nejpravděpodobnější příčinou je, že vlákno s jedním vláknem (STA) neprovádí pumpu zpráv.</span><span class="sxs-lookup"><span data-stu-id="3e248-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="3e248-109">Vlákno STA buď čeká bez pumpování zpráv, nebo provádí zdlouhavé operace a neumožňuje frontě zpráv pumpovat.</span><span class="sxs-lookup"><span data-stu-id="3e248-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="3e248-110">Zvýšení využití paměti v průběhu času je způsobeno tím, že se podproces finalizačního vlákna snaží volat `Release` na nespravované součásti modelu COM a tato součást nevrací.</span><span class="sxs-lookup"><span data-stu-id="3e248-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="3e248-111">To brání finalizačnímu objektu v uvolnění jiných objektů.</span><span class="sxs-lookup"><span data-stu-id="3e248-111">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="3e248-112">Ve výchozím nastavení je model vláken pro hlavní vlákno Visual Basic konzolových aplikací STA.</span><span class="sxs-lookup"><span data-stu-id="3e248-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="3e248-113">Tato aplikace MDA je aktivována, pokud vlákno STA používá interoperabilitu modelu COM přímo nebo nepřímo prostřednictvím modulu CLR (Common Language Runtime) nebo ovládacího prvku třetí strany.</span><span class="sxs-lookup"><span data-stu-id="3e248-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="3e248-114">Chcete-li se vyhnout aktivaci tohoto MDA ve Visual Basic konzolové aplikaci, použijte atribut <xref:System.MTAThreadAttribute> na metodu Main nebo upravte aplikaci na zprávy pumpy.</span><span class="sxs-lookup"><span data-stu-id="3e248-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="3e248-115">Je možné, že se tento MDA při splnění všech následujících podmínek aktivuje jako nepravdivá:</span><span class="sxs-lookup"><span data-stu-id="3e248-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="3e248-116">Aplikace vytváří komponenty modelu COM z vláken STA buď přímo, nebo nepřímo prostřednictvím knihoven.</span><span class="sxs-lookup"><span data-stu-id="3e248-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="3e248-117">Aplikace byla zastavena v ladicím programu a uživatel buď pokračoval v aplikaci, nebo provedení operace kroku.</span><span class="sxs-lookup"><span data-stu-id="3e248-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="3e248-118">Nespravované ladění není povoleno.</span><span class="sxs-lookup"><span data-stu-id="3e248-118">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="3e248-119">Chcete-li zjistit, zda je MDA nepravdivě aktivován, zakažte všechny zarážky, restartujte aplikaci a umožněte její spuštění bez zastavení.</span><span class="sxs-lookup"><span data-stu-id="3e248-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="3e248-120">Pokud není modul MDA aktivován, je pravděpodobnější, že počáteční aktivace byla nepravdivá.</span><span class="sxs-lookup"><span data-stu-id="3e248-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="3e248-121">V takovém případě zakažte režim MDA, aby se zabránilo interferenci s relací ladění.</span><span class="sxs-lookup"><span data-stu-id="3e248-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="3e248-122">Tento MDA je ve výchozí sadě pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e248-122">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="3e248-123">Informace o tom, jak zakázat MDA, najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="3e248-123">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="3e248-124">Řešení</span><span class="sxs-lookup"><span data-stu-id="3e248-124">Resolution</span></span>

<span data-ttu-id="3e248-125">Sledujte pravidla modelu COM týkající se čerpacích zpráv STA.</span><span class="sxs-lookup"><span data-stu-id="3e248-125">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="3e248-126">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="3e248-126">Effect on the Runtime</span></span>

<span data-ttu-id="3e248-127">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="3e248-127">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="3e248-128">Pouze hlásí data o kontextech COM.</span><span class="sxs-lookup"><span data-stu-id="3e248-128">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="3e248-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="3e248-129">Output</span></span>

<span data-ttu-id="3e248-130">Zpráva popisující aktuální kontext a cílový kontext.</span><span class="sxs-lookup"><span data-stu-id="3e248-130">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="3e248-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="3e248-131">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="3e248-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e248-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3e248-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="3e248-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3e248-134">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="3e248-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
