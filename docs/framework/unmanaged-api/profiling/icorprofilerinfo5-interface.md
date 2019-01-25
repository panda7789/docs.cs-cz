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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e55d52b3ba3bb2b932627ca364ed8f6084fcf26
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536461"
---
# <a name="icorprofilerinfo5-interface"></a>Rozhraní ICorProfilerInfo5
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Podtřída [icorprofilerinfo4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) , který poskytuje metody pro použití u profilery kódu ke komunikaci s common language runtime (CLR) k řízení, monitorování událostí.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|Získá aktuální kategorie událostí, pro které profileru chce, aby dostávala oznámení z modulu CLR.|  
|[SetEventMask2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|Nastaví hodnotu, která určuje typy událostí, pro které profileru chce obdržet oznámení událostí z modulu CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Metody dostupné pro tato rozhraní jsou určeny k nahrazení [icorprofilerinfo::geteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
