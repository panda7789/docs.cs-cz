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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dbe8d4f7050b93ffb34280be6d63367ef294ae8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049710"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]  
  
Profiler upozorní pokaždé, když se dokončí kompilace JIT dynamické metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>Parametry  
[in] `functionId`  
Identifikátor funkce v paměti, pro které JIT kompilace spuštění.   

[in] `hrStatus`   
Hodnota, která určuje, zda byla úspěšná kompilace JIT.

[in] `fIsSafeToBlock`   
`true` k označení, že blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; `false` k označení, že blokování nebude mít vliv na operace modulu runtime.  

## <a name="remarks"></a>Poznámky  

Toto zpětné volání se aktivuje vždy, když dokončil kompilace JIT dynamické metody. To zahrnuje různé zástupné procedury IL a LCG metody. Jeho cílem je poskytnout dostatek informací k identifikaci metody kompilované pro uživatele autoři profileru.

> [!NOTE]
> `functionId` hodnoty nelze přeložit na jejich tokeny metadat použít, protože dynamické metody mají žádná metadata.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 – rozhraní](icorprofilercallback8-interface.md)
