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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1a0e2a6c7851b261baa3e02f6431e7a4ff697e4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660326"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="3780b-102">contextSwitchDeadlock – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="3780b-102">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="3780b-103">`contextSwitchDeadlock` Pomocníka spravovaného ladění (MDA) je aktivován, když bude během na pokus o přechod kontextu COM zjištěno zablokování.</span><span class="sxs-lookup"><span data-stu-id="3780b-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="3780b-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="3780b-104">Symptoms</span></span>

<span data-ttu-id="3780b-105">Nejběžnější symptomem je, že volání nespravovaného komponenty modelu COM ze spravovaného kódu nevrací.</span><span class="sxs-lookup"><span data-stu-id="3780b-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="3780b-106">Dalším symptomem je využití paměti v průběhu času zvětšuje.</span><span class="sxs-lookup"><span data-stu-id="3780b-106">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="3780b-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="3780b-107">Cause</span></span>

<span data-ttu-id="3780b-108">Nejvíce nejpravděpodobnější příčinou je, že vlákno jednovláknový apartment (STA) není – čerpání zpráv.</span><span class="sxs-lookup"><span data-stu-id="3780b-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="3780b-109">Vlákna STA je buď čekání bez čerpání zpráv nebo provádění operací zdlouhavé a nepovoluje žádná fronta zpráv čerpadla.</span><span class="sxs-lookup"><span data-stu-id="3780b-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="3780b-110">Využití paměti v průběhu času nezvyšuje je způsobeno pokusu o volání vlákna finalizační metody `Release` na nespravovaného COM komponenty a komponenty nevrací.</span><span class="sxs-lookup"><span data-stu-id="3780b-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="3780b-111">To zabrání finalizační metoda uvolní jiných objektů.</span><span class="sxs-lookup"><span data-stu-id="3780b-111">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="3780b-112">Ve výchozím nastavení modelu vláken pro hlavní vlákno konzolové aplikace jazyka Visual Basic je STA.</span><span class="sxs-lookup"><span data-stu-id="3780b-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="3780b-113">Toto MDA aktivováno, pokud vláknem STA. používá interoperabilita modelů COM přímo nebo nepřímo prostřednictvím common language runtime nebo jiného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3780b-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="3780b-114">Vyhněte se aktivuje toto MDA v konzolové aplikace jazyka Visual Basic, použije <xref:System.MTAThreadAttribute> atribut do metody main nebo upravit aplikaci pro pumpování zpráv.</span><span class="sxs-lookup"><span data-stu-id="3780b-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="3780b-115">Je možné toto MDA falešně aktivaci, pokud jsou splněny všechny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="3780b-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="3780b-116">Aplikace vytvoří komponenty modelu COM z vláken STA přímo nebo nepřímo prostřednictvím knihoven.</span><span class="sxs-lookup"><span data-stu-id="3780b-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="3780b-117">Aplikace byla zastavena v ladicím programu a uživatel pokračuje aplikace nebo provést operaci kroku.</span><span class="sxs-lookup"><span data-stu-id="3780b-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="3780b-118">Ladění nespravovaného kódu není povolená.</span><span class="sxs-lookup"><span data-stu-id="3780b-118">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="3780b-119">Pokud chcete zjistit, pokud MDA falešně aktivovaná, zakázat všechny zarážky, restartujte aplikaci a povolíte jeho spuštění bez přerušení.</span><span class="sxs-lookup"><span data-stu-id="3780b-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="3780b-120">Pokud MDA aktivováno, je pravděpodobné, že počáteční aktivace byla hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="3780b-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="3780b-121">V takovém případě zakážete MDA, aby se zabránilo narušení relace ladění.</span><span class="sxs-lookup"><span data-stu-id="3780b-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="3780b-122">Toto MDA je ve výchozím nastavení pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3780b-122">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="3780b-123">Informace o tom, jak zakázat mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="3780b-123">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="3780b-124">Řešení</span><span class="sxs-lookup"><span data-stu-id="3780b-124">Resolution</span></span>

<span data-ttu-id="3780b-125">Postupujte podle pravidla COM – čerpání zpráv STA.</span><span class="sxs-lookup"><span data-stu-id="3780b-125">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="3780b-126">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="3780b-126">Effect on the Runtime</span></span>

<span data-ttu-id="3780b-127">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="3780b-127">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="3780b-128">Sestavy pouze data o COM kontextech.</span><span class="sxs-lookup"><span data-stu-id="3780b-128">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="3780b-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="3780b-129">Output</span></span>

<span data-ttu-id="3780b-130">Zpráva popisující aktuální kontext a cílový kontext.</span><span class="sxs-lookup"><span data-stu-id="3780b-130">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="3780b-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="3780b-131">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="3780b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3780b-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="3780b-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="3780b-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="3780b-134">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="3780b-134">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
