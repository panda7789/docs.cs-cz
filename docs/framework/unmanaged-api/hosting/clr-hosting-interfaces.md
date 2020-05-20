---
title: Rozhraní hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: e6913e18a4ff6e616f357a4ef43fb8b892264943
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616837"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="ba46b-102">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ba46b-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="ba46b-103">Tato část popisuje rozhraní, která nespravované hostitele můžou použít k integraci modulu CLR (Common Language Runtime) do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="ba46b-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="ba46b-104">Informace se týkají .NET Framework verze 2,0 a novějších verzí.</span><span class="sxs-lookup"><span data-stu-id="ba46b-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="ba46b-105">Tato rozhraní umožňují hostiteli řídit mnoho dalších aspektů modulu runtime, než bylo možné ve verzích 1,0 a 1,1, a poskytovat mnohem užší integraci mezi CLR a prováděcím modelem hostitele.</span><span class="sxs-lookup"><span data-stu-id="ba46b-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="ba46b-106">V .NET Framework verze 1,0 a 1,1 hostující model povolil nespravovanému hostiteli, aby načetl CLR do procesu, aby nakonfiguroval určitá nastavení a přijímal oznámení události.</span><span class="sxs-lookup"><span data-stu-id="ba46b-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="ba46b-107">Obecně platí, že hostitel a CLR běžely nezávisle na tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="ba46b-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="ba46b-108">V .NET Framework verze 2,0 a novějších mají nové vrstvy abstrakce poskytnout hostiteli mnoho prostředků aktuálně poskytovaných typy v sestavení Win32 a rozšíření sady funkcí, které může hostitel konfigurovat.</span><span class="sxs-lookup"><span data-stu-id="ba46b-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba46b-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ba46b-109">In This Section</span></span>  
 [<span data-ttu-id="ba46b-110">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-110">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)  
 <span data-ttu-id="ba46b-111">Poskytuje metodu, která provádí zpětné volání pro registrovanou událost.</span><span class="sxs-lookup"><span data-stu-id="ba46b-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="ba46b-112">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-112">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)  
 <span data-ttu-id="ba46b-113">Poskytuje metody pro provádění zpětných volání v rámci objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="ba46b-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="ba46b-114">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-114">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)  
 <span data-ttu-id="ba46b-115">Poskytuje metody pro nastavení konfigurace běhového běhu.</span><span class="sxs-lookup"><span data-stu-id="ba46b-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="ba46b-116">ICatalogServices – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-116">ICatalogServices Interface</span></span>](icatalogservices-interface.md)  
 <span data-ttu-id="ba46b-117">Poskytuje metody pro služby katalogu.</span><span class="sxs-lookup"><span data-stu-id="ba46b-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="ba46b-118">(Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="ba46b-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="ba46b-119">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-119">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="ba46b-120">Poskytuje metody, které podporují komunikaci mezi hostitelem a CLR o sestaveních.</span><span class="sxs-lookup"><span data-stu-id="ba46b-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="ba46b-121">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="ba46b-122">Spravuje seznam sestavení, která jsou načtena modulem CLR a nikoli hostitelem.</span><span class="sxs-lookup"><span data-stu-id="ba46b-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="ba46b-123">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)  
 <span data-ttu-id="ba46b-124">Poskytuje metody pro hostitele k získání přístupu a konfiguraci různých aspektů, CLR.</span><span class="sxs-lookup"><span data-stu-id="ba46b-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="ba46b-125">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)  
 <span data-ttu-id="ba46b-126">Poskytuje metody, které umožňují hostiteli přidružit sadu úkolů s identifikátorem a popisným názvem.</span><span class="sxs-lookup"><span data-stu-id="ba46b-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="ba46b-127">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-127">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="ba46b-128">Poskytuje metody, které hostiteli umožňují nakonfigurovat vlastní výpisy paměti haldy pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="ba46b-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="ba46b-129">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-129">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)  
 <span data-ttu-id="ba46b-130">Poskytuje metody, které umožňují hostiteli pracovat se systémem uvolňování paměti CLR.</span><span class="sxs-lookup"><span data-stu-id="ba46b-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="ba46b-131">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-131">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="ba46b-132">Poskytuje metody pro hostitele k vyhodnocení a předávání změn v informacích o zásadách pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="ba46b-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="ba46b-133">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-133">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="ba46b-134">Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole ze spouštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="ba46b-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="ba46b-135">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-135">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)  
 <span data-ttu-id="ba46b-136">Implementuje metodu zpětného volání, která umožňuje hostiteli informovat modul CLR o stavu specifikovaných vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="ba46b-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="ba46b-137">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="ba46b-138">Umožňuje hostiteli hlásit podmínky pro tlak paměti pomocí přístupu podobného `CreateMemoryResourceNotification` funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="ba46b-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="ba46b-139">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-139">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)  
 <span data-ttu-id="ba46b-140">Poskytuje metody, které umožňují hostiteli registrovat a odregistrovat zpětná volání pro události CLR.</span><span class="sxs-lookup"><span data-stu-id="ba46b-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="ba46b-141">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-141">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)  
 <span data-ttu-id="ba46b-142">Poskytuje metody, které umožňují hostiteli určit akce zásad, které mají být provedeny v případě selhání a časových limitů.</span><span class="sxs-lookup"><span data-stu-id="ba46b-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="ba46b-143">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="ba46b-144">Poskytuje metody, které umožňují hostiteli získat identity sestavení pomocí informací o identitě sestavení, které jsou interní pro CLR, a to bez nutnosti vytvořit nebo porozumět této identitě.</span><span class="sxs-lookup"><span data-stu-id="ba46b-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="ba46b-145">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-145">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="ba46b-146">Poskytuje metody, které umožňují hostiteli manipulovat s množinou sestavení, na které odkazuje soubor nebo datový proud, pomocí dat identity sestavení, která jsou interní pro CLR, aniž by bylo nutné tyto identity vytvářet nebo porozumět.</span><span class="sxs-lookup"><span data-stu-id="ba46b-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="ba46b-147">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-147">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)  
 <span data-ttu-id="ba46b-148">Poskytuje možnosti podobné [ICorRuntimeHost](icorruntimehost-interface.md), s další metodou pro nastavení rozhraní pro řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="ba46b-148">Provides capabilities similar to [ICorRuntimeHost](icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="ba46b-149">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-149">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)  
 <span data-ttu-id="ba46b-150">Poskytuje metody pro hostitele k získání informací o požadovaných úlohách a k detekci zablokování v jeho implementaci synchronizace.</span><span class="sxs-lookup"><span data-stu-id="ba46b-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="ba46b-151">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-151">ICLRTask Interface</span></span>](iclrtask-interface.md)  
 <span data-ttu-id="ba46b-152">Poskytuje metody, které umožňují hostiteli vytvářet požadavky CLR, nebo poskytovat oznámení modulu CLR o přidružené úloze.</span><span class="sxs-lookup"><span data-stu-id="ba46b-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="ba46b-153">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-153">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)  
 <span data-ttu-id="ba46b-154">Poskytuje metody, které umožňují hostiteli explicitně požádat, aby CLR vytvořil nový úkol, získal aktuálně spuštěnou úlohu a pro úkol nastavil zeměpisný jazyk a jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="ba46b-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="ba46b-155">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-155">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)  
 <span data-ttu-id="ba46b-156">Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.</span><span class="sxs-lookup"><span data-stu-id="ba46b-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="ba46b-157">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-157">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)  
 <span data-ttu-id="ba46b-158">Poskytuje metody pro konfiguraci CLR.</span><span class="sxs-lookup"><span data-stu-id="ba46b-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="ba46b-159">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-159">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)  
 <span data-ttu-id="ba46b-160">Poskytuje metody pro přístup ke fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="ba46b-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="ba46b-161">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-161">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)  
 <span data-ttu-id="ba46b-162">Poskytuje metody pro získání informací o stavu služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="ba46b-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="ba46b-163">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-163">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="ba46b-164">Poskytuje metody pro upozorňování hostitele na blokování a odblokování vláken pomocí služby ladění.</span><span class="sxs-lookup"><span data-stu-id="ba46b-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="ba46b-165">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-165">IGCHost Interface</span></span>](igchost-interface.md)  
 <span data-ttu-id="ba46b-166">Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ba46b-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="ba46b-167">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-167">IGCHost2 Interface</span></span>](igchost2-interface.md)  
 <span data-ttu-id="ba46b-168">Poskytuje metodu [SetGCStartupLimitsEx –](igchost2-setgcstartuplimitsex-method.md) , která umožňuje hostiteli nastavit velikost segmentu uvolňování paměti a maximální velikost generace systému uvolňování paměti na hodnoty větší než `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="ba46b-168">Provides the [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="ba46b-169">IGCHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-169">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)  
 <span data-ttu-id="ba46b-170">Poskytuje metodu, která umožňuje systému uvolňování paměti požádat hostitele o změnu omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="ba46b-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="ba46b-171">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-171">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)  
 <span data-ttu-id="ba46b-172">Poskytuje metody pro účast v plánování vláken, která by jinak byla zablokována pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ba46b-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="ba46b-173">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-173">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)  
 <span data-ttu-id="ba46b-174">Poskytuje metody, které umožňují hostiteli určit sady sestavení, které by měly být načteny modulem CLR nebo hostitelem.</span><span class="sxs-lookup"><span data-stu-id="ba46b-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="ba46b-175">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-175">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)  
 <span data-ttu-id="ba46b-176">Poskytuje metody, které umožňují hostiteli načíst sestavení a moduly nezávisle na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ba46b-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="ba46b-177">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-177">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)  
 <span data-ttu-id="ba46b-178">Poskytuje reprezentaci události automatického resetování implementované hostitelem.</span><span class="sxs-lookup"><span data-stu-id="ba46b-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="ba46b-179">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-179">IHostControl Interface</span></span>](ihostcontrol-interface.md)  
 <span data-ttu-id="ba46b-180">Poskytuje metody pro konfiguraci načítání sestavení a pro určení, která hostující rozhraní hostitel podporuje.</span><span class="sxs-lookup"><span data-stu-id="ba46b-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="ba46b-181">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-181">IHostCrst Interface</span></span>](ihostcrst-interface.md)  
 <span data-ttu-id="ba46b-182">Slouží jako reprezentace kritické části pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="ba46b-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="ba46b-183">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-183">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)  
 <span data-ttu-id="ba46b-184">Poskytuje metody, které upozorňují na hostitele událostí v mechanizmu uvolňování paměti implementované modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="ba46b-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="ba46b-185">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-185">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="ba46b-186">Poskytuje metody, které umožňují CLR pracovat s porty dokončovacího vstupu a výstupu poskytnutými hostitelem.</span><span class="sxs-lookup"><span data-stu-id="ba46b-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="ba46b-187">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-187">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)  
 <span data-ttu-id="ba46b-188">Poskytuje metody pro modul CLR pro vyžádat detailní přidělení z haldy prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="ba46b-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="ba46b-189">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-189">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)  
 <span data-ttu-id="ba46b-190">Poskytuje implementaci reprezentace události ručního resetování hostitele.</span><span class="sxs-lookup"><span data-stu-id="ba46b-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="ba46b-191">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-191">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)  
 <span data-ttu-id="ba46b-192">Poskytuje metody pro CLR k vytváření požadavků virtuální paměti prostřednictvím hostitele namísto použití standardních funkcí virtuální paměti Win32.</span><span class="sxs-lookup"><span data-stu-id="ba46b-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="ba46b-193">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-193">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)  
 <span data-ttu-id="ba46b-194">Poskytuje metody, které upozorňují na hostitele akcí, které CLR provede v případě přerušení, vypršení časového limitu nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="ba46b-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="ba46b-195">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-195">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)  
 <span data-ttu-id="ba46b-196">Umožňuje modulu CLR zachovat informace o kontextu zabezpečení implementované hostitelem.</span><span class="sxs-lookup"><span data-stu-id="ba46b-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="ba46b-197">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-197">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)  
 <span data-ttu-id="ba46b-198">Poskytuje metody, které umožňují přístup a řízení nad, kontext zabezpečení aktuálně prováděného vlákna.</span><span class="sxs-lookup"><span data-stu-id="ba46b-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="ba46b-199">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-199">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)  
 <span data-ttu-id="ba46b-200">Poskytuje reprezentace semaforu implementovaného hostitelem.</span><span class="sxs-lookup"><span data-stu-id="ba46b-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="ba46b-201">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-201">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="ba46b-202">Poskytuje metody pro modul CLR k vytváření synchronizačních primitiv voláním hostitele namísto použití synchronizačních funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="ba46b-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="ba46b-203">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-203">IHostTask Interface</span></span>](ihosttask-interface.md)  
 <span data-ttu-id="ba46b-204">Poskytuje metody, které umožňují, aby CLR komunikoval s hostitelem a spravoval úlohy.</span><span class="sxs-lookup"><span data-stu-id="ba46b-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="ba46b-205">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-205">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)  
 <span data-ttu-id="ba46b-206">Poskytuje metody, které umožňují CLR pracovat s úlohami přes hostitele namísto použití standardních vláken operačního systému nebo funkcí Fiber.</span><span class="sxs-lookup"><span data-stu-id="ba46b-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="ba46b-207">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-207">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="ba46b-208">Poskytuje metody pro CLR ke konfiguraci fondu vláken a k zařazení pracovních položek do fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="ba46b-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="ba46b-209">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-209">IManagedObject Interface</span></span>](imanagedobject-interface.md)  
 <span data-ttu-id="ba46b-210">Poskytuje metody pro řízení spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="ba46b-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="ba46b-211">IObjectHandle –</span><span class="sxs-lookup"><span data-stu-id="ba46b-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="ba46b-212">Poskytuje metodu pro rozbalení objektů Marshal-to-Value z dereference.</span><span class="sxs-lookup"><span data-stu-id="ba46b-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="ba46b-213">ITypeName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-213">ITypeName Interface</span></span>](itypename-interface.md)  
 <span data-ttu-id="ba46b-214">Poskytuje metody pro získání informací o názvu typu.</span><span class="sxs-lookup"><span data-stu-id="ba46b-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="ba46b-215">(Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="ba46b-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="ba46b-216">ITypeNameBuilder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-216">ITypeNameBuilder Interface</span></span>](itypenamebuilder-interface.md)  
 <span data-ttu-id="ba46b-217">Poskytuje metody pro sestavení názvu typu.</span><span class="sxs-lookup"><span data-stu-id="ba46b-217">Provides methods for building a type name.</span></span> <span data-ttu-id="ba46b-218">(Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="ba46b-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="ba46b-219">ITypeNameFactory – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba46b-219">ITypeNameFactory Interface</span></span>](itypenamefactory-interface.md)  
 <span data-ttu-id="ba46b-220">Poskytuje metody pro dekonstrukci názvu typu.</span><span class="sxs-lookup"><span data-stu-id="ba46b-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="ba46b-221">(Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="ba46b-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="ba46b-222">IValidator</span><span class="sxs-lookup"><span data-stu-id="ba46b-222">"IValidator"</span></span>  
 <span data-ttu-id="ba46b-223">Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.</span><span class="sxs-lookup"><span data-stu-id="ba46b-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ba46b-224">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ba46b-224">Related Sections</span></span>  
 [<span data-ttu-id="ba46b-225">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ba46b-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="ba46b-226">Obsahuje témata, která popisují rozhraní hostování poskytované v .NET Framework verze 1,0 a 1,1.</span><span class="sxs-lookup"><span data-stu-id="ba46b-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="ba46b-227">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="ba46b-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="ba46b-228">Obsahuje témata, která popisují rozhraní hostování poskytované v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ba46b-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>
