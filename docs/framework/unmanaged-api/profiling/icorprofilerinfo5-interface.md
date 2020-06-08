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
ms.openlocfilehash: 82f6262c2c576b49be4e7fcaa14043950df4c67a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495624"
---
# <a name="icorprofilerinfo5-interface"></a>Rozhraní ICorProfilerInfo5
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Podtřída [ICorProfilerInfo4](icorprofilerinfo4-interface.md) , která poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[Metoda GetEventMask2](icorprofilerinfo5-geteventmask2-method.md)|Získá aktuální kategorie událostí, pro které profiler chce dostávat oznámení z CLR.|  
|[Metoda SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)|Nastaví hodnotu, která určuje typy událostí, pro které profiler chce dostávat oznámení události z CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Metody, které jsou k dispozici v tomto rozhraní, mají za cíl nahradit metody [ICorProfilerInfo:: GetEventMask –](icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
