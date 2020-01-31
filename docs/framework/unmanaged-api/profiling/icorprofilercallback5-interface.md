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
ms.openlocfilehash: 7981e7d2d2a4588e56d3c30d0ede2d003fdcd32e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865022"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5 – rozhraní
Doplňují informace, které pomůžou profileru identifikovat úplný uzávěr živých objektů při použití s metodou [ICorProfilerCallback:: RootReferences –](icorprofilercallback-rootreferences-method.md) nebo [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) společně s metodami [ICorProfilerCallback:: objectReferences –](icorprofilercallback-objectreferences-method.md) a [ConditionalWeakTableElementReferences –](icorprofilercallback5-conditionalweaktableelementreferences-method.md) .  
  
 `ICorProfilerCallback5` musí být implementovaná pomocí profileru spravované paměti pro přihlášení k odběru oznámení souvisejících s závislými popisovači.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences – metoda](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Určuje přenosný uzávěr objektů, na které odkazují tyto kořeny, prostřednictvím odkazů na přímé členské pole a prostřednictvím závislostí `ConditionalWeakTable`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
