---
title: STARTUP_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f39608b39be7d5c25b916fb20877aa73d6e5a8bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916223"
---
# <a name="startup_flags-enumeration"></a><span data-ttu-id="cb631-102">STARTUP_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="cb631-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="cb631-103">Obsahuje hodnoty, které označují chování při spuštění modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="cb631-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="cb631-104">Ve výchozím nastavení je uvolňování paměti nesouběžné a pouze základní knihovna tříd je načtena do doménové neutrální oblasti.</span><span class="sxs-lookup"><span data-stu-id="cb631-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb631-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb631-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="cb631-106">Členové</span><span class="sxs-lookup"><span data-stu-id="cb631-106">Members</span></span>  
  
|<span data-ttu-id="cb631-107">Člen</span><span class="sxs-lookup"><span data-stu-id="cb631-107">Member</span></span>|<span data-ttu-id="cb631-108">Popis</span><span class="sxs-lookup"><span data-stu-id="cb631-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="cb631-109">Určuje, že by mělo být použito souběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="cb631-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="cb631-110">Pokud volající požaduje pro sestavení serveru a souběžné uvolňování paměti v počítači s jedním procesorem, spustí se místo toho sestavení pracovní stanice a nesouběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="cb631-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="cb631-111">**Poznámka:**  Souběžné uvolňování paměti není podporováno v aplikacích, které spouštějí emulátor WOW64 x86 v 64 systémech, které implementují architekturu Intel Itanium (dříve nazývané IA-64).</span><span class="sxs-lookup"><span data-stu-id="cb631-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="cb631-112">Další informace o používání WOW64 v systémech s 64 Windows najdete v tématu [spouštění 32 aplikací](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="cb631-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="cb631-113">Určuje, že se má vyskytnout optimalizace zavaděče.</span><span class="sxs-lookup"><span data-stu-id="cb631-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="cb631-114">Určuje, že žádná sestavení nejsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="cb631-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="cb631-115">Určuje, že všechna sestavení jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="cb631-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="cb631-116">Určuje, že všechna sestavení se silným názvem jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="cb631-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="cb631-117">Určuje, že zásady verze CLR nebudou aplikovány na předanou verzi.</span><span class="sxs-lookup"><span data-stu-id="cb631-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="cb631-118">Bude načtena přesná verze, která je určena pro modul CLR.</span><span class="sxs-lookup"><span data-stu-id="cb631-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="cb631-119">Překrytí nevyhodnotí zásadu, aby určila nejnovější kompatibilní verzi.</span><span class="sxs-lookup"><span data-stu-id="cb631-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="cb631-120">Určuje, že preferovaný modul runtime bude nastaven, ale ne skutečně spuštěný.</span><span class="sxs-lookup"><span data-stu-id="cb631-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="cb631-121">Určuje, že bude použito uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="cb631-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="cb631-122">Určuje, že uvolňování paměti bude uchovávat virtuální adresu použitou.</span><span class="sxs-lookup"><span data-stu-id="cb631-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="cb631-123">Určuje, že se nepovoluje kombinování hostitelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cb631-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="cb631-124">Určuje, že při výchozím nastavení by zosobnění nemělo v rámci asynchronních bodů přesměrovat.</span><span class="sxs-lookup"><span data-stu-id="cb631-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="cb631-125">Určuje, že plný zásobník vláken by neměl být potvrzen při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="cb631-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="cb631-126">Určuje, že spravované zosobnění a zosobnění dosažené prostřednictvím vyvolání platformy budou procházet mezi asynchronními body.</span><span class="sxs-lookup"><span data-stu-id="cb631-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="cb631-127">Ve výchozím nastavení budou v rámci asynchronních bodů zaplněny pouze spravované zosobnění.</span><span class="sxs-lookup"><span data-stu-id="cb631-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="cb631-128">Určuje, že uvolňování paměti bude používat méně potvrzené místo v případě nízké systémové paměti.</span><span class="sxs-lookup"><span data-stu-id="cb631-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="cb631-129">Nahlédněte do části `gcTrimCommitOnLowMemory` [optimalizace pro sdílené webové hostování](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="cb631-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="cb631-130">Určuje, že pro události modulu CLR (Common Language Runtime) je povoleno trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="cb631-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="cb631-131">Počínaje systémem Windows Vista je trasování událostí vždy povoleno, takže tento příznak nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="cb631-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="cb631-132">Viz [řízení protokolování .NET Framework](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="cb631-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="cb631-133">Určuje, zda je povoleno monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="cb631-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="cb631-134">Podívejte se <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> na vlastnost a [ \<> element appDomainResourceMonitoring](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="cb631-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb631-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb631-135">Requirements</span></span>  
 <span data-ttu-id="cb631-136">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb631-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb631-137">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cb631-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb631-138">**Knihovna** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb631-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb631-139">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb631-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb631-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb631-140">See also</span></span>

- [<span data-ttu-id="cb631-141">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="cb631-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
