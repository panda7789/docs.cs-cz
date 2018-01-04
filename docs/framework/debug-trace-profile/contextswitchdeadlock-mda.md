---
title: "contextSwitchDeadlock – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 816afbae0cca18de24c11152541a509b54c119b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="9fafe-102">contextSwitchDeadlock – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="9fafe-102">contextSwitchDeadlock MDA</span></span>
<span data-ttu-id="9fafe-103">`contextSwitchDeadlock` Pomocník spravovaného ladění (MDA) se aktivuje, když bude během pokusu o přechod kontextu COM zjištěno zablokování.</span><span class="sxs-lookup"><span data-stu-id="9fafe-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="9fafe-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="9fafe-104">Symptoms</span></span>  
 <span data-ttu-id="9fafe-105">Nejběžnější symptomem je, že se nevrací volání nespravovaného komponentu COM ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9fafe-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="9fafe-106">Dalším symptomem je využití paměti v průběhu času zvětšuje.</span><span class="sxs-lookup"><span data-stu-id="9fafe-106">Another symptom is memory usage increasing over time.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="9fafe-107">příčina</span><span class="sxs-lookup"><span data-stu-id="9fafe-107">Cause</span></span>  
 <span data-ttu-id="9fafe-108">Nejvíce pravděpodobné příčiny je, že vlákno single-threaded apartment (STA) není čerpání – zprávy.</span><span class="sxs-lookup"><span data-stu-id="9fafe-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="9fafe-109">STA vlákno je buď čekání bez čerpání zpráv nebo provádí náročná operace a nepovolí fronty zpráv čerpadla.</span><span class="sxs-lookup"><span data-stu-id="9fafe-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>  
  
 <span data-ttu-id="9fafe-110">Využití paměti v průběhu času zvětšuje je způsobena finalizační metodu vlákno pokus o volání `Release` na nespravované modelu COM není vrácení součásti a součást.</span><span class="sxs-lookup"><span data-stu-id="9fafe-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="9fafe-111">To brání tomu, aby finalizační metodu opětovného získání jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="9fafe-111">This prevents the finalizer from reclaiming other objects.</span></span>  
  
 <span data-ttu-id="9fafe-112">Výchozí hodnota je STA modelu vláken pro hlavní vlákno konzolové aplikace jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9fafe-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="9fafe-113">Tato MDA je aktivována, pokud zřetězení STA používá interoperabilita modelů COM přímo nebo nepřímo přes modul common language runtime nebo ovládacího prvku třetích stran.</span><span class="sxs-lookup"><span data-stu-id="9fafe-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="9fafe-114">Abyste se vyhnuli aktivace této MDA v konzolové aplikaci jazyka Visual Basic, použít <xref:System.MTAThreadAttribute> atribut hlavní metodu nebo upravit aplikaci na čerpadlo zprávy.</span><span class="sxs-lookup"><span data-stu-id="9fafe-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>  
  
 <span data-ttu-id="9fafe-115">Je možné pro tento MDA k nesprávně aktivovat, pokud jsou splněny všechny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="9fafe-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="9fafe-116">Aplikace vytvoří komponenty modelu COM z vláken STA přímo nebo nepřímo prostřednictvím knihovny.</span><span class="sxs-lookup"><span data-stu-id="9fafe-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>  
  
-   <span data-ttu-id="9fafe-117">Aplikace byla zastavena v ladicím programu a uživatel dál aplikace nebo provést operaci kroku.</span><span class="sxs-lookup"><span data-stu-id="9fafe-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>  
  
-   <span data-ttu-id="9fafe-118">Nespravované ladění není povoleno.</span><span class="sxs-lookup"><span data-stu-id="9fafe-118">Unmanaged debugging is not enabled.</span></span>  
  
 <span data-ttu-id="9fafe-119">Pokud chcete zjistit, pokud MDA nesprávně aktivován, zakažte všechny zarážky, restartujte aplikaci a povolit jeho spuštění bez zastavení.</span><span class="sxs-lookup"><span data-stu-id="9fafe-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="9fafe-120">Pokud MDA není aktivováno, je pravděpodobné, že původní aktivace je chybná.</span><span class="sxs-lookup"><span data-stu-id="9fafe-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="9fafe-121">V takovém případě zakážete MDA, aby se zabránilo narušení s relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="9fafe-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9fafe-122">Tato (mda) je ve výchozím nastavení pro [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="9fafe-122">This MDA is in the default set for [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and later versions.</span></span> <span data-ttu-id="9fafe-123">Když je proces hostování povoleno v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], nelze zakázat mda, které jsou ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="9fafe-123">When the hosting process is enabled in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], you cannot disable MDAs that are in the default set.</span></span> <span data-ttu-id="9fafe-124">Proces hostování je zapnutá ve výchozím nastavení, takže musí být explicitně zakázány.</span><span class="sxs-lookup"><span data-stu-id="9fafe-124">The hosting process is enabled by default, so it must be explicitly disabled.</span></span> <span data-ttu-id="9fafe-125">Informace o tom, jak zakázat mda, najdete v části "Povolení a zákaz mda" v [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="9fafe-125">For information about how to disable MDAs, see "Enabling and Disabling MDAs" in [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="9fafe-126">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="9fafe-126">Resolution</span></span>  
 <span data-ttu-id="9fafe-127">Postupujte podle COM pravidla týkající se STA čerpání zpráv.</span><span class="sxs-lookup"><span data-stu-id="9fafe-127">Follow COM rules regarding STA message pumping.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9fafe-128">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="9fafe-128">Effect on the Runtime</span></span>  
 <span data-ttu-id="9fafe-129">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="9fafe-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="9fafe-130">Pouze sestavy data o kontextech COM.</span><span class="sxs-lookup"><span data-stu-id="9fafe-130">It only reports data about COM contexts.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9fafe-131">Výstup</span><span class="sxs-lookup"><span data-stu-id="9fafe-131">Output</span></span>  
 <span data-ttu-id="9fafe-132">Zpráva popisující aktuální kontext a cílový kontext.</span><span class="sxs-lookup"><span data-stu-id="9fafe-132">A message describing the current context and the target context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9fafe-133">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9fafe-133">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fafe-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="9fafe-134">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="9fafe-135">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="9fafe-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="9fafe-136">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="9fafe-136">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
