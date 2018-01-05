---
title: "Rozhraní hostování CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fd954419f46313a239ddf5a309a646e3d2f1b9bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clr-hosting-interfaces"></a><span data-ttu-id="6be5b-102">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6be5b-102">CLR Hosting Interfaces</span></span>
<span data-ttu-id="6be5b-103">Tato část popisuje rozhraní, která nespravované hostitelů můžete integrovat common language runtime (CLR) do svých aplikací.</span><span class="sxs-lookup"><span data-stu-id="6be5b-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span> <span data-ttu-id="6be5b-104">Informace se vztahují na rozhraní .NET Framework verze 2.0 a novější verze.</span><span class="sxs-lookup"><span data-stu-id="6be5b-104">The information pertains to the .NET Framework version 2.0 and later versions.</span></span> <span data-ttu-id="6be5b-105">Tato rozhraní povolte hostitele k řízení další aspekty modul runtime, než bylo možné v verze 1.0 a 1.1 a zadejte mnohem náročnější integrace modulu CLR a model spouštění hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-105">These interfaces enable the host to control many more aspects of the runtime than was possible in versions 1.0 and 1.1, and provide much tighter integration between the CLR and the host's execution model.</span></span>  
  
 <span data-ttu-id="6be5b-106">V rozhraní .NET Framework verze 1.0 a 1.1 model hostování povoleno nespravované hostitele k načtení modulu CLR do procesu, nakonfigurovat některá nastavení a k přijímání oznámení událostí.</span><span class="sxs-lookup"><span data-stu-id="6be5b-106">In the .NET Framework version 1.0 and 1.1, the hosting model enabled an unmanaged host to load the CLR into a process, to configure certain settings, and to receive event notifications.</span></span> <span data-ttu-id="6be5b-107">Ale obecně platí, hostitele a modulu CLR byla spuštěna nezávisle v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="6be5b-107">However, in general, the host and the CLR ran independently in that process.</span></span> <span data-ttu-id="6be5b-108">V rozhraní .NET Framework verze 2.0 a novějších verzích nechte nové vrstvy abstrakce hostitele zadejte mnoho prostředků aktuálně poskytuje typy v sestavení Win32 a rozšířit sadu funkcí, které můžete nakonfigurovat hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-108">In the .NET Framework version 2.0 and later versions, new layers of abstraction let the host provide many of the resources currently provided by the types in the Win32 assembly, and extend the set of capabilities that the host can configure.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6be5b-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6be5b-109">In This Section</span></span>  
 [<span data-ttu-id="6be5b-110">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-110">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 <span data-ttu-id="6be5b-111">Poskytne metodu, která provede zpětné volání pro registrované událost.</span><span class="sxs-lookup"><span data-stu-id="6be5b-111">Provides a method that performs a callback for a registered event.</span></span>  
  
 [<span data-ttu-id="6be5b-112">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-112">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 <span data-ttu-id="6be5b-113">Poskytuje metody pro provádění zpětných volání v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="6be5b-113">Provides methods for making callbacks within an apartment.</span></span>  
  
 [<span data-ttu-id="6be5b-114">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-114">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 <span data-ttu-id="6be5b-115">Poskytuje metody pro konfiguraci nastavení spuštění.</span><span class="sxs-lookup"><span data-stu-id="6be5b-115">Provides methods for setting run-time configuration.</span></span>  
  
 [<span data-ttu-id="6be5b-116">ICatalogServices – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-116">ICatalogServices Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 <span data-ttu-id="6be5b-117">Poskytuje metody pro vytváření katalogu služeb.</span><span class="sxs-lookup"><span data-stu-id="6be5b-117">Provides methods for cataloging services.</span></span> <span data-ttu-id="6be5b-118">(Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)</span><span class="sxs-lookup"><span data-stu-id="6be5b-118">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6be5b-119">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-119">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 <span data-ttu-id="6be5b-120">Poskytuje metody, které podporují komunikaci mezi hostitelem a CLR o sestavení.</span><span class="sxs-lookup"><span data-stu-id="6be5b-120">Provides methods that support communication between the host and the CLR about assemblies.</span></span>  
  
 [<span data-ttu-id="6be5b-121">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 <span data-ttu-id="6be5b-122">Spravuje seznam sestavení, která jsou načtena modulu CLR a ne hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-122">Manages a list of assemblies that are loaded by the CLR and not by the host.</span></span>  
  
 [<span data-ttu-id="6be5b-123">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-123">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 <span data-ttu-id="6be5b-124">Poskytuje metody pro hostitele k získání přístupu k a nakonfigurovat různé aspekty modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6be5b-124">Provides methods for the host to gain access to, and configure various aspects of, the CLR.</span></span>  
  
 [<span data-ttu-id="6be5b-125">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 <span data-ttu-id="6be5b-126">Poskytuje metody, které umožní hostitele k sadu úloh přidružit identifikátor a popisný název.</span><span class="sxs-lookup"><span data-stu-id="6be5b-126">Provides methods that enable a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
 [<span data-ttu-id="6be5b-127">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-127">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 <span data-ttu-id="6be5b-128">Poskytuje metody, které umožní hostiteli nakonfigurovat vlastní haldy výpisy pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="6be5b-128">Provides methods that enable the host to configure custom heap dumps for error reporting.</span></span>  
  
 [<span data-ttu-id="6be5b-129">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-129">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 <span data-ttu-id="6be5b-130">Poskytuje metody, které umožní hostitele k interakci s systém kolekce paměti modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6be5b-130">Provides methods that enable a host to interact with the CLR's garbage collection system.</span></span>  
  
 [<span data-ttu-id="6be5b-131">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-131">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 <span data-ttu-id="6be5b-132">Poskytuje metody pro hostitele k vyhodnocení a komunikaci změny v informace o zásadách pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="6be5b-132">Provides methods for the host to evaluate and communicate changes in policy information for assemblies.</span></span>  
  
 [<span data-ttu-id="6be5b-133">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-133">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 <span data-ttu-id="6be5b-134">Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole ve spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="6be5b-134">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
 [<span data-ttu-id="6be5b-135">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-135">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 <span data-ttu-id="6be5b-136">Implementuje metody zpětného volání, která umožňuje hostiteli oznámit CLR stavu zadaný vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="6be5b-136">Implements a callback method that enables the host to notify the CLR of the status of specified I/O requests.</span></span>  
  
 [<span data-ttu-id="6be5b-137">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 <span data-ttu-id="6be5b-138">Umožňuje hostiteli podmínky přetížení paměti sestavy pomocí podobná Win32 přístup `CreateMemoryResourceNotification` funkce.</span><span class="sxs-lookup"><span data-stu-id="6be5b-138">Enables the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
 [<span data-ttu-id="6be5b-139">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-139">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 <span data-ttu-id="6be5b-140">Poskytuje metody, které umožní hostitele registrace a zrušení registrace zpětných volání pro události CLR.</span><span class="sxs-lookup"><span data-stu-id="6be5b-140">Provides methods that enable the host to register and unregister callbacks for CLR events.</span></span>  
  
 [<span data-ttu-id="6be5b-141">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 <span data-ttu-id="6be5b-142">Poskytuje metody, které umožní na hostiteli a poté zadejte akce zásad pro případ selhání a vypršení časových limitů.</span><span class="sxs-lookup"><span data-stu-id="6be5b-142">Provides methods that enable the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
 [<span data-ttu-id="6be5b-143">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 <span data-ttu-id="6be5b-144">Poskytuje metody, které umožňují získat zkušební identity sestavení pomocí informace identity je sestavení, která je interní modul CLR, aniž by museli vytvářet nebo pochopit tuto identitu hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-144">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the CLR, without needing to create or understand that identity.</span></span>  
  
 [<span data-ttu-id="6be5b-145">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-145">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 <span data-ttu-id="6be5b-146">Poskytuje metody, které umožní hostitele k manipulaci s sadu sestavení odkazuje souboru nebo datový proud pomocí sestavení identifikační údaje, které je interní modul CLR, aniž by museli vytvářet nebo pochopení těchto identit.</span><span class="sxs-lookup"><span data-stu-id="6be5b-146">Provides methods that enable the host to manipulate the set of assemblies referenced by a file or stream using assembly identity data that is internal to the CLR, without needing to create or understand those identities.</span></span>  
  
 [<span data-ttu-id="6be5b-147">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-147">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 <span data-ttu-id="6be5b-148">Poskytuje podobné možnosti [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), s další způsob, jak nastavit rozhraní Řízení hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-148">Provides capabilities similar to [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), with an additional method to set the host control interface.</span></span>  
  
 [<span data-ttu-id="6be5b-149">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-149">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 <span data-ttu-id="6be5b-150">Poskytuje metody pro hostitele k načtení informací o požadovaných úkolů a ke zjištění zablokování v jeho implementaci synchronizace.</span><span class="sxs-lookup"><span data-stu-id="6be5b-150">Provides methods for the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
 [<span data-ttu-id="6be5b-151">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 <span data-ttu-id="6be5b-152">Poskytuje metody, které umožní hostitele pro požadavky modulu CLR, nebo zajistit oznámení modulu CLR o související úlohy.</span><span class="sxs-lookup"><span data-stu-id="6be5b-152">Provides methods that enable the host to make requests of the CLR, or to provide notification to the CLR about the associated task.</span></span>  
  
 [<span data-ttu-id="6be5b-153">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-153">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 <span data-ttu-id="6be5b-154">Poskytuje metody, které umožní na hostiteli a požadavku explicitně modulu CLR vytvořit nový úkol, získat aktuálně spuštěné úlohy a nastavit zeměpisné language a jazykovou verzi pro úlohu.</span><span class="sxs-lookup"><span data-stu-id="6be5b-154">Provides methods that enable the host to request explicitly that the CLR create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
 [<span data-ttu-id="6be5b-155">ICLRValidator – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-155">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 <span data-ttu-id="6be5b-156">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie (PE) a vytváření sestav chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="6be5b-156">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
 [<span data-ttu-id="6be5b-157">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-157">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 <span data-ttu-id="6be5b-158">Poskytuje metody pro konfiguraci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6be5b-158">Provides methods for configuring the CLR.</span></span>  
  
 [<span data-ttu-id="6be5b-159">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-159">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 <span data-ttu-id="6be5b-160">Poskytuje metody pro přístup k fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="6be5b-160">Provides methods for accessing the thread pool.</span></span>  
  
 [<span data-ttu-id="6be5b-161">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-161">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 <span data-ttu-id="6be5b-162">Poskytuje metody pro získání informací o stavu služby ladění.</span><span class="sxs-lookup"><span data-stu-id="6be5b-162">Provides methods for obtaining information about the state of the debugging services.</span></span>  
  
 [<span data-ttu-id="6be5b-163">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-163">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 <span data-ttu-id="6be5b-164">Poskytuje metody pro upozornění hostitele o blokování a odblokování vláken ladění služby.</span><span class="sxs-lookup"><span data-stu-id="6be5b-164">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
 [<span data-ttu-id="6be5b-165">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-165">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 <span data-ttu-id="6be5b-166">Poskytuje metody pro získání informací o systém kolekce paměti a řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6be5b-166">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
 [<span data-ttu-id="6be5b-167">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-167">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 <span data-ttu-id="6be5b-168">Poskytuje [setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metoda, která umožňuje pro hostitele a nastavte velikost segmentu kolekce paměti a maximální velikost systém kolekce paměti generování nula hodnoty větší než `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="6be5b-168">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method that enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation zero to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="6be5b-169">IGCHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-169">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 <span data-ttu-id="6be5b-170">Poskytne metodu, která umožňuje uvolňování paměti požadavku na hostiteli a změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="6be5b-170">Provides a method that enables the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
 [<span data-ttu-id="6be5b-171">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-171">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 <span data-ttu-id="6be5b-172">Poskytuje metody pro účastní plánování vláken, které by jinak blokovaly pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6be5b-172">Provides methods for participating in the scheduling of threads that would otherwise be blocked for garbage collection.</span></span>  
  
 [<span data-ttu-id="6be5b-173">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-173">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 <span data-ttu-id="6be5b-174">Poskytuje metody, které umožní hostitele k určení sady sestavení, které se mají načíst modul CLR, nebo hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-174">Provides methods that enable a host to specify sets of assemblies that should be loaded by the CLR or by the host.</span></span>  
  
 [<span data-ttu-id="6be5b-175">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-175">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 <span data-ttu-id="6be5b-176">Poskytuje metody, které umožní hostitele k načtení sestavení a moduly nezávisle na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6be5b-176">Provides methods that enable a host to load assemblies and modules independently of the CLR.</span></span>  
  
 [<span data-ttu-id="6be5b-177">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-177">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 <span data-ttu-id="6be5b-178">Poskytuje reprezentaci událost automatickým vynulováním implementované hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-178">Provides a representation of an auto-reset event implemented by the host.</span></span>  
  
 [<span data-ttu-id="6be5b-179">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-179">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 <span data-ttu-id="6be5b-180">Poskytuje metody pro konfiguraci načítání sestavení a určení, kterou rozhraní hostitel podporuje.</span><span class="sxs-lookup"><span data-stu-id="6be5b-180">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
 [<span data-ttu-id="6be5b-181">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-181">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 <span data-ttu-id="6be5b-182">Slouží jako reprezentace hostitele kritické oddílu pro dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="6be5b-182">Serves as the host's representation of a critical section for threading.</span></span>  
  
 [<span data-ttu-id="6be5b-183">IHostGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-183">IHostGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 <span data-ttu-id="6be5b-184">Poskytuje metody, které hostitele události v kolekci mechanismus paměti implementované modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6be5b-184">Provides methods that notify the host of events in the garbage collection mechanism implemented by the CLR.</span></span>  
  
 [<span data-ttu-id="6be5b-185">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-185">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 <span data-ttu-id="6be5b-186">Poskytuje metody, které umožňují modulu CLR pro interakci s porty dokončení vstupně-výstupních operací od hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-186">Provides methods that enable the CLR to interact with I/O completion ports provided by the host.</span></span>  
  
 [<span data-ttu-id="6be5b-187">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-187">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 <span data-ttu-id="6be5b-188">Poskytuje metody pro CLR do požádat podrobných přidělení haldy prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-188">Provides methods for the CLR to request fine-grained allocations from the heap through the host.</span></span>  
  
 [<span data-ttu-id="6be5b-189">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-189">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 <span data-ttu-id="6be5b-190">Poskytuje implementaci hostitele reprezentace Ruční vynulování události.</span><span class="sxs-lookup"><span data-stu-id="6be5b-190">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
 [<span data-ttu-id="6be5b-191">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-191">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 <span data-ttu-id="6be5b-192">Poskytuje metody pro CLR provádět požadavky na virtuální paměti prostřednictvím hostitele, místo použití standardní funkce Win32 virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="6be5b-192">Provides methods for the CLR to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
 [<span data-ttu-id="6be5b-193">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-193">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 <span data-ttu-id="6be5b-194">Poskytuje metody, které hostitele akce, které provádí modulu CLR pro zrušení, překročení časového limitu nebo chyby.</span><span class="sxs-lookup"><span data-stu-id="6be5b-194">Provides methods that notify the host of the actions the CLR performs in case of aborts, timeouts, or failures.</span></span>  
  
 [<span data-ttu-id="6be5b-195">IHostSecurityContext – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-195">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 <span data-ttu-id="6be5b-196">Umožňuje CLR Udržovat informace kontextu zabezpečení implementované hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-196">Enables the CLR to maintain security context information implemented by the host.</span></span>  
  
 [<span data-ttu-id="6be5b-197">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-197">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 <span data-ttu-id="6be5b-198">Poskytuje metody, které umožňují přístup k a kontrolu nad kontext zabezpečení aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="6be5b-198">Provides methods that enable access to, and control over, the security context of the currently executing thread.</span></span>  
  
 [<span data-ttu-id="6be5b-199">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-199">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 <span data-ttu-id="6be5b-200">Poskytuje reprezentaci semafor implementované hostitele.</span><span class="sxs-lookup"><span data-stu-id="6be5b-200">Provides a representation of a semaphore implemented by the host.</span></span>  
  
 [<span data-ttu-id="6be5b-201">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-201">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 <span data-ttu-id="6be5b-202">Poskytuje metody pro CLR vytvořit synchronizace primitiv voláním hostitele, místo použití funkce synchronizace Win32.</span><span class="sxs-lookup"><span data-stu-id="6be5b-202">Provides methods for the CLR to create synchronization primitives by calling the host, instead of using the Win32 synchronization functions.</span></span>  
  
 [<span data-ttu-id="6be5b-203">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-203">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 <span data-ttu-id="6be5b-204">Poskytuje metody, které umožní CLR ke komunikaci s hostitelem ke správě úloh.</span><span class="sxs-lookup"><span data-stu-id="6be5b-204">Provides methods that enable the CLR to communicate with the host to manage tasks.</span></span>  
  
 [<span data-ttu-id="6be5b-205">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-205">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 <span data-ttu-id="6be5b-206">Poskytuje metody, které umožňují modulu CLR pro práci s úkoly prostřednictvím hostitele místo použití funkce dělení na vlákna nebo fiber standardní operační systém.</span><span class="sxs-lookup"><span data-stu-id="6be5b-206">Provides methods that enable the CLR to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
 [<span data-ttu-id="6be5b-207">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-207">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 <span data-ttu-id="6be5b-208">Poskytuje metody pro CLR ke konfiguraci fondu vláken a do fronty pracovních položek pro fond vláken.</span><span class="sxs-lookup"><span data-stu-id="6be5b-208">Provides methods for the CLR to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
 [<span data-ttu-id="6be5b-209">IManagedObject – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-209">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 <span data-ttu-id="6be5b-210">Poskytuje metody pro řízení spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="6be5b-210">Provides methods for controlling a managed object.</span></span>  
  
 <span data-ttu-id="6be5b-211">Iobjecthandle "–"</span><span class="sxs-lookup"><span data-stu-id="6be5b-211">"IObjectHandle"</span></span>  
 <span data-ttu-id="6be5b-212">Poskytuje metodu pro rozbalení zařazování hodnota objekty z indirection.</span><span class="sxs-lookup"><span data-stu-id="6be5b-212">Provides a method for unwrapping marshal-by-value objects from indirection.</span></span>  
  
 [<span data-ttu-id="6be5b-213">ITypeName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-213">ITypeName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 <span data-ttu-id="6be5b-214">Poskytuje metody pro získání informací o název typu.</span><span class="sxs-lookup"><span data-stu-id="6be5b-214">Provides methods for obtaining type name information.</span></span> <span data-ttu-id="6be5b-215">(Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)</span><span class="sxs-lookup"><span data-stu-id="6be5b-215">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6be5b-216">ITypeNameBuilder – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-216">ITypeNameBuilder Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 <span data-ttu-id="6be5b-217">Poskytuje metody pro vytváření název typu.</span><span class="sxs-lookup"><span data-stu-id="6be5b-217">Provides methods for building a type name.</span></span> <span data-ttu-id="6be5b-218">(Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)</span><span class="sxs-lookup"><span data-stu-id="6be5b-218">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="6be5b-219">ITypeNameFactory – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be5b-219">ITypeNameFactory Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 <span data-ttu-id="6be5b-220">Poskytuje metody pro deconstructing název typu.</span><span class="sxs-lookup"><span data-stu-id="6be5b-220">Provides methods for deconstructing a type name.</span></span> <span data-ttu-id="6be5b-221">(Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)</span><span class="sxs-lookup"><span data-stu-id="6be5b-221">(This interface supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 <span data-ttu-id="6be5b-222">IValidator "–"</span><span class="sxs-lookup"><span data-stu-id="6be5b-222">"IValidator"</span></span>  
 <span data-ttu-id="6be5b-223">Poskytuje metody pro ověřování přenosné spustitelné bitové kopie (PE) a vytváření sestav chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="6be5b-223">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6be5b-224">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6be5b-224">Related Sections</span></span>  
 [<span data-ttu-id="6be5b-225">Zastaralá rozhraní a třídy typu Coclass pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6be5b-225">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="6be5b-226">Obsahuje témata, která popisují rozhraní hostování zadaný v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="6be5b-226">Contains topics that describe the hosting interfaces provided in the .NET Framework version 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="6be5b-227">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="6be5b-227">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="6be5b-228">Obsahuje témata, která popisují rozhraní hostování součástí [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6be5b-228">Contains topics that describe the hosting interfaces provided in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>
