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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0deadc3783663fe595d8217a167d18e6916c6be9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465995"
---
# <a name="icorprofilercallbackobjectallocated-method"></a>ICorProfilerCallback::ObjectAllocated – metoda
Oznámí profileru, který se přidělí paměť v rámci haldy objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 [in] ID objektu, pro kterou byla přidělena paměť.  
  
 `classId`  
 [in] ID třídy, které je objekt instancí.  
  
## <a name="remarks"></a>Poznámky  
 `ObjectedAllocated` Metoda není volána pro přidělení v zásobníku nebo nespravované paměti. `classId` Parametr mohou odkazovat na třídu ve spravovaném kódu, která dosud nebyla načtena. Profiler obdrží zpětné volání třídy zatížení pro danou třídu ihned po `ObjectAllocated` zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [ClassLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
