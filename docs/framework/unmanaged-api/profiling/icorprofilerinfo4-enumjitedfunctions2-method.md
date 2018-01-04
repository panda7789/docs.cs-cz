---
title: "ICorProfilerInfo4::EnumJITedFunctions2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumJITedFunctions2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7dc381848307ea0606f6989d6946c11aa5ef9a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a>ICorProfilerInfo4::EnumJITedFunctions2 – metoda
Vrátí enumerátor pro všechny funkce, které byly dříve kompilována a překompilovat JIT. Nahradí tato metoda [icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metodu, která není výčet překompilovat JIT ID.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Ukazatel [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerátor.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se mohou překrývat s `JITCompilation` zpětná volání, jako [icorprofilercallback::jitcompilationstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metoda. Vrácený výčtu obsahuje hodnoty pro `COR_PRF_FUNCTION::reJitId` pole. [Icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metodu, která nahradí tato metoda není výčet překompilovat JIT ID, protože `COR_PRF_FUNCTION::reJitId` pole je vždycky nastavený na hodnotu 0. `ICorProfilerInfo4::EnumJITedFunctions` Metoda výčet překompilovat JIT ID, protože `COR_PRF_FUNCTION::reJitId` pole je správně nastaveno. Všimněte si, že [icorprofilerinfo4::enumjitedfunctions2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metoda můžete aktivovat uvolňování paměti, zatímco [icorprofilerinfo3::enumjitedfunctions – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) nikoli.  Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [EnumJITedFunctions – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)  
 [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
