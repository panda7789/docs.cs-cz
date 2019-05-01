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
ms.openlocfilehash: 05ff93f9dc7e875c9f84dd6d8d1f4be9b4f12653
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043508"
---
# <a name="startupflags-enumeration"></a><span data-ttu-id="fed2f-102">STARTUP_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="fed2f-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="fed2f-103">Obsahuje hodnoty, které označují chování při spouštění modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fed2f-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="fed2f-104">Uvolňování paměti je standardně nesouběžné a pouze v knihovně základních tříd je načtena do doménově neutrální oblasti.</span><span class="sxs-lookup"><span data-stu-id="fed2f-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fed2f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fed2f-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fed2f-106">Členové</span><span class="sxs-lookup"><span data-stu-id="fed2f-106">Members</span></span>  
  
|<span data-ttu-id="fed2f-107">Člen</span><span class="sxs-lookup"><span data-stu-id="fed2f-107">Member</span></span>|<span data-ttu-id="fed2f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="fed2f-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="fed2f-109">Určuje, že má být použito souběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="fed2f-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="fed2f-110">Pokud volající požaduje sestavení serveru a souběžné uvolňování paměti na počítači s jedním procesorem, sestavení pracovní stanice a nesouběžné uvolnění místo toho spuštěno.</span><span class="sxs-lookup"><span data-stu-id="fed2f-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="fed2f-111">**Poznámka:**  Souběžné uvolňování paměti se nepodporuje v aplikacích, které jsou spuštěny modulu WOW64 x86 emulátor v 64bitových systémech, které implementují Intel Itanium architekturu (dříve označovanou jako IA-64).</span><span class="sxs-lookup"><span data-stu-id="fed2f-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="fed2f-112">Další informace o použití modulu WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).</span><span class="sxs-lookup"><span data-stu-id="fed2f-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="fed2f-113">Určuje, že optimalizační zavaděč se vyskytují.</span><span class="sxs-lookup"><span data-stu-id="fed2f-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="fed2f-114">Určuje, že žádná sestavení nejsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="fed2f-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="fed2f-115">Určuje, že všechna sestavení jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="fed2f-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="fed2f-116">Určuje, že všechna sestavení se silným názvem jsou načtena jako doménově neutrální.</span><span class="sxs-lookup"><span data-stu-id="fed2f-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="fed2f-117">Určí, že zásada verze CLR nebude použita na předanou verzi.</span><span class="sxs-lookup"><span data-stu-id="fed2f-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="fed2f-118">Přesnou verzi zadanou modulu CLR bude načtena.</span><span class="sxs-lookup"><span data-stu-id="fed2f-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="fed2f-119">Překrytí nevyhodnocuje zásadu, aby určilo nejnovější kompatibilní verzi.</span><span class="sxs-lookup"><span data-stu-id="fed2f-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="fed2f-120">Určuje, že upřednostňovaný modul runtime bude možné nastavit, ale ne spuštěn.</span><span class="sxs-lookup"><span data-stu-id="fed2f-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="fed2f-121">Určuje, že se použije uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="fed2f-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="fed2f-122">Určuje, že uvolňování paměti zachová virtuální adresu použitou.</span><span class="sxs-lookup"><span data-stu-id="fed2f-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="fed2f-123">Určuje, že míchání hostitelského rozhraní nebude povoleno.</span><span class="sxs-lookup"><span data-stu-id="fed2f-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="fed2f-124">Určuje, že by neměla zosobnění téct přes asynchronní body ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="fed2f-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="fed2f-125">Určuje, že zásobníku úplného vlákna by neměl být potvrzen při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="fed2f-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="fed2f-126">Určuje, že spravovaná zosobnění a zosobnění dosažená prostřednictvím platformy vyvolat budou téct přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="fed2f-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="fed2f-127">Ve výchozím nastavení budou pouze spravovaná zosobnění téct přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="fed2f-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="fed2f-128">Určuje, že uvolňování paměti bude používat méně potvrzeného místa při nedostatku systémové paměti.</span><span class="sxs-lookup"><span data-stu-id="fed2f-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="fed2f-129">Zobrazit `gcTrimCommitOnLowMemory` v [optimalizace pro sdílené hostování webů](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span><span class="sxs-lookup"><span data-stu-id="fed2f-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="fed2f-130">Určuje, že je povoleno trasování událostí pro Windows (ETW) pro common language runtime události.</span><span class="sxs-lookup"><span data-stu-id="fed2f-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="fed2f-131">Od verze Windows Vista, je povoleno sledování událostí vždy, takže tento příznak nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="fed2f-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="fed2f-132">Zobrazit [řízení přihlašování rozhraní .NET Framework](../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="fed2f-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="fed2f-133">Určuje, zda je povoleno sledování prostředků domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fed2f-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="fed2f-134">Zobrazit <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> vlastnost a [ \<appdomainresourcemonitoring – > Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span><span class="sxs-lookup"><span data-stu-id="fed2f-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fed2f-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fed2f-135">Requirements</span></span>  
 <span data-ttu-id="fed2f-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fed2f-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fed2f-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fed2f-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fed2f-138">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fed2f-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fed2f-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fed2f-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed2f-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fed2f-140">See also</span></span>

- [<span data-ttu-id="fed2f-141">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="fed2f-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
