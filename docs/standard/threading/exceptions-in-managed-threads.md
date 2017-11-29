---
title: "Výjimky ve spravovaných vláknech"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ebb5559d300bb3db34fe640e87eb8b9e67931561
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-in-managed-threads"></a><span data-ttu-id="0e5bd-102">Výjimky ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="0e5bd-102">Exceptions in Managed Threads</span></span>
<span data-ttu-id="0e5bd-103">Od verze rozhraní .NET Framework verze 2.0, modul common language runtime umožňuje nejvíce neošetřených výjimek v vláken přirozeně pokračovat.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-103">Starting with the .NET Framework version 2.0, the common language runtime allows most unhandled exceptions in threads to proceed naturally.</span></span> <span data-ttu-id="0e5bd-104">Ve většině případů to znamená, že neošetřené výjimce způsobí, že je aplikace ukončena.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-104">In most cases this means that the unhandled exception causes the application to terminate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e5bd-105">Toto je významné změny z rozhraní .NET Framework verze 1.0 a 1.1, které přinášejí mnoho neošetřených výjimek backstop – například neošetřené výjimky v podprocesy z fondu podprocesů.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-105">This is a significant change from the .NET Framework versions 1.0 and 1.1, which provide a backstop for many unhandled exceptions — for example, unhandled exceptions in thread pool threads.</span></span> <span data-ttu-id="0e5bd-106">V tématu [změnit z předchozích verzí](#ChangeFromPreviousVersions) dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-106">See [Change from Previous Versions](#ChangeFromPreviousVersions) later in this topic.</span></span>  
  
 <span data-ttu-id="0e5bd-107">Modul common language runtime poskytuje backstop určité neošetřené výjimky, které se používají pro řízení toku programu:</span><span class="sxs-lookup"><span data-stu-id="0e5bd-107">The common language runtime provides a backstop for certain unhandled exceptions that are used for controlling program flow:</span></span>  
  
-   <span data-ttu-id="0e5bd-108">A <xref:System.Threading.ThreadAbortException> je vyvolána v vlákno, protože <xref:System.Threading.Thread.Abort%2A> byla volána.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-108">A <xref:System.Threading.ThreadAbortException> is thrown in a thread because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
-   <span data-ttu-id="0e5bd-109"><xref:System.AppDomainUnloadedException> Je vyvolána v vlákno, protože odpojení doménu aplikace, ve kterém je prováděna vlákno.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-109">An <xref:System.AppDomainUnloadedException> is thrown in a thread because the application domain in which the thread is executing is being unloaded.</span></span>  
  
-   <span data-ttu-id="0e5bd-110">Modul common language runtime nebo hostitelský proces se ukončuje vlákno podle došlo k vnitřní výjimce.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-110">The common language runtime or a host process terminates the thread by throwing an internal exception.</span></span>  
  
 <span data-ttu-id="0e5bd-111">Pokud jsou tyto výjimky neošetřené v vláken vytvořený modul common language runtime, výjimka ukončí vlákno, ale modul common language runtime neumožňuje výjimka, která má pokračovat.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-111">If any of these exceptions are unhandled in threads created by the common language runtime, the exception terminates the thread, but the common language runtime does not allow the exception to proceed further.</span></span>  
  
 <span data-ttu-id="0e5bd-112">Pokud jsou tyto výjimky neošetřené do hlavního vlákna nebo vláken, které zadali modulu runtime z nespravovaného kódu, budou pokračovat vést k ukončení aplikace za normálních okolností.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-112">If these exceptions are unhandled in the main thread, or in threads that entered the runtime from unmanaged code, they proceed normally, resulting in termination of the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e5bd-113">Je možné pro modul runtime má být vyvolána k neošetřené výjimce před spravovaný kód dostal příležitost k instalaci obslužnou rutinu výjimky.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-113">It is possible for the runtime to throw an unhandled exception before any managed code has had a chance to install an exception handler.</span></span> <span data-ttu-id="0e5bd-114">I když spravovaného kódu dříve žádné šanci na zpracování takové výjimky, může pokračovat přirozeně výjimku.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-114">Even though managed code had no chance to handle such an exception, the exception is allowed to proceed naturally.</span></span>  
  
## <a name="exposing-threading-problems-during-development"></a><span data-ttu-id="0e5bd-115">Vystavení vlákna problémy během vývoje</span><span class="sxs-lookup"><span data-stu-id="0e5bd-115">Exposing Threading Problems During Development</span></span>  
 <span data-ttu-id="0e5bd-116">Pokud vláken mají povoleno selhání tiše, bez ukončení aplikace, může pokračovat nezjištěné programovací vážným problémům.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-116">When threads are allowed to fail silently, without terminating the application, serious programming problems can go undetected.</span></span> <span data-ttu-id="0e5bd-117">Toto je konkrétního problému služeb a dalších aplikací, které se spustit po delší dobu.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-117">This is a particular problem for services and other applications which run for extended periods.</span></span> <span data-ttu-id="0e5bd-118">Jako vláken nezdaří, je poškozena postupně stav programu.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-118">As threads fail, program state gradually becomes corrupted.</span></span> <span data-ttu-id="0e5bd-119">Může snížit výkon aplikace nebo aplikace může přestat reagovat.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-119">Application performance may degrade, or the application might hang.</span></span>  
  
 <span data-ttu-id="0e5bd-120">Povolení neošetřených výjimek v vláken samozřejmě pokračovat, dokud operační systém ukončuje programu, zpřístupní takovým problémům během vývoje a testování.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-120">Allowing unhandled exceptions in threads to proceed naturally, until the operating system terminates the program, exposes such problems during development and testing.</span></span> <span data-ttu-id="0e5bd-121">Zprávy o chybách na program ukončení podpory ladění.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-121">Error reports on program terminations support debugging.</span></span>  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a><span data-ttu-id="0e5bd-122">Změnit z předchozích verzí</span><span class="sxs-lookup"><span data-stu-id="0e5bd-122">Change from Previous Versions</span></span>  
 <span data-ttu-id="0e5bd-123">Nejdůležitější změny se vztahují na spravovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-123">The most significant change pertains to managed threads.</span></span> <span data-ttu-id="0e5bd-124">V rozhraní .NET Framework verze 1.0 a 1.1 poskytuje modul common language runtime backstop neošetřené výjimky v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="0e5bd-124">In the .NET Framework versions 1.0 and 1.1, the common language runtime provides a backstop for unhandled exceptions in the following situations:</span></span>  
  
-   <span data-ttu-id="0e5bd-125">Neexistuje žádný takový akci jako k neošetřené výjimce v podprocesu fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-125">There is no such thing as an unhandled exception on a thread pool thread.</span></span> <span data-ttu-id="0e5bd-126">Pokud úloha vyvolá výjimku, který nezpracovává, modul runtime vytiskne trasování zásobníku výjimky ke konzole a vrátí do fondu vláken vlákno.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-126">When a task throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then returns the thread to the thread pool.</span></span>  
  
-   <span data-ttu-id="0e5bd-127">Neexistuje žádná taková věc k neošetřené výjimce v podprocesu vytvořeného s <xref:System.Threading.Thread.Start%2A> metodu <xref:System.Threading.Thread> třídy.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-127">There is no such thing as an unhandled exception on a thread created with the <xref:System.Threading.Thread.Start%2A> method of the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="0e5bd-128">Pokud kód spuštěný na takové vlákno vyvolá výjimku, který nezpracovává, modul runtime vytiskne trasování zásobníku výjimky ke konzole a řádně ukončí vlákno.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-128">When code running on such a thread throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then gracefully terminates the thread.</span></span>  
  
-   <span data-ttu-id="0e5bd-129">Neexistuje žádná taková věc jako neošetřená výjimka ve vláknu finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-129">There is no such thing as an unhandled exception on the finalizer thread.</span></span> <span data-ttu-id="0e5bd-130">Pokud finalizační metody vyvolá výjimku, který nezpracovává, modul runtime vytiskne trasování zásobníku výjimky do konzoly a pak umožňuje vlákno finalizační metodu obnovit systémem finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-130">When a finalizer throws an exception that it does not handle, the runtime prints the exception stack trace to the console and then allows the finalizer thread to resume running finalizers.</span></span>  
  
 <span data-ttu-id="0e5bd-131">Stav popředí nebo pozadí spravované vlákno toto chování neovlivňuje.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-131">The foreground or background status of a managed thread does not affect this behavior.</span></span>  
  
 <span data-ttu-id="0e5bd-132">Pro neošetřených výjimek na vláken z nespravovaného kódu je další menší rozdíl.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-132">For unhandled exceptions on threads originating in unmanaged code, the difference is more subtle.</span></span> <span data-ttu-id="0e5bd-133">JIT – připojené dialogu runtime brání dialogu operačního systému pro spravované výjimky nebo nativní výjimky na vláken, které uplynuly prostřednictvím nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-133">The runtime JIT-attach dialog preempts the operating system dialog for managed exceptions or native exceptions on threads that have passed through native code.</span></span> <span data-ttu-id="0e5bd-134">Proces se ukončuje ve všech případech.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-134">The process terminates in all cases.</span></span>  
  
### <a name="migrating-code"></a><span data-ttu-id="0e5bd-135">Migrace kódu</span><span class="sxs-lookup"><span data-stu-id="0e5bd-135">Migrating Code</span></span>  
 <span data-ttu-id="0e5bd-136">Obecně platí změna zveřejní dříve nerozpoznané programovací problémy tak, aby odstraněny.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-136">In general, the change will expose previously unrecognized programming problems so that they can be fixed.</span></span> <span data-ttu-id="0e5bd-137">V některých případech ale programátory může využili backstop modulu runtime, např. Chcete-li ukončit vláken.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-137">In some cases, however, programmers might have taken advantage of the runtime backstop, for example to terminate threads.</span></span> <span data-ttu-id="0e5bd-138">V závislosti na situaci že měli zvážit jednu z následujících strategií migrace:</span><span class="sxs-lookup"><span data-stu-id="0e5bd-138">Depending on the situation, they should consider one of the following migration strategies:</span></span>  
  
-   <span data-ttu-id="0e5bd-139">Změnit strukturu kód, aby vlákno ukončí řádně, když je obdržena signál.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-139">Restructure the code so the thread exits gracefully when a signal is received.</span></span>  
  
-   <span data-ttu-id="0e5bd-140">Použití <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metoda k přerušení vlákno.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-140">Use the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method to abort the thread.</span></span>  
  
-   <span data-ttu-id="0e5bd-141">Pokud vlákno musí být zastaven, ukončení procesu mohli pokračovat, ujistěte se, vlákno vlákna na pozadí tak, aby je automaticky ukončen na ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-141">If a thread must be stopped so that process termination can proceed, make the thread a background thread so that it is automatically terminated on process exit.</span></span>  
  
 <span data-ttu-id="0e5bd-142">Ve všech případech strategie postupujte podle pokynů pro návrh pro výjimky.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-142">In all cases, the strategy should follow the design guidelines for exceptions.</span></span> <span data-ttu-id="0e5bd-143">V tématu [návrh pokyny pro výjimky](../../../docs/standard/design-guidelines/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="0e5bd-143">See [Design Guidelines for Exceptions](../../../docs/standard/design-guidelines/exceptions.md).</span></span>  
  
### <a name="application-compatibility-flag"></a><span data-ttu-id="0e5bd-144">Příznak kompatibility aplikace</span><span class="sxs-lookup"><span data-stu-id="0e5bd-144">Application Compatibility Flag</span></span>  
 <span data-ttu-id="0e5bd-145">Z důvodu dočasného kompatibility správci můžete umístit příznak kompatibility ve `<runtime>` oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-145">As a temporary compatibility measure, administrators can place a compatibility flag in the `<runtime>` section of the application configuration file.</span></span> <span data-ttu-id="0e5bd-146">To způsobí, že modul common language runtime se vrátit k chování verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-146">This causes the common language runtime to revert to the behavior of versions 1.0 and 1.1.</span></span>  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a><span data-ttu-id="0e5bd-147">Přepsání hostitele</span><span class="sxs-lookup"><span data-stu-id="0e5bd-147">Host Override</span></span>  
 <span data-ttu-id="0e5bd-148">V rozhraní .NET Framework verze 2.0, můžete použít nespravované hostitele [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) rozhraní v rozhraní API hostování přepsat výchozí nastavení neošetřená výjimka zásady modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-148">In the .NET Framework version 2.0, an unmanaged host can use the [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface in the Hosting API to override the default unhandled exception policy of the common language runtime.</span></span> <span data-ttu-id="0e5bd-149">[Iclrpolicymanager::setunhandledexceptionpolicy –](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) funkce slouží k nastavení zásad pro neošetřených výjimek.</span><span class="sxs-lookup"><span data-stu-id="0e5bd-149">The [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) function is used to set the policy for unhandled exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e5bd-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e5bd-150">See Also</span></span>  
 [<span data-ttu-id="0e5bd-151">Dělení na spravovaná vlákna základy</span><span class="sxs-lookup"><span data-stu-id="0e5bd-151">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
