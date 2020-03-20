---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177043"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
[Podporováno v rozhraní .NET Framework 4.7 a novějších verzích]  
  
Upozorní profiler při každém spuštění kompilace JIT dynamické metody.  
  
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
[v]`functionId`  
Identifikátor funkce v paměti, pro kterou je spuštěna kompilace JIT.

[v] `fIsSafeToBlock` označuje, že blokování může způsobit, že runtime čekat na volání vlákno vrátit z tohoto zpětného 
 `true` volání; `false` znamená, že blokování nebude mít vliv na provoz za běhu.  

[v] `pILHeader` Ukazatel na první bajt hlavičky IL metody.

[v] `cbILHeader` Počet bajtů v záhlaví IL.

## <a name="remarks"></a>Poznámky  

Toto zpětné volání se aktivuje vždy, když je dynamická metoda kompilován JIT. To zahrnuje různé IL útržky a LCG metody. Jeho cílem je poskytnout autoři profiler s dostatek informací k identifikaci kompilované metody pro uživatele.

> [!NOTE]
> `functionId`hodnoty nelze použít k překladu na jejich tokeny metadat, protože dynamické metody nemají žádná metadata.

Ukazatel `pILHeader` je platný pouze během zpětného volání.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Viz také

- [DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 – rozhraní](icorprofilercallback8-interface.md)
