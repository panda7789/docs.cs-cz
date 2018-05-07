---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9bd144717decd16a84d2f005d84a22b4ef824d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a>ICorProfilerCallback::ExceptionUnwindFinallyEnter – metoda
Upozorní profileru, který fázi unwind výjimky je zpracování zadání `finally` klauzule obsažené v zadanou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, která obsahuje `finally` klauzule.  
  
## <a name="remarks"></a>Poznámky  
 Profileru by neměly blokovat v jeho implementace této metody, protože zásobník nemusí být ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit preemptivní uvolňování paměti. Pokud zde blokuje profileru a dojde k pokusu o uvolňování paměti, modul runtime se zablokuje, dokud se vrátí tato zpětného volání.  
  
 Okna profilování implementace této metody by neměla volání do spravovaného kódu nebo v žádné příčina způsob přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [GetNotifiedExceptionClauseInfo – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)  
 [ExceptionUnwindFinallyLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
