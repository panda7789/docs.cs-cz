---
title: ICorProfilerCallback::ExceptionSearchCatcherFound – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: 8f5997dddf78dd75d482bc45d2ee730b20d9ab16
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866467"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a>ICorProfilerCallback::ExceptionSearchCatcherFound – metoda
Upozorní profileru, že ve fázi hledání výjimek byla nalezena obslužná rutina pro vyvolanou výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Parametry

- `functionId`

  \[in] ID funkce, která obsahuje obslužnou rutinu výjimky.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
