---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished – metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136574"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::D ynamicMethodJITCompilationFinished – metoda
[Podporováno v .NET Framework 4,7 a novějších verzích]  
  
Upozorní profiler vždy, když se dokončí kompilace JIT dynamické metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>Parametry  
[in] `functionId`  
Identifikátor funkce v paměti, pro kterou je spuštěná kompilace JIT.   

[in] `hrStatus`   
Hodnota, která označuje, zda byla kompilace JIT úspěšná.

[in] `fIsSafeToBlock`   
`true` k označení toho, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání; `false` k označení, že blokování nebude mít vliv na operaci modulu runtime.  

## <a name="remarks"></a>Poznámky  

Toto zpětné volání je aktivováno při dokončení kompilace JIT dynamické metody. To zahrnuje různé zástupné procedury IL a LCG metody. Jeho cílem je poskytnout zapisovačům profileru dostatek informací pro identifikaci zkompilované metody uživatelům.

> [!NOTE]
> hodnoty `functionId` nelze použít k překladu na jejich tokeny metadat, protože dynamické metody nemají žádná metadata.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 – rozhraní](icorprofilercallback8-interface.md)
