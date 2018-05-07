---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a79a9c925392b0ab5e50269479b2f693f1a9b58d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a>ICorProfilerCallback::ExceptionUnwindFunctionLeave – metoda
Upozorní profileru, že byla dokončena fázi unwind výjimek unwinding funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a>Poznámky  
 Když `ExceptionUnwindFunctionLeave` metoda je volána, instance funkce a jeho zásobníku data se odeberou ze zásobníku.  
  
 Profileru by neměly blokovat během toto volání, protože zásobníku nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti. Pokud na profileru bloky a uvolnění paměti dojde k pokusu o, modul runtime zablokuje, dokud vrátí tuto zpětného volání.  
  
 Navíc během tohoto hovoru profileru nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ExceptionUnwindFunctionEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
