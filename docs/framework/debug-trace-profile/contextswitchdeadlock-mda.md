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
ms.openlocfilehash: fdbad4a5eb9a9d0c81ae8d29394652e9f6df136e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214430"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="51ee1-102">contextSwitchDeadlock – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="51ee1-102">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="51ee1-103">`contextSwitchDeadlock` Pomocníka spravovaného ladění (MDA) je aktivován, když bude během na pokus o přechod kontextu COM zjištěno zablokování.</span><span class="sxs-lookup"><span data-stu-id="51ee1-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="51ee1-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="51ee1-104">Symptoms</span></span>

<span data-ttu-id="51ee1-105">Nejběžnější symptomem je, že volání nespravovaného komponenty modelu COM ze spravovaného kódu nevrací.</span><span class="sxs-lookup"><span data-stu-id="51ee1-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="51ee1-106">Dalším symptomem je využití paměti v průběhu času zvětšuje.</span><span class="sxs-lookup"><span data-stu-id="51ee1-106">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="51ee1-107">příčina</span><span class="sxs-lookup"><span data-stu-id="51ee1-107">Cause</span></span>

<span data-ttu-id="51ee1-108">Nejvíce nejpravděpodobnější příčinou je, že vlákno jednovláknový apartment (STA) není – čerpání zpráv.</span><span class="sxs-lookup"><span data-stu-id="51ee1-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="51ee1-109">Vlákna STA je buď čekání bez čerpání zpráv nebo provádění operací zdlouhavé a nepovoluje žádná fronta zpráv čerpadla.</span><span class="sxs-lookup"><span data-stu-id="51ee1-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="51ee1-110">Využití paměti v průběhu času nezvyšuje je způsobeno pokusu o volání vlákna finalizační metody `Release` na nespravovaného COM komponenty a komponenty nevrací.</span><span class="sxs-lookup"><span data-stu-id="51ee1-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="51ee1-111">To zabrání finalizační metoda uvolní jiných objektů.</span><span class="sxs-lookup"><span data-stu-id="51ee1-111">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="51ee1-112">Ve výchozím nastavení modelu vláken pro hlavní vlákno konzolové aplikace jazyka Visual Basic je STA.</span><span class="sxs-lookup"><span data-stu-id="51ee1-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="51ee1-113">Toto MDA aktivováno, pokud vláknem STA. používá interoperabilita modelů COM přímo nebo nepřímo prostřednictvím common language runtime nebo jiného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="51ee1-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="51ee1-114">Vyhněte se aktivuje toto MDA v konzolové aplikace jazyka Visual Basic, použije <xref:System.MTAThreadAttribute> atribut do metody main nebo upravit aplikaci pro pumpování zpráv.</span><span class="sxs-lookup"><span data-stu-id="51ee1-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="51ee1-115">Je možné toto MDA falešně aktivaci, pokud jsou splněny všechny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="51ee1-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

-   <span data-ttu-id="51ee1-116">Aplikace vytvoří komponenty modelu COM z vláken STA přímo nebo nepřímo prostřednictvím knihoven.</span><span class="sxs-lookup"><span data-stu-id="51ee1-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

-   <span data-ttu-id="51ee1-117">Aplikace byla zastavena v ladicím programu a uživatel pokračuje aplikace nebo provést operaci kroku.</span><span class="sxs-lookup"><span data-stu-id="51ee1-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

-   <span data-ttu-id="51ee1-118">Ladění nespravovaného kódu není povolená.</span><span class="sxs-lookup"><span data-stu-id="51ee1-118">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="51ee1-119">Pokud chcete zjistit, pokud MDA falešně aktivovaná, zakázat všechny zarážky, restartujte aplikaci a povolíte jeho spuštění bez přerušení.</span><span class="sxs-lookup"><span data-stu-id="51ee1-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="51ee1-120">Pokud MDA aktivováno, je pravděpodobné, že počáteční aktivace byla hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="51ee1-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="51ee1-121">V takovém případě zakážete MDA, aby se zabránilo narušení relace ladění.</span><span class="sxs-lookup"><span data-stu-id="51ee1-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="51ee1-122">Toto MDA je ve výchozím nastavení pro sadu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="51ee1-122">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="51ee1-123">Informace o tom, jak zakázat mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span><span class="sxs-lookup"><span data-stu-id="51ee1-123">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="51ee1-124">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="51ee1-124">Resolution</span></span>

<span data-ttu-id="51ee1-125">Postupujte podle pravidla COM – čerpání zpráv STA.</span><span class="sxs-lookup"><span data-stu-id="51ee1-125">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="51ee1-126">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="51ee1-126">Effect on the Runtime</span></span>

<span data-ttu-id="51ee1-127">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="51ee1-127">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="51ee1-128">Sestavy pouze data o COM kontextech.</span><span class="sxs-lookup"><span data-stu-id="51ee1-128">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="51ee1-129">Výstup</span><span class="sxs-lookup"><span data-stu-id="51ee1-129">Output</span></span>

<span data-ttu-id="51ee1-130">Zpráva popisující aktuální kontext a cílový kontext.</span><span class="sxs-lookup"><span data-stu-id="51ee1-130">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="51ee1-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="51ee1-131">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="51ee1-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="51ee1-132">See Also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="51ee1-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="51ee1-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="51ee1-134">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="51ee1-134">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
