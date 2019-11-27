---
title: ICorProfilerCallback5 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: ce34d43091cdee0bca88f94711e49072fa4fd08c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430064"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5 – rozhraní
Doplňují informace, které pomůžou profileru identifikovat úplný uzávěr živých objektů při použití s metodou [ICorProfilerCallback:: RootReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) nebo [ICorProfilerCallback2:: RootReferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) společně s metodami [ICorProfilerCallback:: objectReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) a [ConditionalWeakTableElementReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) .  
  
 `ICorProfilerCallback5` musí být implementovaná pomocí profileru spravované paměti pro přihlášení k odběru oznámení souvisejících s závislými popisovači.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Určuje přenosný uzávěr objektů, na které odkazují tyto kořeny, prostřednictvím odkazů na přímé členské pole a prostřednictvím závislostí `ConditionalWeakTable`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
