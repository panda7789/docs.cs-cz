---
title: ICorProfilerCallback::Initialize – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: ea4fc8ab39d616415106150f56f4b7afd5f68237
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500101"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize – metoda
Volá se, aby se inicializoval Profiler kódu, když se spustí nová aplikace Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>Parametry

- `pICorProfilerInfoUnk`

  \[v] ukazatel na rozhraní [IUnknown](/cpp/atl/iunknown) , které musí Profiler zadat dotaz na ukazatel rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) .  

## <a name="remarks"></a>Poznámky  
 `Initialize`Volání je jediná možnost Povolit (nebo zakázat) zpětná volání, která jsou neměnná. Jakmile je zpětné volání povoleno `Initialize` voláním, nelze jej zakázat později pomocí [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md). Hodnota COR_PRF_MONITOR_IMMUTABLE výčtu [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) označuje, které události jsou neměnné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [Shutdown – metoda](icorprofilercallback-shutdown-method.md)
