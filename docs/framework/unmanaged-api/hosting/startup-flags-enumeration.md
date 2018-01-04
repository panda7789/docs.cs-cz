---
title: "STARTUP_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: STARTUP_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: STARTUP_FLAGS
helpviewer_keywords: STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca2db0cd7082a596999f1d74c9092264a65692ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="startupflags-enumeration"></a><span data-ttu-id="439f0-102">STARTUP_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="439f0-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="439f0-103">Obsahuje hodnoty, které označují chování při spouštění modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="439f0-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="439f0-104">Ve výchozím nastavení, uvolňování paměti je nesouběžného a to pouze v knihovně základní třída je načten do oblasti domény jazykově neutrální.</span><span class="sxs-lookup"><span data-stu-id="439f0-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="439f0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="439f0-105">Syntax</span></span>  
  
```  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="439f0-106">Členové</span><span class="sxs-lookup"><span data-stu-id="439f0-106">Members</span></span>  
  
|<span data-ttu-id="439f0-107">Člen</span><span class="sxs-lookup"><span data-stu-id="439f0-107">Member</span></span>|<span data-ttu-id="439f0-108">Popis</span><span class="sxs-lookup"><span data-stu-id="439f0-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="439f0-109">Určuje, že má být použita souběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="439f0-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="439f0-110">Volající požaduje serveru sestavení a souběžné uvolňování paměti na počítač s jedním procesorem, jsou sestavení pracovní stanice a nesouběžného uvolňování paměti Spusťte místo toho.</span><span class="sxs-lookup"><span data-stu-id="439f0-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="439f0-111">**Poznámka:** souběžné uvolňování není podporována v aplikacích, které jsou spuštěny WOW64 x86 emulátoru na 64bitových systémech, které implementují architektuře Intel Itanium (dříve se označovaly jako platformu IA-64).</span><span class="sxs-lookup"><span data-stu-id="439f0-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="439f0-112">Další informace o používání WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitové aplikace](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span><span class="sxs-lookup"><span data-stu-id="439f0-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="439f0-113">Určuje, že zavaděč optimalizace se probíhat.</span><span class="sxs-lookup"><span data-stu-id="439f0-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="439f0-114">Určuje, že žádné sestavení jsou načteny jako domény jazykově neutrální.</span><span class="sxs-lookup"><span data-stu-id="439f0-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="439f0-115">Určuje, že jsou všechna sestavení načíst jako domény jazykově neutrální.</span><span class="sxs-lookup"><span data-stu-id="439f0-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="439f0-116">Určuje, zda jsou načteny všechny sestavení se silným názvem, jako domény jazykově neutrální.</span><span class="sxs-lookup"><span data-stu-id="439f0-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="439f0-117">Určí, že zásady verze CLR nebude použita na verzi předaná.</span><span class="sxs-lookup"><span data-stu-id="439f0-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="439f0-118">Přesné verze zadaná CLR budou načteny.</span><span class="sxs-lookup"><span data-stu-id="439f0-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="439f0-119">Shim nevyhodnocuje zásady, které určují nejnovější kompatibilní verzi.</span><span class="sxs-lookup"><span data-stu-id="439f0-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="439f0-120">Určuje, že upřednostňované runtime budou nastavení, ale ve skutečnosti není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="439f0-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="439f0-121">Určuje, že se použije uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="439f0-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="439f0-122">Určuje, že uvolňování uchová virtuální adresu použitou.</span><span class="sxs-lookup"><span data-stu-id="439f0-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="439f0-123">Určuje, že kombinování hostingu rozhraní nebudou povolena.</span><span class="sxs-lookup"><span data-stu-id="439f0-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="439f0-124">Určuje, že by neměl zosobnění toku přes asynchronní body ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="439f0-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="439f0-125">Určuje, že zásobníku úplné vlákno by neměl být potvrdit při spuštění vlákno.</span><span class="sxs-lookup"><span data-stu-id="439f0-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="439f0-126">Určuje, že spravované impersonations a impersonations dosáhnout pomocí platformy vyvolání bude procházet přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="439f0-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="439f0-127">Ve výchozím nastavení bude pouze spravované impersonations procházet přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="439f0-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="439f0-128">Určuje, že uvolňování paměti použijí méně potvrdit místa při nedostatku systémové paměti.</span><span class="sxs-lookup"><span data-stu-id="439f0-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="439f0-129">V tématu `gcTrimCommitOnLowMemory` v [optimalizace pro sdílené hostování webů](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="439f0-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="439f0-130">Určuje, zda je povoleno trasování událostí pro Windows (ETW) pro běžné události modulu runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="439f0-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="439f0-131">Počínaje Windows Vista, trasování událostí je vždy zapnutá, takže tento příznak nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="439f0-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="439f0-132">V tématu [řízení přihlašování rozhraní .NET Framework](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="439f0-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="439f0-133">Určuje, zda je povoleno sledování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="439f0-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="439f0-134">Najdete v článku <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> vlastnost a [ \<appdomainresourcemonitoring – > Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="439f0-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="439f0-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="439f0-135">Requirements</span></span>  
 <span data-ttu-id="439f0-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="439f0-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="439f0-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="439f0-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="439f0-138">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="439f0-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="439f0-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="439f0-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="439f0-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="439f0-140">See Also</span></span>  
 [<span data-ttu-id="439f0-141">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="439f0-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
