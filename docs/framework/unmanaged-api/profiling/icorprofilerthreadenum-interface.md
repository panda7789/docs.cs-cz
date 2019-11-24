---
title: ICorProfilerThreadEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: b83706176091fd70d48e0f50a0fe5988c876f606
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447616"
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum – rozhraní
Provides methods to sequentially iterate through a collection of threads in the common language runtime.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|Gets the number of threads that are used by the application.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|Moves the enumerator's cursor to the starting position of the sequence.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|Advances the enumerator's cursor from its current position to skip the specified number of elements.|  
  
## <a name="remarks"></a>Poznámky  
 The `ICorProfilerThreadEnum` interface is an enumerator. It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver. In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
