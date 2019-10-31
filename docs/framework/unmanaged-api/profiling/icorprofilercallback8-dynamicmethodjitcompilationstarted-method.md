---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted – metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 1eaf29e1c93f352facde4af2ee57910783d82e5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136467"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::D ynamicMethodJITCompilationStarted – metoda
[Podporováno v .NET Framework 4,7 a novějších verzích]  
  
Upozorní profiler vždy při spuštění kompilace JIT dynamické metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a>Parametry  
[in] `functionId`  
Identifikátor funkce v paměti, pro kterou je spuštěná kompilace JIT.   

[in] `fIsSafeToBlock`   
`true` k označení toho, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání; `false` k označení, že blokování nebude mít vliv na operaci modulu runtime.  

[in] `pILHeader`    
Ukazatel na první bajt hlavičky IL metody.   

[in] `cbILHeader`    
Počet bajtů v hlavičce IL. 

## <a name="remarks"></a>Poznámky  

Toto zpětné volání se aktivuje pokaždé, když je dynamická metoda kompilována JIT. To zahrnuje různé zástupné procedury IL a LCG metody. Jeho cílem je poskytnout zapisovačům profileru dostatek informací pro identifikaci zkompilované metody uživatelům.

> [!NOTE]
> hodnoty `functionId` nelze použít k překladu na jejich tokeny metadat, protože dynamické metody nemají žádná metadata.

Ukazatel `pILHeader` je platný pouze během zpětného volání.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 – rozhraní](icorprofilercallback8-interface.md)
