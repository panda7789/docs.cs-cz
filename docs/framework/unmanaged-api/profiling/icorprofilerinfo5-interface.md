---
title: Rozhraní ICorProfilerInfo5
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: e6df5dcb26d61d30407d1efeeed7d207744276fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124190"
---
# <a name="icorprofilerinfo5-interface"></a>Rozhraní ICorProfilerInfo5
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Podtřída [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) , která poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|Získá aktuální kategorie událostí, pro které profiler chce dostávat oznámení z CLR.|  
|[SetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|Nastaví hodnotu, která určuje typy událostí, pro které profiler chce dostávat oznámení události z CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Metody, které jsou k dispozici v tomto rozhraní, mají za cíl nahradit metody [ICorProfilerInfo:: GetEventMask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
