---
title: Výčet COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cbc66ef1eb5048d2c708a615a99ea363d29540f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752171"
---
# <a name="corprfhighmonitor-enumeration"></a>Výčet COR_PRF_HIGH_MONITOR
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje příznaky kromě v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který lze vybrat profiler [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Jsou nastaveny žádné příznaky.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Ovládací prvky [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání pro přidání odkazů na sestavení během procházení uzavření odkaz na sestavení CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Ovládací prvky [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) zpětného volání pro aktualizace do datového proudu symbol přidružený k modulu v paměti.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Ovládací prvky [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) zpětné volání pro určující, kdy byl dynamickou metodu uvolňování paměti shromažďují a byla uvolněna. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET core 3.0 a novějších verzích pouze: Zakáže [vrstvené kompilace](../../../core/whats-new/dotnet-core-3-0.md) pro profilovací programy.|
|`COR_PRF_HIGH_BASIC_GC`|.NET core 3.0 a novějších verzích pouze: Poskytuje zjednodušenou GC profilace možnost ve srovnání s [ `COR_PRF_MONITOR_GC` ](cor-prf-monitor-enumeration.md). Řídí pouze [garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), a [getgenerationbounds –](icorprofilerinfo2-getgenerationbounds-method.md) zpětná volání. Na rozdíl od `COR_PRF_MONITOR_GC` příznak `COR_PRF_HIGH_BASIC_GC` není zakázat souběžné uvolňování paměti.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET core 3.0 a novějších verzích pouze: Umožňuje [movedreferences –](icorprofilercallback-movedreferences-method.md) a [movedreferences2 –](icorprofilercallback4-movedreferences2-method.md) zpětná volání pro pouze komprimaci GC.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET core 3.0 a novějších verzích pouze: Podobně jako [ `COR_PRF_MONITOR_OBJECT_ALLOCATED` ](cor-prf-monitor-enumeration.md), ale poskytuje informace o přidělení objektů pro velký objekt haldy (loh) modulem GC pouze.|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které vyžadují profil vylepšené bitové kopie. Odpovídá `COR_PRF_REQUIRE_PROFILE_IMAGE` příznak v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které je možné nastavit poté, co je profiler připojen ke spuštěné aplikaci.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit pouze během inicializace. Změnit některý z těchto příznaky jinde vede `HRESULT` hodnotu, která indikuje selhání.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_HIGH_MONITOR` Příznaky se používají s `pdwEventsHigh` parametr [icorprofilerinfo5::geteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) a [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.  
  
Od verze rozhraní .NET Framework 4.6.1, hodnota `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` změněn od 0 do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). Počínaje rozhraním .NET Framework 4.7.2, její hodnota změněna z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` k `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` má být bitová maska, která představuje všechny příznaky, které lze nastavit pouze během inicializace. Změnit některý z těchto příznaky jinde výsledkem nezdařené `HRESULT`.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [COR_PRF_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
