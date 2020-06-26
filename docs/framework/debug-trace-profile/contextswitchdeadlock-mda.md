---
title: contextSwitchDeadlock – pomocník spravovaného ladění (MDA)
description: Přečtěte si o Pomocníkovi pro Managed Debugging contextSwitchDeadlock – (MDA) v rozhraní .NET, který se aktivuje při zjištění vzájemného zablokování během přechodu kontextu modelu COM.
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
ms.openlocfilehash: 52db4f2c88bac4e8cac621cca989fa10acb43f94
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416015"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="cb346-103">contextSwitchDeadlock – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="cb346-103">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="cb346-104">`contextSwitchDeadlock`Pomocník spravovaného ladění (MDA) je aktivován při zjištění vzájemného zablokování při pokusu o přechod kontextu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cb346-104">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="cb346-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="cb346-105">Symptoms</span></span>

<span data-ttu-id="cb346-106">Nejběžnějším příznakem je, že volání na nespravované součásti modelu COM ze spravovaného kódu nevrátí.</span><span class="sxs-lookup"><span data-stu-id="cb346-106">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="cb346-107">Dalším příznakem je využití paměti při nárůstu času.</span><span class="sxs-lookup"><span data-stu-id="cb346-107">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="cb346-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="cb346-108">Cause</span></span>

<span data-ttu-id="cb346-109">Nejpravděpodobnější příčinou je, že vlákno s jedním vláknem (STA) neprovádí pumpu zpráv.</span><span class="sxs-lookup"><span data-stu-id="cb346-109">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="cb346-110">Vlákno STA buď čeká bez pumpování zpráv, nebo provádí zdlouhavé operace a neumožňuje frontě zpráv pumpovat.</span><span class="sxs-lookup"><span data-stu-id="cb346-110">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="cb346-111">Zvýšení využití paměti v průběhu času je způsobeno tím, že se podproces finalizačního procesu pokusí zavolat `Release` na nespravovanou komponentu modelu COM a tato součást se nevrátí.</span><span class="sxs-lookup"><span data-stu-id="cb346-111">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="cb346-112">To brání finalizačnímu objektu v uvolnění jiných objektů.</span><span class="sxs-lookup"><span data-stu-id="cb346-112">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="cb346-113">Ve výchozím nastavení je model vláken pro hlavní vlákno Visual Basic konzolových aplikací STA.</span><span class="sxs-lookup"><span data-stu-id="cb346-113">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="cb346-114">Tato aplikace MDA je aktivována, pokud vlákno STA používá interoperabilitu modelu COM přímo nebo nepřímo prostřednictvím modulu CLR (Common Language Runtime) nebo ovládacího prvku třetí strany.</span><span class="sxs-lookup"><span data-stu-id="cb346-114">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="cb346-115">Chcete-li se vyhnout aktivaci tohoto MDA ve Visual Basic konzolové aplikaci, použijte <xref:System.MTAThreadAttribute> atribut na metodu Main nebo upravte aplikaci na zprávy pumpy.</span><span class="sxs-lookup"><span data-stu-id="cb346-115">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="cb346-116">Je možné, že se tento MDA při splnění všech následujících podmínek aktivuje jako nepravdivá:</span><span class="sxs-lookup"><span data-stu-id="cb346-116">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="cb346-117">Aplikace vytváří komponenty modelu COM z vláken STA buď přímo, nebo nepřímo prostřednictvím knihoven.</span><span class="sxs-lookup"><span data-stu-id="cb346-117">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="cb346-118">Aplikace byla zastavena v ladicím programu a uživatel buď pokračoval v aplikaci, nebo provedení operace kroku.</span><span class="sxs-lookup"><span data-stu-id="cb346-118">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="cb346-119">Nespravované ladění není povoleno.</span><span class="sxs-lookup"><span data-stu-id="cb346-119">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="cb346-120">Chcete-li zjistit, zda je MDA nepravdivě aktivován, zakažte všechny zarážky, restartujte aplikaci a umožněte její spuštění bez zastavení.</span><span class="sxs-lookup"><span data-stu-id="cb346-120">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="cb346-121">Pokud není modul MDA aktivován, je pravděpodobnější, že počáteční aktivace byla nepravdivá.</span><span class="sxs-lookup"><span data-stu-id="cb346-121">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="cb346-122">V takovém případě zakažte režim MDA, aby se zabránilo interferenci s relací ladění.</span><span class="sxs-lookup"><span data-stu-id="cb346-122">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="cb346-123">Tento MDA je ve výchozí sadě pro Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb346-123">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="cb346-124">Informace o tom, jak zakázat MDA, najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="cb346-124">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="cb346-125">Řešení</span><span class="sxs-lookup"><span data-stu-id="cb346-125">Resolution</span></span>

<span data-ttu-id="cb346-126">Sledujte pravidla modelu COM týkající se čerpacích zpráv STA.</span><span class="sxs-lookup"><span data-stu-id="cb346-126">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="cb346-127">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="cb346-127">Effect on the Runtime</span></span>

<span data-ttu-id="cb346-128">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="cb346-128">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="cb346-129">Pouze hlásí data o kontextech COM.</span><span class="sxs-lookup"><span data-stu-id="cb346-129">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="cb346-130">Výstup</span><span class="sxs-lookup"><span data-stu-id="cb346-130">Output</span></span>

<span data-ttu-id="cb346-131">Zpráva popisující aktuální kontext a cílový kontext.</span><span class="sxs-lookup"><span data-stu-id="cb346-131">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="cb346-132">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="cb346-132">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="cb346-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb346-133">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="cb346-134">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="cb346-134">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="cb346-135">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="cb346-135">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
