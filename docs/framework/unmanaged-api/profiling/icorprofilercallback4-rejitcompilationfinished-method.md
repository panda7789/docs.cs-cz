---
title: ICorProfilerCallback4::ReJITCompilationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cf2e1be735150dfb006e2274c79c25649d0271d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a>ICorProfilerCallback4::ReJITCompilationFinished – metoda
Upozorní profileru, že nutnosti rekompilace funkce kompilátoru za běhu (JIT) byla dokončena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, která byla zopakovat.  
  
 `rejitId`  
 [v] Identita překompilovat JIT funkce.  
  
 `hrStatus`  
 [v] Hodnota, která určuje, zda rekompilace JIT byla úspěšná.  
  
 `fIsSafeToBlock`  
 [v] `true` k označení, že blokování může způsobit modulu runtime počkejte volající vlákno k návratu z této zpětného volání; `false` k označení, že blokování neovlivní operaci modulu runtime.  
  
 Hodnota `true` nepříznivý vliv modul runtime, ale může ovlivnit profilování výsledky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [ReJITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
