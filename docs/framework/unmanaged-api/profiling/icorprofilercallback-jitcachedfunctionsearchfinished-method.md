---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
ms.openlocfilehash: 6efc9d407bb95f75a79252b2dfad85b396d2164a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500075"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished – metoda
Upozorní profileru, že vyhledávání skončilo pro funkci, která byla dříve kompilována pomocí generátoru nativních imagí (NGen. exe).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>Parametry

- `functionId`

  \[in] ID funkce, pro kterou bylo provedeno hledání.

- `result`

  \[in] hodnota výčtu [COR_PRF_JIT_CACHE](cor-prf-jit-cache-enumeration.md) , která určuje výsledek hledání.

## <a name="remarks"></a>Poznámky  
 V .NET Framework verze 2,0 se [ICorProfilerCallback:: jitcachedfunctionsearchstarted –](icorprofilercallback-jitcachedfunctionsearchstarted-method.md) a `JITCachedFunctionSearchFinished` zpětná volání pro všechny funkce v normálních bitových kopiích Ngen nebudou provádět. Zpětná volání pro všechny funkce v imagi budou generovat pouze image NGen optimalizované pro Profiler. V důsledku dodatečné režie by měl Profiler vyžádat image NGen optimalizované profilerem jenom v případě, že má v úmyslu použít tato zpětná volání k vynucení funkce JIT just-in-time (JIT). V opačném případě by Profiler měl používat opožděnou strategii pro shromažďování informací o funkcích.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
