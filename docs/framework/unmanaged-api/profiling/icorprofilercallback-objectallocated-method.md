---
title: ICorProfilerCallback::ObjectAllocated – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: 9a402b7dfc3ece9d38994ed897162fe0d81ff0b9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503299"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated – metoda
Upozorní profileru, že paměť v haldě byla přidělena pro objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 pro ID objektu, pro který byla přidělena paměť  
  
 `classId`  
 pro ID třídy, jejíž objekt je instancí.  
  
## <a name="remarks"></a>Poznámky  
 `ObjectedAllocated`Metoda není volána pro přidělení z zásobníku nebo nespravované paměti. `classId`Parametr může odkazovat na třídu ve spravovaném kódu, která ještě nebyla načtena. Profiler získá zpětné volání třídy pro tuto třídu ihned po `ObjectAllocated` zpětném volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ClassLoadStarted – metoda](icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished – metoda](icorprofilercallback-classloadfinished-method.md)
