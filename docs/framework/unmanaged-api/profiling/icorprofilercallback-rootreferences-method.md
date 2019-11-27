---
title: ICorProfilerCallback::RootReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: 9c96cacf508ef5c056a1ff4469247393fdfb9e9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444470"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences – metoda
Oznamuje profileru informace o kořenových odkazech po uvolnění paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cRootRefs`  
 pro Počet odkazů v poli `rootRefIds`.  
  
 `rootRefIds`  
 pro Pole ID objektů, které odkazuje buď na statický objekt, nebo na objekt v zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Pro upozorňování profileru jsou volány `RootReferences` a [ICorProfilerCallback2:: RootReferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) . Profilery obvykle implementují jeden nebo druhý, ale ne obojí, protože informace předané `RootReferences2` jsou nadmnožinou předaných `RootReferences`.  
  
 Je možné, že pole `rootRefIds` obsahuje objekt s hodnotou null. Například všechny odkazy na objekty deklarované v zásobníku jsou považovány za kořeny systémem uvolňování paměti a budou vždy hlášeny.  
  
 ID objektů vrácená `RootReferences` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů ze starých adres na nové adresy. Proto se profilery nesmí pokoušet prozkoumat objekty během volání `RootReferences`. Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) , všechny objekty byly přesunuty do jejich nových umístění a lze je bezpečně zkontrolovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
