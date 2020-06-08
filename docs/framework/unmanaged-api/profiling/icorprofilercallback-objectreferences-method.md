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
ms.openlocfilehash: 12a0792e8fafc73b480de6bacc86f98470dfedf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503286"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences – metoda
Upozorní profiler na objekty v paměti, na které je odkazováno pomocí zadaného objektu.  
  
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
 pro ID objektu, který odkazuje na objekty.  
  
 `classId`  
 pro ID třídy, jejíž zadaný objekt je instancí.  
  
 `cObjectRefs`  
 pro Počet objektů odkazovaný specifikovaným objektem (tj. počet prvků v `objectRefIds` poli).  
  
 `objectRefIds`  
 pro Pole identifikátorů objektů, na které odkazuje `objectId` .  
  
## <a name="remarks"></a>Poznámky  
 `ObjectReferences`Metoda je volána pro každý objekt zbývající v haldě po dokončení uvolňování paměti. Pokud Profiler vrátí chybu z tohoto zpětného volání, služba profilování přestane pokračovat ve volání tohoto zpětného volání do dalšího uvolňování paměti.  
  
 `ObjectReferences`Zpětné volání lze použít ve spojení s zpětným voláním [ICorProfilerCallback:: RootReferences –](icorprofilercallback-rootreferences-method.md) pro vytvoření kompletního grafu odkazů na objekty pro modul runtime. Modul CLR (Common Language Runtime) zajišťuje, že každý odkaz na objekt je uveden pouze jednou `ObjectReferences` metodou.  
  
 ID objektů vrácená nástrojem `ObjectReferences` nejsou platná během samotného zpětného volání, protože uvolňování paměti může být uprostřed přesunutí objektů. Proto profilery nesmí zkoušet při volání kontrolu objektů `ObjectReferences` . Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) , uvolňování paměti je dokončeno a kontrola může být provedena bezpečně.  
  
 Hodnota null `ClassId` značí, že `objectId` má typ, který se vykládá.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
