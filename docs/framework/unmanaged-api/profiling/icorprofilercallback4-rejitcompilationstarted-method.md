---
title: "ICorProfilerCallback4::ReJITCompilationStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 903db06089f7c68843b503c94483087ff9fce636
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted – metoda
Upozorní profileru, že kompilátoru za běhu (JIT) byla spuštěna znovu kompilovat funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReJITCompilationStarted(    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, která JIT kompilátoru bylo zahájeno její kompilace.  
  
 `rejitId`  
 [v] ID rekompilace nové verze funkce.  
  
 `fIsSafeToBlock`  
 [v] `true` k označení, že blokování může způsobit modulu runtime počkejte volající vlákno k návratu z této zpětného volání; `false` k označení, že blokování neovlivní operaci modulu runtime. Hodnota `true` nepříznivý vliv modul runtime, ale může ovlivnit profilování výsledky.  
  
## <a name="remarks"></a>Poznámky  
 Je možné získat více než jednu dvojici `ReJITCompilationStarted` a [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) metoda volá pro jednotlivé funkce z důvodu způsob, jakým modul runtime konstruktory třídu obslužné rutiny. Například modul runtime začne znovu zkompiluje metoda A, ale konstruktoru třídy pro třídy B musí být spuštěn. Modul runtime proto znovu zkompiluje v konstruktoru pro třídy B a ho spouští. Je spuštěn v konstruktoru, provede volání do metody A, což způsobí, že metoda A k akci zopakovat. V tomto scénáři je první rekompilace metody A zastavit. Však obě pokusí znovu zkompiluje metoda A jsou hlášené s rekompilace JIT – události.  
  
 Profilery musí podporovat posloupnost zpětných volání rekompilace JIT v případech, kde jsou dva vláken současně provádění zpětných volání. Například přístup z více vláken A volá `ReJITCompilationStarted`; však před volání vláken A [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), vlákno B volání [icorprofilercallback::exceptionsearchfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID – funkce z `ReJITCompilationStarted` zpětné volání pro přístup z více vláken A. Může se zdát, že funkce ID nesmí být ještě platný protože volání [rejitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) kdyby ještě přijatý nástrojem profileru. V takovém případě Identifikátor funkce je však platný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [ReJITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
