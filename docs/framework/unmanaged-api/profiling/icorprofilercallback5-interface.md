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
ms.openlocfilehash: 02a690503d7b6323f19dcb66247d8a552b760b1c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499204"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5 – rozhraní
Doplňují informace, které pomůžou profileru identifikovat úplný uzávěr živých objektů při použití s metodou [ICorProfilerCallback:: RootReferences –](icorprofilercallback-rootreferences-method.md) nebo [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) společně s metodami [ICorProfilerCallback:: objectReferences –](icorprofilercallback-objectreferences-method.md) a [ConditionalWeakTableElementReferences –](icorprofilercallback5-conditionalweaktableelementreferences-method.md) .  
  
 `ICorProfilerCallback5`musí být implementováno pomocí profileru spravované paměti pro přihlášení k odběru oznámení souvisejících s závislými popisovači.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences – metoda](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Určuje přenosný uzávěr objektů, na které odkazují tyto kořeny, prostřednictvím přímých odkazů na pole členů a prostřednictvím `ConditionalWeakTable` závislostí.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
