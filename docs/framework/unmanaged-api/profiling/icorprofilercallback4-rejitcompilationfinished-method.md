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
ms.openlocfilehash: ff06c285bf5306977b520ed9ff845e70fb25989a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499373"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a>ICorProfilerCallback4::ReJITCompilationFinished – metoda
Upozorní profileru, že kompilátor JIT (just-in-time) dokončil opětovné kompilování funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro ID funkce, která byla znovu zkompilována.  
  
 `rejitId`  
 pro Identita funkce Rekompilované JIT.  
  
 `hrStatus`  
 pro Hodnota, která označuje, zda byla opětovná kompilace JIT úspěšná.  
  
 `fIsSafeToBlock`  
 [in] `true` pro indikaci, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání; `false`pro indikaci, že blokování nebude mít vliv na operaci modulu runtime.  
  
 Hodnota `true` nepoškozuje modul runtime, ale může ovlivnit výsledky profilace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
- [JITCompilationStarted – metoda](icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted – metoda](icorprofilercallback4-rejitcompilationstarted-method.md)
