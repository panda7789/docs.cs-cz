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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ea53e02cc20964a43bc4784b4354d429e238295
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a>ICorProfilerCallback::ExceptionCatcherLeave – metoda
Upozorní profileru, který ovládací prvek je předávána mimo odpovídající `catch` bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
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
 [ExceptionCatcherEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
