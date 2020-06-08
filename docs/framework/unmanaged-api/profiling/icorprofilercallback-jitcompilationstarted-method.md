---
title: ICorProfilerCallback::JITCompilationStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 57981ef134dc3f30337d47f5cee426a25d0414cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500036"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted – metoda
Upozorní profileru, že kompilátor JIT (just-in-time) začal kompilovat funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro ID funkce, pro kterou je kompilace spouštěna.  
  
 `fIsSafeToBlock`  
 pro Hodnota, která označuje Profiler, zda blokování bude mít vliv na operaci modulu runtime. Hodnota je, `true` Pokud blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání. v opačném případě `false` .  
  
 I když hodnota `true` nebude mít vliv na modul runtime, může zkosit výsledky profilace.  
  
## <a name="remarks"></a>Poznámky  
 Je možné získat více než jednu dvojici `JITCompilationStarted` a volání [ICorProfilerCallback:: JITCompilationFinished –](icorprofilercallback-jitcompilationfinished-method.md) pro jednotlivé funkce z důvodu způsobu, jakým modul runtime zpracovává konstruktory tříd. Například modul runtime začíná metodou kompilace JIT A, ale je nutné spustit konstruktor třídy pro třídu B. Proto modul runtime JIT – zkompiluje konstruktor pro třídu B a spustí jej. I když je konstruktor spuštěn, provede volání metody A, což způsobí, že metoda A bude znovu zkompilována kompilátorem JIT. V tomto scénáři je první kompilace JIT metody A zastavena. Oba pokusy o metodu kompilace JIT A jsou však hlášeny s událostmi kompilace JIT. Pokud profiler hodlá nahradit kód jazyka MSIL (Microsoft Intermediate Language) pro metodu A voláním metody [ICorProfilerInfo:: SetILFunctionBody –](icorprofilerinfo-setilfunctionbody-method.md) , musí to udělat pro obě `JITCompilationStarted` události, ale může použít stejný blok MSIL pro oba.  
  
 Profilery musí podporovat posloupnost zpětných volání JIT v případech, kdy dvě vlákna současně provádí zpětná volání. Například vlákno A volání `JITCompilationStarted` . Nicméně před voláním vlákna `JITCompilationFinished` B vlákno B volá [ICorProfilerCallback:: EXCEPTIONSEARCHFUNCTIONENTER –](icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce z `JITCompilationStarted` zpětného volání vlákna A. Může se zdát, že ID funkce by ještě nemělo být platné, protože `JITCompilationFinished` Profiler zatím nepřijal volání. V takovém případě je však ID funkce platné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [JITCompilationFinished – metoda](icorprofilercallback-jitcompilationfinished-method.md)
