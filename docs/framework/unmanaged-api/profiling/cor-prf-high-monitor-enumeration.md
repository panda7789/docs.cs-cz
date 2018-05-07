---
title: Výčet COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92ba2b5eac5eb1368a7d7ccf3b666886f4ca92a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="corprfhighmonitor-enumeration"></a>Výčet COR_PRF_HIGH_MONITOR
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje příznaky kromě těch, které v nalezen [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který můžete vybrat profileru [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Žádné příznaky se nastavují.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Ovládací prvky [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání pro přidání odkazů na sestavení během procházení uzavření odkaz na sestavení CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Ovládací prvky [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) zpětné volání pro aktualizace do datového proudu symbol, který je přidružený modul v paměti.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Ovládací prvky [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) zpětné volání pro označující při dynamické metoda byla paměti shromážděných a odpojeno. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které vyžadují rozšířené profil bitové kopie. Odpovídá `COR_PRF_REQUIRE_PROFILE_IMAGE` příznak v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit po profileru k spuštěné aplikaci.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit pouze během inicializace. Pokusu změnit tyto příznaky jinde vede `HRESULT` hodnotu, která určuje selhání.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_HIGH_MONITOR` Příznaky, které se používají s `pdwEventsHigh` parametr [icorprofilerinfo5::geteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) a [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.  
  
Od verze [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], hodnota `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` změnit od 0 do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). Od verze rozhraní .NET Framework 4.7.2, jeho hodnota změněna z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` k `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` má být bitová maska, která představuje všechny příznaky, které lze nastavit pouze během inicializace. Při pokusu o změnit tyto příznaky jinde výsledkem nezdařené `HRESULT`.

## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [COR_PRF_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [ICorProfilerInfo5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
