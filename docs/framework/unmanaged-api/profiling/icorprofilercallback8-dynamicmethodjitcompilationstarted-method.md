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
ms.openlocfilehash: a4c434c5d458602db8a4d582b239d6e57def6ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498996"
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
pro`functionId`  
Identifikátor funkce v paměti, pro kterou je spuštěná kompilace JIT.

[in] `fIsSafeToBlock` 
 `true` pro indikaci, že blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání; `false`pro indikaci, že blokování nebude mít vliv na operaci modulu runtime.  

[in] `pILHeader` Ukazatel na první bajt hlavičky IL metody.

[in] `cbILHeader` Počet bajtů v hlavičce IL.

## <a name="remarks"></a>Poznámky  

Toto zpětné volání se aktivuje pokaždé, když je dynamická metoda kompilována JIT. To zahrnuje různé zástupné procedury IL a LCG metody. Jeho cílem je poskytnout zapisovačům profileru dostatek informací pro identifikaci zkompilované metody uživatelům.

> [!NOTE]
> `functionId`hodnoty nelze použít k přeložení tokenů metadat, protože dynamické metody nemají žádná metadata.

`pILHeader`Ukazatel je platný pouze během zpětného volání.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 – rozhraní](icorprofilercallback8-interface.md)
