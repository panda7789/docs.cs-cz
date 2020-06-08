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
ms.openlocfilehash: 6e340fa08800f31d36e6cfb280cac847a4fca548
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499347"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted – metoda
Upozorní profileru, že kompilátor JIT (just-in-time) začal znovu kompilovat funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro ID funkce, kterou byl kompilátor JIT spuštěn pro rekompilaci.  
  
 `rejitId`  
 pro ID překompilace nové verze funkce  
  
 `fIsSafeToBlock`  
 [in] `true` pro indikaci, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání; `false`pro indikaci, že blokování nebude mít vliv na operaci modulu runtime. Hodnota `true` nepoškozuje modul runtime, ale může ovlivnit výsledky profilace.  
  
## <a name="remarks"></a>Poznámky  
 Pro každou funkci je možné získat více než jednu dvojici `ReJITCompilationStarted` a [ReJITCompilationFinished –](icorprofilercallback4-rejitcompilationfinished-method.md) volání metody, protože modul runtime zpracovává konstruktory tříd. Například modul runtime začíná znovu kompilovat metodu A, ale je nutné spustit konstruktor třídy pro třídu B. Proto modul runtime znovu zkompiluje konstruktor pro třídu B a spustí jej. I když je konstruktor spuštěn, provede volání metody A, což způsobí, že metoda A bude znovu zkompilována. V tomto scénáři je první opětovná kompilace metody A zastavena. Oba pokusy o rekompilaci metody A jsou však hlášeny s událostmi opětovné kompilace JIT.  
  
 Profilery musí podporovat sekvenci zpětných volání rekompilace JIT v případech, kdy dvě vlákna současně provádí zpětná volání. Například vlákno A volání, `ReJITCompilationStarted` ale před voláním [ReJITCompilationFinished –](icorprofilercallback4-rejitcompilationfinished-method.md)vlákna B volá [ICorProfilerCallback:: ExceptionSearchFunctionEnter –](icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce ze `ReJITCompilationStarted` zpětného volání pro vlákno A. Může se zdát, že ID funkce by ještě nemělo být platné, protože Profiler ještě nepřijal volání [ReJITCompilationFinished –](icorprofilercallback4-rejitcompilationfinished-method.md) . V tomto případě je však ID funkce platné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
- [JITCompilationFinished – metoda](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished – metoda](icorprofilercallback4-rejitcompilationfinished-method.md)
