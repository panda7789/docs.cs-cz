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
ms.openlocfilehash: 66643bbb8dbc914b2e0e48a7f0c87630fe95e5d3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445848"
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
 Metoda `ObjectedAllocated` není volána pro přidělení z zásobníku nebo nespravované paměti. Parametr `classId` může odkazovat na třídu ve spravovaném kódu, která ještě nebyla načtena. Profiler obdrží zpětné volání třídy pro tuto třídu hned po zpětném volání `ObjectAllocated`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
