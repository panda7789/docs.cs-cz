---
title: ICorProfilerCallback::ExceptionCatcherLeave – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: 7d61a6db8f42398a0d6e0d818605592f4fe71cf7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445007"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a>ICorProfilerCallback::ExceptionCatcherLeave – metoda
Upozorňuje profileru, že řízení se předává z příslušného `catch`ho bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a>Poznámky  
 Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti. Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.  
  
 Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ExceptionCatcherEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
