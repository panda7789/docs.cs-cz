---
title: ICorProfilerCallback4::ReJITCompilationStarted – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177084"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted – metoda
Upozorní profiler, že kompilátor just-in-time (JIT) začal znovu kompilovat funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, která kompilátor JIT začala znovu kompilovat.  
  
 `rejitId`  
 [v] ID rekompilace nové verze funkce.  
  
 `fIsSafeToBlock`  
 [v] `true` označuje, že blokování může způsobit, že runtime čekat na volání vlákno vrátit z tohoto zpětného volání; `false` znamená, že blokování nebude mít vliv na provoz za běhu. Hodnota `true` nepoškozuje za běhu, ale může ovlivnit výsledky profilování.  
  
## <a name="remarks"></a>Poznámky  
 Je možné přijímat více než `ReJITCompilationStarted` jeden pár a [ReJITCompilationFinish](icorprofilercallback4-rejitcompilationfinished-method.md) volání metody pro každou funkci z důvodu způsobu runtime zpracovává konstruktory třídy. Například runtime začne překompilovat metodu A, ale konstruktor třídy pro třídu B musí být spuštěn. Proto runtime překompiluje konstruktor pro třídu B a spustí jej. Při spuštění konstruktoru provede volání metody A, která způsobí, že metoda A znovu zkompilovat. V tomto scénáři je zastavena první rekompilace metody A. Oba pokusy o překompilování metody A jsou však hlášeny s událostmi rekompilace JIT.  
  
 Profilovací programy musí podporovat posloupnost jit recompilation zpětná volání v případech, kdy dvě vlákna jsou současně volání. Například volání vlákna A `ReJITCompilationStarted`; však před podproces volání [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), vlákno B volání [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce z zpětného `ReJITCompilationStarted` volání pro vlákno A. Může se zdát, že ID funkce by ještě neměla být platná, protože volání [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) ještě nebyla přijata profiler. V tomto případě je však ID funkce platné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
- [JITCompilationFinished – metoda](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished – metoda](icorprofilercallback4-rejitcompilationfinished-method.md)
