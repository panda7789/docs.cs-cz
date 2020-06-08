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
ms.openlocfilehash: b587f30a01623c6e9806bcd9d01058a0880be239
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499906"
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
 pro Počet odkazů v `rootRefIds` poli.  
  
 `rootRefIds`  
 pro Pole ID objektů, které odkazuje buď na statický objekt, nebo na objekt v zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 `RootReferences`Pro upozorňování profileru jsou volány oba a [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) . Profilery obvykle implementují jeden nebo druhý, ale ne obojí, protože předané informace `RootReferences2` jsou nadmnožinou předaných informací `RootReferences` .  
  
 Je možné, že `rootRefIds` pole obsahuje objekt s hodnotou null. Například všechny odkazy na objekty deklarované v zásobníku jsou považovány za kořeny systémem uvolňování paměti a budou vždy hlášeny.  
  
 ID objektů vrácená nástrojem `RootReferences` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů ze starých adres na nové adresy. Proto profilery nesmí zkoušet při volání kontrolu objektů `RootReferences` . Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) , všechny objekty byly přesunuty do jejich nových umístění a lze je bezpečně zkontrolovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
