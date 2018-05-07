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
ms.openlocfilehash: bc1d3ffc34cd74d68bf10cb677b68f0a75bb7c67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="startupflags-enumeration"></a>STARTUP_FLAGS – výčet
Obsahuje hodnoty, které označují chování při spouštění modulu common language runtime (CLR). Ve výchozím nastavení, uvolňování paměti je nesouběžného a to pouze v knihovně základní třída je načten do oblasti domény jazykově neutrální.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|Určuje, že má být použita souběžné uvolňování paměti. Volající požaduje serveru sestavení a souběžné uvolňování paměti na počítač s jedním procesorem, jsou sestavení pracovní stanice a nesouběžného uvolňování paměti Spusťte místo toho. **Poznámka:** souběžné uvolňování není podporována v aplikacích, které jsou spuštěny WOW64 x86 emulátoru na 64bitových systémech, které implementují architektuře Intel Itanium (dříve se označovaly jako platformu IA-64). Další informace o používání WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitové aplikace](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Určuje, že zavaděč optimalizace se probíhat.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Určuje, že žádné sestavení jsou načteny jako domény jazykově neutrální.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Určuje, že jsou všechna sestavení načíst jako domény jazykově neutrální.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Určuje, zda jsou načteny všechny sestavení se silným názvem, jako domény jazykově neutrální.|  
|`STARTUP_LOADER_SAFEMODE`|Určí, že zásady verze CLR nebude použita na verzi předaná. Přesné verze zadaná CLR budou načteny. Shim nevyhodnocuje zásady, které určují nejnovější kompatibilní verzi.|  
|`STARTUP_LOADER_SETPREFERENCE`|Určuje, že upřednostňované runtime budou nastavení, ale ve skutečnosti není spuštěna.|  
|`STARTUP_SERVER_GC`|Určuje, že se použije uvolňování paměti serveru.|  
|`STARTUP_HOARD_GC_VM`|Určuje, že uvolňování uchová virtuální adresu použitou.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Určuje, že kombinování hostingu rozhraní nebudou povolena.|  
|`STARTUP_LEGACY_IMPERSONATION`|Určuje, že by neměl zosobnění toku přes asynchronní body ve výchozím nastavení.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Určuje, že zásobníku úplné vlákno by neměl být potvrdit při spuštění vlákno.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Určuje, že spravované impersonations a impersonations dosáhnout pomocí platformy vyvolání bude procházet přes asynchronní body. Ve výchozím nastavení bude pouze spravované impersonations procházet přes asynchronní body.|  
|`STARTUP_TRIM_GC_COMMIT`|Určuje, že uvolňování paměti použijí méně potvrdit místa při nedostatku systémové paměti. V tématu `gcTrimCommitOnLowMemory` v [optimalizace pro sdílené hostování webů](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Určuje, zda je povoleno trasování událostí pro Windows (ETW) pro běžné události modulu runtime jazyka. Počínaje Windows Vista, trasování událostí je vždy zapnutá, takže tento příznak nemá žádný vliv. V tématu [řízení přihlašování rozhraní .NET Framework](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Určuje, zda je povoleno sledování prostředků domény aplikace. Najdete v článku <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> vlastnost a [ \<appdomainresourcemonitoring – > Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
