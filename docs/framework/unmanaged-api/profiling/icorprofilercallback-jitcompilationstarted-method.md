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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 88362d33c05c25e7a86e474adf37f2ccd0474ff4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530755"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted – metoda
Oznámí profileru, kompilátor just-in-time (JIT) byla spuštěna kompilovat funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] ID funkce, pro který se spouští kompilace.  
  
 `fIsSafeToBlock`  
 [in] Hodnotu, která k profileru, zda blokování bude mít vliv na operace modulu runtime. Hodnota je `true` Pokud blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; v opačném případě `false`.  
  
 I když hodnota `true` nepoškodí modul runtime, je zkosení výsledků profilace.  
  
## <a name="remarks"></a>Poznámky  
 Je možné přijímat více než jednu dvojici `JITCompilationStarted` a [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) volá pro každou funkci kvůli způsobu, jakým modul runtime konstruktor třídy obslužné rutiny. Například modul runtime spustí metodě JIT-kompilovat A, ale třída konstruktor třídy B musí být spuštěn. Proto se modul runtime JIT zkompiluje konstruktor třídy B a spustí ho. Je spuštěn konstruktoru, provede volání do metody A, což způsobí, že metoda A být znovu sestaveny JIT. V tomto scénáři je první JIT kompilaci metody A zastaveno. Ale i pokusy o metoda JIT-kompilovat A označené s událostmi kompilace JIT. Pokud profileru kód Microsoft intermediate language (MSIL) pro metodu A nahraďte voláním [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metodu, musíte udělat, tak pro obě `JITCompilationStarted` události, ale může používat stejný blok MSIL u obou.  
  
 Profilovací programy musí podporovat posloupnost zpětných volání JIT v případech, kde dva vláken současně, aby zpětná volání. Například, vlákna A zavolá `JITCompilationStarted`. Nicméně před volání vlákna A `JITCompilationFinished`, vlákno B vyvolá [icorprofilercallback::exceptionsearchfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce z vlákna A `JITCompilationStarted` zpětného volání. Může se zdát, že ID funkce by neměl být ještě platný protože volání `JITCompilationFinished` nebyl dosud nebylo přijato pomocí profileru. V případě tohoto typu, je však platné ID funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
