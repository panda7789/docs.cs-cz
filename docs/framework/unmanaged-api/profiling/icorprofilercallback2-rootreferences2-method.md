---
title: ICorProfilerCallback2::RootReferences2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09616243aef272be041573864effd25017cc65c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992027"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 – metoda
Oznámí profileru odkazy na kořenové po uvolňování paměti došlo k chybě. Tato metoda je rozšířením [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [in] Počet prvků v `rootRefIds`, `rootKinds`, `rootFlags`, a `rootIds` pole.  
  
 `rootRefIds`  
 [in] Pole objektu ID, každý z nich odkazuje na statický objekt nebo objekt v zásobníku. Prvky `rootKinds` pole obsahují informace, které klasifikovat odpovídající elementy ve `rootRefIds` pole.  
  
 `rootKinds`  
 [in] Pole [cor_prf_gc_root_kind –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) hodnoty, které označují typ kořenové kolekce uvolnění paměti.  
  
 `rootFlags`  
 [in] Pole [cor_prf_gc_root_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) hodnot, které popisují vlastnosti kořenové kolekce uvolnění paměti.  
  
 `rootIds`  
 [in] Pole UINT_PTR hodnoty, které odkazují na celé číslo, které obsahuje další informace o kořenové kolekce uvolnění paměti, v závislosti na hodnotu `rootKinds` parametru.  
  
 Pokud je typ kořenového zásobníku, ID kořenového je pro funkci, která obsahuje proměnnou. Pokud toto ID kořenového je 0, funkce je nepojmenovaný funkce, který je interní modulu CLR. Pokud je typ kořenového popisovač, ID kořenového je pro popisovač kolekce uvolnění paměti. U jiných typů kořenové ID je neprůhledná hodnota a je třeba ignorovat.  
  
## <a name="remarks"></a>Poznámky  
 `rootRefIds`, `rootKinds`, `rootFlags`, A `rootIds` pole jsou paralelní pole. To znamená `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, a `rootIds[i]` všechny týkají stejným kořenem.  
  
 Obě `RootReferences` a `RootReferences2` jsou volány pro oznámení profileru. Profilery obvykle implementuje jednu metodu nebo druhé, ale ne obojí, protože předaným informace `RootReferences2` je nadstavbou jazyka, které předáno `RootReferences`.  
  
 Je možné pro položky v `rootRefIds` rovno nule, což znamená, že odpovídající kořenový odkaz má hodnotu null a neodkazuje na objekt na spravované haldě.  
  
 ID objektů vrácených `RootReferences2` nejsou platné během zpětného volání, protože kolekce uvolnění paměti může být uvnitř přesun objektů ze staré adresy k nové adresy. Proto by se neměly pokoušet profilery pro kontrolu objektů během `RootReferences2` volání. Když [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána, všechny objekty se přesunuly na jejich nových umístění a můžete ho bezpečně zkontrolovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
