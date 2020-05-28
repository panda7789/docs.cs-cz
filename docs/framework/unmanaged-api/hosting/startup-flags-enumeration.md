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
# <a name="startup_flags-enumeration"></a>STARTUP_FLAGS – výčet
Obsahuje hodnoty, které označují chování při spuštění modulu CLR (Common Language Runtime). Ve výchozím nastavení je uvolňování paměti nesouběžné a pouze základní knihovna tříd je načtena do doménové neutrální oblasti.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|Určuje, že by mělo být použito souběžné uvolňování paměti. Pokud volající požaduje pro sestavení serveru a souběžné uvolňování paměti v počítači s jedním procesorem, spustí se místo toho sestavení pracovní stanice a nesouběžné uvolňování paměti. **Poznámka:**  Souběžné uvolňování paměti není podporováno v aplikacích, které spouštějí emulátor WOW64 x86 v 64 systémech, které implementují architekturu Intel Itanium (dříve nazývané IA-64). Další informace o používání WOW64 v systémech s 64 Windows najdete v tématu [spouštění 32 aplikací](/windows/desktop/WinProg64/running-32-bit-applications).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Určuje, že se má vyskytnout optimalizace zavaděče.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Určuje, že žádná sestavení nejsou načtena jako doménově neutrální.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Určuje, že všechna sestavení jsou načtena jako doménově neutrální.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Určuje, že všechna sestavení se silným názvem jsou načtena jako doménově neutrální.|  
|`STARTUP_LOADER_SAFEMODE`|Určuje, že zásady verze CLR nebudou aplikovány na předanou verzi. Bude načtena přesná verze, která je určena pro modul CLR. Překrytí nevyhodnotí zásadu, aby určila nejnovější kompatibilní verzi.|  
|`STARTUP_LOADER_SETPREFERENCE`|Určuje, že preferovaný modul runtime bude nastaven, ale ne skutečně spuštěný.|  
|`STARTUP_SERVER_GC`|Určuje, že bude použito uvolňování paměti serveru.|  
|`STARTUP_HOARD_GC_VM`|Určuje, že uvolňování paměti bude uchovávat virtuální adresu použitou.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Určuje, že se nepovoluje kombinování hostitelského rozhraní.|  
|`STARTUP_LEGACY_IMPERSONATION`|Určuje, že při výchozím nastavení by zosobnění nemělo v rámci asynchronních bodů přesměrovat.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Určuje, že plný zásobník vláken by neměl být potvrzen při spuštění vlákna.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Určuje, že spravované zosobnění a zosobnění dosažené prostřednictvím vyvolání platformy budou procházet mezi asynchronními body. Ve výchozím nastavení budou v rámci asynchronních bodů zaplněny pouze spravované zosobnění.|  
|`STARTUP_TRIM_GC_COMMIT`|Určuje, že uvolňování paměti bude používat méně potvrzené místo v případě nízké systémové paměti. Nahlédněte `gcTrimCommitOnLowMemory` do části [optimalizace pro sdílené webové hostování](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Určuje, že pro události modulu CLR (Common Language Runtime) je povoleno trasování událostí pro Windows (ETW). Počínaje systémem Windows Vista je trasování událostí vždy povoleno, takže tento příznak nemá žádný vliv. Viz [řízení protokolování .NET Framework](../../performance/controlling-logging.md).|  
|`STARTUP_ARM`|Určuje, zda je povoleno monitorování prostředků domény aplikace. Podívejte se na <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> vlastnost a [ \<appDomainResourceMonitoring> element](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty hostování](hosting-enumerations.md)
