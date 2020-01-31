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
ms.openlocfilehash: 6e6cc44c2f9028c0e26c4f933242cad93e3a98c3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866088"
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
 pro Počet objektů odkazovaný specifikovaným objektem (tj. počet prvků v poli `objectRefIds`).  
  
 `objectRefIds`  
 pro Pole ID objektů, na které odkazují `objectId`.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ObjectReferences` je volána pro každý objekt zbývající v haldě po dokončení uvolňování paměti. Pokud Profiler vrátí chybu z tohoto zpětného volání, služba profilování přestane pokračovat ve volání tohoto zpětného volání do dalšího uvolňování paměti.  
  
 Zpětné volání `ObjectReferences` lze použít ve spojení s zpětným voláním [ICorProfilerCallback:: RootReferences –](icorprofilercallback-rootreferences-method.md) pro vytvoření kompletního grafu odkazů na objekty pro modul runtime. Modul CLR (Common Language Runtime) zajišťuje, že každý odkaz na objekt je uveden pouze jednou metodou `ObjectReferences`.  
  
 ID objektů vrácená `ObjectReferences` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů. Proto se profilery nesmí pokoušet prozkoumat objekty během volání `ObjectReferences`. Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) , uvolňování paměti je dokončeno a kontrola může být provedena bezpečně.  
  
 `ClassId` null značí, že `objectId` má typ, který se uvolňuje.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
