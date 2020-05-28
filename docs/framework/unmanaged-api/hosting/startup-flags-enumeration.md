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
ms.openlocfilehash: b4694efffa0a3dd6fed1f97fc2359c5eb335d440
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006412"
---
# <a name="startup_flags-enumeration"></a><span data-ttu-id="8e5ea-102">STARTUP_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="8e5ea-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="8e5ea-103">Obsahuje hodnoty, které označují chování při spuštění modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="8e5ea-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="8e5ea-104">Ve výchozím nastavení je uvolňování paměti nesouběžné a pouze základní knihovna tříd je načtena do doménové neutrální oblasti.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e5ea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e5ea-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8e5ea-106">Členové</span><span class="sxs-lookup"><span data-stu-id="8e5ea-106">Members</span></span>  
  
|<span data-ttu-id="8e5ea-107">Člen</span><span class="sxs-lookup"><span data-stu-id="8e5ea-107">Member</span></span>|<span data-ttu-id="8e5ea-108">Description</span><span class="sxs-lookup"><span data-stu-id="8e5ea-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="8e5ea-109">Určuje, že by mělo být použito souběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="8e5ea-110">Pokud volající požaduje pro sestavení serveru a souběžné uvolňování paměti v počítači s jedním procesorem, spustí se místo toho sestavení pracovní stanice a nesouběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="8e5ea-111">**Poznámka:**  Souběžné uvolňování paměti není podporováno v aplikacích, které spouštějí emulátor WOW64 x86 v 64 systémech, které implementují architekturu Intel Itanium (dříve nazývané IA-64).</span><span class="sxs-lookup"><span data-stu-id="8e5ea-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="8e5ea-112">Další informace o používání WOW64 v systémech s 64 Windows najdete v tématu [spouštění 32 aplikací](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="8e5ea-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="8e5ea-113">Určuje, že se má vyskytnout optimalizace zavaděče.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="8e5ea-114">Určuje, že žádná sestavení nejsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="8e5ea-115">Určuje, že všechna sestavení jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="8e5ea-116">Určuje, že všechna sestavení se silným názvem jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="8e5ea-117">Určuje, že zásady verze CLR nebudou aplikovány na předanou verzi.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="8e5ea-118">Bude načtena přesná verze, která je určena pro modul CLR.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="8e5ea-119">Překrytí nevyhodnotí zásadu, aby určila nejnovější kompatibilní verzi.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="8e5ea-120">Určuje, že preferovaný modul runtime bude nastaven, ale ne skutečně spuštěný.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="8e5ea-121">Určuje, že bude použito uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="8e5ea-122">Určuje, že uvolňování paměti bude uchovávat virtuální adresu použitou.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="8e5ea-123">Určuje, že se nepovoluje kombinování hostitelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="8e5ea-124">Určuje, že při výchozím nastavení by zosobnění nemělo v rámci asynchronních bodů přesměrovat.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="8e5ea-125">Určuje, že plný zásobník vláken by neměl být potvrzen při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="8e5ea-126">Určuje, že spravované zosobnění a zosobnění dosažené prostřednictvím vyvolání platformy budou procházet mezi asynchronními body.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="8e5ea-127">Ve výchozím nastavení budou v rámci asynchronních bodů zaplněny pouze spravované zosobnění.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="8e5ea-128">Určuje, že uvolňování paměti bude používat méně potvrzené místo v případě nízké systémové paměti.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="8e5ea-129">Nahlédněte `gcTrimCommitOnLowMemory` do části [optimalizace pro sdílené webové hostování](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="8e5ea-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="8e5ea-130">Určuje, že pro události modulu CLR (Common Language Runtime) je povoleno trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="8e5ea-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="8e5ea-131">Počínaje systémem Windows Vista je trasování událostí vždy povoleno, takže tento příznak nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="8e5ea-132">Viz [řízení protokolování .NET Framework](../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="8e5ea-132">See [Controlling .NET Framework Logging](../../performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="8e5ea-133">Určuje, zda je povoleno monitorování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8e5ea-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="8e5ea-134">Podívejte se na <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> vlastnost a [ \<appDomainResourceMonitoring> element](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="8e5ea-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e5ea-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e5ea-135">Requirements</span></span>  
 <span data-ttu-id="8e5ea-136">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e5ea-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e5ea-137">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8e5ea-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e5ea-138">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8e5ea-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e5ea-139">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e5ea-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5ea-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e5ea-140">See also</span></span>

- [<span data-ttu-id="8e5ea-141">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="8e5ea-141">Hosting Enumerations</span></span>](hosting-enumerations.md)
