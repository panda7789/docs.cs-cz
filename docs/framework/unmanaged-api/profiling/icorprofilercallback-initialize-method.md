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
ms.openlocfilehash: e4a003b30c495852a3a68d44d92bef35c3ed7812
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866292"
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

  \[in] ukazatel na rozhraní [IUnknown](/cpp/atl/iunknown) , které musí Profiler dotazovat na ukazatel rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) .  

## <a name="remarks"></a>Poznámky  
 `Initialize` volání je jediná možnost Povolit (nebo zakázat) zpětná volání, která jsou neměnná. Jakmile je zpětné volání povoleno voláním `Initialize`, nelze jej později zakázat pomocí [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md). Hodnota COR_PRF_MONITOR_IMMUTABLE výčtu [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) označuje, které události jsou neměnné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [Shutdown – metoda](icorprofilercallback-shutdown-method.md)
