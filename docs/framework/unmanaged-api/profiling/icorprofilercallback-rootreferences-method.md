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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfab1d716b5a8b530561e2dc72442591eb0d8e42
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499027"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences – metoda
Upozornění profileru s informacemi o odkazů na kořenový po uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [in] Počet odkazů v `rootRefIds` pole.  
  
 `rootRefIds`  
 [in] Pole ID objektů, které odkazují na statický objekt nebo objekt v zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Obě `RootReferences` a [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) jsou volány pro oznámení profileru. Profilery obvykle implementuje jednu z nich, ale nikoli oba současně, protože předaným informace `RootReferences2` je nadstavbou jazyka, které předáno `RootReferences`.  
  
 Je možné, `rootRefIds` pole tak, aby obsahovala objekt s hodnotou null. Například všechny odkazy na objekty deklarované v zásobníku jsou považovány za kořeny uvolnění paměti a vždy se ohlásí.  
  
 ID objektů vrácených `RootReferences` nejsou platné během zpětného volání, protože kolekce uvolnění paměti může být uvnitř přesun objektů ze staré adresy k nové adresy. Proto se nesmíte pokoušet profilery pro kontrolu objektů během `RootReferences` volání. Když [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána, všechny objekty se přesunuly na jejich nových umístění a můžete ho bezpečně zkontrolovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
