---
title: ICorProfilerCallback::ObjectReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4141c79502dae89ec228e4e39da121615f292786
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782975"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences – metoda
Upozornění profileru o objektech v paměti, které se odkazuje zadaný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 [in] ID objektu, který odkazuje na objekty.  
  
 `classId`  
 [in] ID třídy, která je instance zadaného objektu.  
  
 `cObjectRefs`  
 [in] Počet objektů, které odkazuje zadaný objekt (to znamená, počet prvků v `objectRefIds` pole).  
  
 `objectRefIds`  
 [in] Pole ID objektů, které se neodkazuje `objectId`.  
  
## <a name="remarks"></a>Poznámky  
 `ObjectReferences` Metoda je volána pro každý objekt zbývajících v haldě, po dokončení procesu uvolnění paměti. Pokud profiler vrátí chybu z této zpětné volání, bude profilování služby přestat vyvolání této zpětné volání až do dalšího uvolnění.  
  
 `ObjectReferences` Zpětného volání lze použít ve spojení s [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) zpětné volání pro vytvoření grafu odkaz na kompletní objekt pro modul runtime. Modul CLR (CLR) zajišťuje, že každý odkaz na objekt je ohlášena jenom jednou `ObjectReferences` metody.  
  
 ID objektů vrácených `ObjectReferences` nejsou platné během zpětného volání, protože kolekce uvolnění paměti může být uvnitř přesouvání objektů. Proto se nesmíte pokoušet profilery pro kontrolu objektů během `ObjectReferences` volání. Když [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána, uvolňování paměti kolekce je kompletní a kontroly lze bezpečně provést.  
  
 S hodnotou null `ClassId` znamená, že `objectId` má typ, který je uvolnění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
