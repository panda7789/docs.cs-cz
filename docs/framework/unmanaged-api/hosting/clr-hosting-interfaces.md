---
title: Rozhraní hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80404e65263aa4ad245a8c8213630a4736bd7b11
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456884"
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="6c25d-102">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6c25d-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="6c25d-103">Tato část popisuje rozhraní, která nespravovaných hostitelů můžete použít k integraci common language runtime (CLR) do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="6c25d-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="6c25d-104">Informace se vztahují na rozhraní .NET Framework verze 2.0 a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="6c25d-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="6c25d-105">Tato rozhraní umožňují hostitele tak, aby řízení více aspektů modul runtime, než bylo možné ve verzích 1.0 a 1.1 a poskytují mnohem užší integraci modulu CLR a spouštěcí model hostitele.</span><span class="sxs-lookup"><span data-stu-id="6c25d-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="6c25d-106">Model hostingu v rozhraní .NET Framework verze 1.0 a 1.1, povolené nespravovaný hostitel načíst modul CLR do procesu, nakonfigurovat některá nastavení a získat oznámení události.</span><span class="sxs-lookup"><span data-stu-id="6c25d-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="6c25d-107">Ale obecně platí, hostitele a CLR spustili nezávisle na sobě v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="6c25d-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="6c25d-108">V rozhraní .NET Framework verze 2.0 a novějších verzích nových úrovní abstrakce umožní hostovat poskytují mnoho prostředků, které jsou aktuálně k dispozici typy v sestavení Win32 a rozšířit sadu funkcí, které můžete nakonfigurovat hostitele.</span><span class="sxs-lookup"><span data-stu-id="6c25d-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c25d-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6c25d-109">In This Section</span></span>  
 [<span data-ttu-id="6c25d-110">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-110">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 <span data-ttu-id="6c25d-111">Poskytuje metodu, která provede zpětné volání pro registrované události.</span><span class="sxs-lookup"><span data-stu-id="6c25d-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="6c25d-112">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-112">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 <span data-ttu-id="6c25d-113">Poskytuje metody pro provádění zpětných volání v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="6c25d-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="6c25d-114">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-114">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 <span data-ttu-id="6c25d-115">Poskytuje metody pro konfiguraci nastavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="6c25d-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="6c25d-116">ICatalogServices – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-116">ICatalogServices Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 <span data-ttu-id="6c25d-117">Poskytuje metody pro vytváření katalogu služeb.</span><span class="sxs-lookup"><span data-stu-id="6c25d-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="6c25d-118">(Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="6c25d-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6c25d-119">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="6c25d-120">Poskytuje metody, které podporují komunikaci mezi hostitelem a CLR o sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c25d-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="6c25d-121">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="6c25d-122">Spravuje seznam sestavení, která jsou načtena pomocí modulu CLR a ne hostiteli.</span><span class="sxs-lookup"><span data-stu-id="6c25d-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="6c25d-123">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-123">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 <span data-ttu-id="6c25d-124">Poskytuje metody pro hostitele k získání přístupu k a konfigurovat různé funkce modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6c25d-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="6c25d-125">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 <span data-ttu-id="6c25d-126">Poskytuje metody, které umožní hostitele do sady úloh přidružit identifikátor a popisný název.</span><span class="sxs-lookup"><span data-stu-id="6c25d-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="6c25d-127">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-127">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="6c25d-128">Poskytuje metody, které umožní hostitele tak, aby konfigurace výpisů paměti haldy vlastní pro hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="6c25d-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="6c25d-129">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-129">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 <span data-ttu-id="6c25d-130">Poskytuje metody, které umožní hostitele k interakci se systémem kolekce uvolnění paměti modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6c25d-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="6c25d-131">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-131">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="6c25d-132">Poskytuje metody pro hostitele k vyhodnocení a Oznamovat změny v informace o zásadách pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c25d-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="6c25d-133">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-133">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="6c25d-134">Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole spouštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="6c25d-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="6c25d-135">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-135">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 <span data-ttu-id="6c25d-136">Implementuje metodu zpětného volání, která umožňuje hostiteli oznámit CLR stav zadaného vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="6c25d-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="6c25d-137">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="6c25d-138">Umožňuje hostiteli podmínky přetížení paměti sestavy pomocí metodiky podobný Win32 `CreateMemoryResourceNotification` funkce.</span><span class="sxs-lookup"><span data-stu-id="6c25d-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="6c25d-139">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-139">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 <span data-ttu-id="6c25d-140">Poskytuje metody, které umožní hostitele tak, aby vytvářet a rušit registraci zpětná volání pro události CLR.</span><span class="sxs-lookup"><span data-stu-id="6c25d-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="6c25d-141">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 <span data-ttu-id="6c25d-142">Poskytuje metody, které umožní hostitele k určení akce zásad, které mají být provedeny v případě selhání a vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="6c25d-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="6c25d-143">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="6c25d-144">Poskytuje metody, které umožní získat zkušební identity sestavení s použitím identity informací o sestavení, který je interní modul CLR, aniž by bylo nutné vytvořit nebo pochopit tuto identitu hostitele.</span><span class="sxs-lookup"><span data-stu-id="6c25d-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="6c25d-145">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-145">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="6c25d-146">Poskytuje metody, které umožní hostitele k manipulaci s sadu sestavení odkazuje na soubor nebo datový proud pomocí data identitu sestavení, která je interní modul CLR, aniž by bylo nutné vytvořit nebo pochopit tyto identity.</span><span class="sxs-lookup"><span data-stu-id="6c25d-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="6c25d-147">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-147">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 <span data-ttu-id="6c25d-148">Poskytuje funkce podobné [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), s další způsob, jak nastavit ovládací prvek rozhraní hostitele.</span><span class="sxs-lookup"><span data-stu-id="6c25d-148">Provides capabilities similar to [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="6c25d-149">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-149">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 <span data-ttu-id="6c25d-150">Poskytuje metody pro hostitele a získat informace o požadované úlohy zjišťování případů zablokování v rámci příslušné implementace synchronizace.</span><span class="sxs-lookup"><span data-stu-id="6c25d-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="6c25d-151">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 <span data-ttu-id="6c25d-152">Poskytuje metody, které umožní hostitele k podání žádostí o modulu CLR, nebo k poskytování oznámení o přidružené úloze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6c25d-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="6c25d-153">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-153">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 <span data-ttu-id="6c25d-154">Poskytuje metody, které umožní hostitele tak, aby explicitně vyžádat CLR vytvoří nový úkol, získat právě prováděnou úlohu a nastavit geografické jazyk a jazykovou verzi pro úlohu.</span><span class="sxs-lookup"><span data-stu-id="6c25d-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="6c25d-155">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-155">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 <span data-ttu-id="6c25d-156">Poskytuje metody pro ověřování přenosné spustitelné (PE) bitové kopie a oznamování chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c25d-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="6c25d-157">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-157">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 <span data-ttu-id="6c25d-158">Poskytuje metody pro konfiguraci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6c25d-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="6c25d-159">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-159">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 <span data-ttu-id="6c25d-160">Poskytuje metody pro přístup k fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="6c25d-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="6c25d-161">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-161">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 <span data-ttu-id="6c25d-162">Poskytuje metody pro získání informací o stavu služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="6c25d-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="6c25d-163">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-163">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="6c25d-164">Poskytuje metody pro upozornění hostitele o blokování a odblokování vláken pomocí služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="6c25d-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="6c25d-165">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-165">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 <span data-ttu-id="6c25d-166">Poskytuje metody pro získání informací o systému uvolňování paměti kolekce a pro řízení některé aspekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6c25d-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="6c25d-167">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-167">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 <span data-ttu-id="6c25d-168">Poskytuje [setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodu, která umožňuje hostiteli nastavte velikost segmentu kolekce uvolnění paměti a maximální velikost systému uvolňování paměti kolekce generace nula na hodnoty vyšší než `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="6c25d-168">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="6c25d-169">IGCHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-169">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 <span data-ttu-id="6c25d-170">Poskytuje metodu, která umožňuje uvolňování paměti požádat o hostiteli, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="6c25d-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="6c25d-171">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-171">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 <span data-ttu-id="6c25d-172">Poskytuje metody pro účast při plánování vláken, která by se jinak zablokovaly pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="6c25d-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="6c25d-173">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-173">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 <span data-ttu-id="6c25d-174">Poskytuje metody, které umožní hostitele zadat sadu sestavení, které se mají načíst modul CLR nebo hostitele.</span><span class="sxs-lookup"><span data-stu-id="6c25d-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="6c25d-175">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-175">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 <span data-ttu-id="6c25d-176">Poskytuje metody, které umožní hostitele k načtení sestavení a modulů nezávisle na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6c25d-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="6c25d-177">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-177">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 <span data-ttu-id="6c25d-178">Poskytuje reprezentaci událost automatickým vynulováním implementovaná tímto hostitelem.</span><span class="sxs-lookup"><span data-stu-id="6c25d-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="6c25d-179">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-179">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 <span data-ttu-id="6c25d-180">Poskytuje metody pro konfiguraci načítání sestavení a k určení, kterou rozhraní hostitel podporuje.</span><span class="sxs-lookup"><span data-stu-id="6c25d-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="6c25d-181">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-181">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 <span data-ttu-id="6c25d-182">Slouží jako hostitele reprezentace kritický oddíl pro dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="6c25d-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="6c25d-183">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-183">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 <span data-ttu-id="6c25d-184">Poskytuje metody, které upozornil hostitele události v mechanismu kolekce uvolnění paměti implementován modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="6c25d-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="6c25d-185">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-185">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="6c25d-186">Poskytuje metody, které umožní modulu CLR pro interakci s poskytované hostitelem portů dokončení vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="6c25d-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="6c25d-187">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-187">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 <span data-ttu-id="6c25d-188">Poskytuje metody pro modul CLR pro žádosti o jemně odstupňovaných přidělení haldy přes hostitele.</span><span class="sxs-lookup"><span data-stu-id="6c25d-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="6c25d-189">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-189">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 <span data-ttu-id="6c25d-190">Poskytuje implementaci hostitele reprezentace Ruční vynulování události.</span><span class="sxs-lookup"><span data-stu-id="6c25d-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="6c25d-191">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-191">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 <span data-ttu-id="6c25d-192">Poskytuje metody pro modul CLR k podání žádostí o virtuální paměti prostřednictvím hostitele, namísto použití standardních funkcí virtuální paměti systému Win32.</span><span class="sxs-lookup"><span data-stu-id="6c25d-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="6c25d-193">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-193">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 <span data-ttu-id="6c25d-194">Poskytuje metody, které upozornění na hostiteli akce, které modul CLR provede v případě klíčových přeruší, vypršení časového limitu nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="6c25d-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="6c25d-195">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-195">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 <span data-ttu-id="6c25d-196">Umožňuje udržovat informace kontextu zabezpečení implementované hostitele modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6c25d-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="6c25d-197">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-197">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 <span data-ttu-id="6c25d-198">Poskytuje metody, které umožňují přístup a kontrolu nad kontextu zabezpečení aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="6c25d-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="6c25d-199">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-199">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 <span data-ttu-id="6c25d-200">Poskytuje reprezentaci semafor implementovaná tímto hostitelem.</span><span class="sxs-lookup"><span data-stu-id="6c25d-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="6c25d-201">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-201">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <span data-ttu-id="6c25d-202">Poskytuje metody pro modul CLR k vytvoření synchronizací primitiv voláním hostitele, namísto použití funkce synchronizace Win32.</span><span class="sxs-lookup"><span data-stu-id="6c25d-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="6c25d-203">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-203">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 <span data-ttu-id="6c25d-204">Poskytuje metody, které umožní modulu CLR pro komunikaci s hostitelem ke správě úloh.</span><span class="sxs-lookup"><span data-stu-id="6c25d-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="6c25d-205">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-205">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 <span data-ttu-id="6c25d-206">Poskytuje metody, které umožní modulu CLR pro práci s úkoly prostřednictvím hostitele namísto použití funkce dělení na vlákna nebo vlákénka standardním operačním systému.</span><span class="sxs-lookup"><span data-stu-id="6c25d-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="6c25d-207">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-207">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="6c25d-208">Poskytuje metody pro CLR ke konfiguraci fondu vláken a zařadit do fronty pracovních položek s fondem vláken.</span><span class="sxs-lookup"><span data-stu-id="6c25d-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="6c25d-209">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-209">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 <span data-ttu-id="6c25d-210">Poskytuje metody pro řízení spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="6c25d-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="6c25d-211">Iobjecthandle "–"</span><span class="sxs-lookup"><span data-stu-id="6c25d-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="6c25d-212">Poskytuje metodu pro rozbalení objekty zařazování podle hodnot z dereference.</span><span class="sxs-lookup"><span data-stu-id="6c25d-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="6c25d-213">ITypeName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-213">ITypeName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 <span data-ttu-id="6c25d-214">Poskytuje metody pro získání informací o název typu.</span><span class="sxs-lookup"><span data-stu-id="6c25d-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="6c25d-215">(Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="6c25d-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6c25d-216">ITypeNameBuilder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-216">ITypeNameBuilder Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 <span data-ttu-id="6c25d-217">Poskytuje metody pro vytvoření názvu typu.</span><span class="sxs-lookup"><span data-stu-id="6c25d-217">Provides methods for building a type name.</span></span> <span data-ttu-id="6c25d-218">(Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="6c25d-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6c25d-219">ITypeNameFactory – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c25d-219">ITypeNameFactory Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 <span data-ttu-id="6c25d-220">Poskytuje metody pro dekonstrukce název typu.</span><span class="sxs-lookup"><span data-stu-id="6c25d-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="6c25d-221">(Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.)</span><span class="sxs-lookup"><span data-stu-id="6c25d-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="6c25d-222">IValidator "–"</span><span class="sxs-lookup"><span data-stu-id="6c25d-222">"IValidator"</span></span>  
 <span data-ttu-id="6c25d-223">Poskytuje metody pro ověřování přenosné spustitelné (PE) bitové kopie a oznamování chyb ověřování.</span><span class="sxs-lookup"><span data-stu-id="6c25d-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6c25d-224">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6c25d-224">Related Sections</span></span>  
 [<span data-ttu-id="6c25d-225">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6c25d-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="6c25d-226">Obsahuje témata, která popisují rozhraní hostování zadaný v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="6c25d-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="6c25d-227">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="6c25d-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="6c25d-228">Obsahuje témata, která popisují rozhraní hostování zadaný v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6c25d-228">Contains topics that describe the hosting interfaces provided in the .NET Framework 4.</span></span>
