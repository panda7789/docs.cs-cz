---
title: "Výčet COR_PRF_HIGH_MONITOR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ec30d19af133b4f0734dadf8775dc8682666e22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfhighmonitor-enumeration"></a>Výčet COR_PRF_HIGH_MONITOR
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje příznaky kromě těch, které v nalezen [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který můžete vybrat profileru [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES     = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED     = 0x00000002,     
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE       = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH      = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE           = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Žádné příznaky se nastavují.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Ovládací prvky [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání pro přidání odkazů na sestavení během procházení uzavření odkaz na sestavení CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Ovládací prvky [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) zpětné volání pro aktualizace do datového proudu symbol, který je přidružený modul v paměti.|  
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které vyžadují rozšířené profil bitové kopie. Odpovídá `COR_PRF_REQUIRE_PROFILE_IMAGE` příznak v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit po profileru k spuštěné aplikaci.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit pouze během inicializace. Pokusu změnit tyto příznaky jinde vede `HRESULT` hodnotu, která určuje selhání.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_HIGH_MONITOR` Příznaky, které se používají s `pdwEventsHigh` parametr [icorprofilerinfo5::geteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) a [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.  
  
 Od verze [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], hodnota `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` změnit od 0 do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [COR_PRF_MONITOR – výčet](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [ICorProfilerInfo5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
