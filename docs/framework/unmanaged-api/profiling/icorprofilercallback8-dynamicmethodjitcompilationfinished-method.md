---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175106"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
[Podporováno v rozhraní .NET Framework 4.7 a novějších verzích]  
  
Upozorní profiler vždy, když je dokončena kompilace JIT dynamické metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a>Parametry  
[v]`functionId`  
Identifikátor funkce v paměti, pro kterou je spuštěna kompilace JIT.

[v] `hrStatus` Hodnota, která označuje, zda byla kompilace JIT úspěšná.

[v] `fIsSafeToBlock` označuje, že blokování může způsobit, že runtime čekat na volání vlákno vrátit z tohoto zpětného 
 `true` volání; `false` znamená, že blokování nebude mít vliv na provoz za běhu.  

## <a name="remarks"></a>Poznámky  

Toto zpětné volání se aktivuje vždy, když jit kompilace dynamické metody byla dokončena. To zahrnuje různé IL útržky a LCG metody. Jeho cílem je poskytnout autoři profiler s dostatek informací k identifikaci kompilované metody pro uživatele.

> [!NOTE]
> `functionId`hodnoty nelze použít k překladu na jejich tokeny metadat, protože dynamické metody nemají žádná metadata.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Viz také

- [DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 – rozhraní](icorprofilercallback8-interface.md)
