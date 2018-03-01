---
title: "ICorProfilerCallback::JITCompilationStarted – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 12a25f452ccb121ef7ebcae05048eb7116b4ac48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted – metoda
Upozorní profileru, že kompilátoru za běhu (JIT) byla spuštěna zkompilovat funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, pro který se spouští kompilace.  
  
 `fIsSafeToBlock`  
 [v] Hodnotu, která určuje profileru, zda blokování ovlivní operaci modulu runtime. Hodnota je `true` Pokud blokování může způsobit počkejte volající vlákno k návratu z této zpětného volání; modulu runtime, jinak hodnota `false`.  
  
 I když hodnota `true` nebude poškodit modul runtime, zkreslit profilování výsledky.  
  
## <a name="remarks"></a>Poznámky  
 Je možné získat více než jednu dvojici `JITCompilationStarted` a [icorprofilercallback::jitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) volání pro každou funkci kvůli způsobu, jakým modul runtime konstruktory třídu obslužné rutiny. Například metoda JIT – kompilace A začne modul runtime, ale konstruktoru třídy pro třídy B musí být spuštěn. Proto runtime JIT zkompiluje v konstruktoru pro třídy B a spustí ho. Je spuštěn v konstruktoru, provede volání do metody A, což způsobí, že metoda A Chcete-li být kompilována znovu. V tomto scénáři se zastavilo první JIT – kompilace metody A. Však obě pokusy o metoda JIT – kompilace A oznamuje s událostmi JIT – kompilace. Pokud budete profileru nahraďte kód Microsoft (MSIL intermediate language) pro metodu A voláním [icorprofilerinfo::setilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metodu, musíte udělat, tak pro obě `JITCompilationStarted` události, ale může používat stejný blok MSIL pro obě.  
  
 Profilery musí podporovat posloupnost zpětných volání JIT v případech, kde jsou dva vláken současně provádění zpětných volání. Například přístup z více vláken A volá `JITCompilationStarted`. Nicméně před volání vláken A `JITCompilationFinished`, vlákno B volání [icorprofilercallback::exceptionsearchfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce z vlákna na `JITCompilationStarted` zpětného volání. Může se zdát, že funkce ID nesmí být ještě platný protože volání `JITCompilationFinished` kdyby ještě přijatý nástrojem profileru. V případě tohoto typu, je však platné ID funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [JITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
