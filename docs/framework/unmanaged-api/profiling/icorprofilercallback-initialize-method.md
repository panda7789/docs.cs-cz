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
ms.openlocfilehash: 64df6a81eb23c20537238c702fd0c204d64d14bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434552"
---
# <a name="icorprofilercallbackinitialize-method"></a>ICorProfilerCallback::Initialize – metoda
Volá se, aby se inicializoval Profiler kódu, když se spustí nová aplikace Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `pICorProfilerInfoUnk`  
 [v](/cpp/atl/iunknown) rozhraní, které musí Profiler zadat dotaz na ukazatel rozhraní [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) .  
  
## <a name="remarks"></a>Poznámky  
 `Initialize` volání je jediná možnost Povolit (nebo zakázat) zpětná volání, která jsou neměnná. Jakmile je zpětné volání povoleno voláním `Initialize`, nelze jej později zakázat pomocí [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Hodnota COR_PRF_MONITOR_IMMUTABLE výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) označuje, které události jsou neměnné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Shutdown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
