---
title: "ICorProfilerCallback4 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4
helpviewer_keywords: ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efcbc9adce9b5cfc39c5eb3e1649a35d458e99c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 – rozhraní
Poskytuje metody zpětného volání, které modul CLR (CLR) používá ke sdělování informací profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReJITParameters – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|Umožňuje profileru kódu nastavit alternativní kód pro nový text Rekompilované metoda příznaky generace.|  
|[MovedReferences2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|Sestavy nové rozložení objektů v haldě v důsledku komprimaci uvolnění paměti.|  
|[ReJITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|Upozorní profileru, že kompilátoru za běhu (JIT) byla dokončena rekompilace funkce.|  
|[ReJITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|Upozorní profileru, že kompilátoru za běhu (JIT) byla spuštěna znovu kompilovat funkci.|  
|[ReJITError – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|Sestavy k chybě při zpracování požadavku. pak ji znovu zkompilovat.|  
|[SurvivingReferences2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|Sestavy rozložení objektů v haldě v důsledku uvolnění paměti kompresi.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
