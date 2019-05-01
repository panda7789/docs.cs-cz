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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 114d97e02b0a6b80c46f971ed74a24dc3c397f1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049671"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5 – rozhraní
Doplňující informace, které pomůžou profiler identifikovat úplné ukončení živé objekty při použití s buď [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) nebo [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)metody společně s [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) a [conditionalweaktableelementreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) metody.  
  
 `ICorProfilerCallback5` musí být implementované spravované paměti profileru k odběru oznámení týkajících se závislé popisovače.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Identifikuje přechodné uzavření objekty odkazují tyto kořenové adresáře prostřednictvím oba odkazy na pole přímé členy a prostřednictvím `ConditionalWeakTable` závislosti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
