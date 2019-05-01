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
# <a name="startupflags-enumeration"></a>STARTUP_FLAGS – výčet
Obsahuje hodnoty, které označují chování při spouštění modulu common language runtime (CLR). Uvolňování paměti je standardně nesouběžné a pouze v knihovně základních tříd je načtena do doménově neutrální oblasti.  
  
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
|`STARTUP_CONCURRENT_GC`|Určuje, že má být použito souběžné uvolňování paměti. Pokud volající požaduje sestavení serveru a souběžné uvolňování paměti na počítači s jedním procesorem, sestavení pracovní stanice a nesouběžné uvolnění místo toho spuštěno. **Poznámka:**  Souběžné uvolňování paměti se nepodporuje v aplikacích, které jsou spuštěny modulu WOW64 x86 emulátor v 64bitových systémech, které implementují Intel Itanium architekturu (dříve označovanou jako IA-64). Další informace o použití modulu WOW64 v 64bitových systémech Windows najdete v tématu [spuštění 32bitových aplikací](/windows/desktop/WinProg64/running-32-bit-applications).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Určuje, že optimalizační zavaděč se vyskytují.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Určuje, že žádná sestavení nejsou načtena jako doménově neutrální.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Určuje, že všechna sestavení jsou načtena jako doménově neutrální.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Určuje, že všechna sestavení se silným názvem jsou načtena jako doménově neutrální.|  
|`STARTUP_LOADER_SAFEMODE`|Určí, že zásada verze CLR nebude použita na předanou verzi. Přesnou verzi zadanou modulu CLR bude načtena. Překrytí nevyhodnocuje zásadu, aby určilo nejnovější kompatibilní verzi.|  
|`STARTUP_LOADER_SETPREFERENCE`|Určuje, že upřednostňovaný modul runtime bude možné nastavit, ale ne spuštěn.|  
|`STARTUP_SERVER_GC`|Určuje, že se použije uvolnění paměti serveru.|  
|`STARTUP_HOARD_GC_VM`|Určuje, že uvolňování paměti zachová virtuální adresu použitou.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Určuje, že míchání hostitelského rozhraní nebude povoleno.|  
|`STARTUP_LEGACY_IMPERSONATION`|Určuje, že by neměla zosobnění téct přes asynchronní body ve výchozím nastavení.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Určuje, že zásobníku úplného vlákna by neměl být potvrzen při spuštění vlákna.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Určuje, že spravovaná zosobnění a zosobnění dosažená prostřednictvím platformy vyvolat budou téct přes asynchronní body. Ve výchozím nastavení budou pouze spravovaná zosobnění téct přes asynchronní body.|  
|`STARTUP_TRIM_GC_COMMIT`|Určuje, že uvolňování paměti bude používat méně potvrzeného místa při nedostatku systémové paměti. Zobrazit `gcTrimCommitOnLowMemory` v [optimalizace pro sdílené hostování webů](../../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Určuje, že je povoleno trasování událostí pro Windows (ETW) pro common language runtime události. Od verze Windows Vista, je povoleno sledování událostí vždy, takže tento příznak nemá žádný vliv. Zobrazit [řízení přihlašování rozhraní .NET Framework](../../../../docs/framework/performance/controlling-logging.md).|  
|`STARTUP_ARM`|Určuje, zda je povoleno sledování prostředků domény aplikace. Zobrazit <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> vlastnost a [ \<appdomainresourcemonitoring – > Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
