---
title: "ICorProfilerCallback2::RootReferences2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.RootReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 29a5a3051b75df18a08498369aa5707a53caf75f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 – metoda
Upozorní profileru o odkazů na kořenový po uvolnění paměti došlo k chybě. Tato metoda je rozšířením [icorprofilercallback::rootreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [v] Počet elementů ve `rootRefIds`, `rootKinds`, `rootFlags`, a `rootIds` pole.  
  
 `rootRefIds`  
 [v] Pole ID, objektů každý z nich odkazuje na objekt statické nebo objekt v zásobníku. Elementy v `rootKinds` pole obsahují informace, které klasifikovat odpovídající elementů v `rootRefIds` pole.  
  
 `rootKinds`  
 [v] Pole [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) hodnoty, které označují typ kořenové kolekce paměti.  
  
 `rootFlags`  
 [v] Pole [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) hodnoty, které popisuje vlastnosti kořenové kolekce paměti.  
  
 `rootIds`  
 [v] Pole UINT_PTR hodnot, které odkazují na celé číslo, které obsahuje další informace o kořenové kolekce paměti, v závislosti na hodnotě `rootKinds` parametr.  
  
 Pokud je typ kořenové zásobníku, kořenové ID je pro tuto funkci, která obsahuje proměnnou. Pokud toto ID kořenové 0, funkce je nepojmenované funkce, která je interní modulu CLR. Je-li typ kořenové popisovač, je kořenový ID pro popisovač kolekce paměti. Pro ostatní typy kořenové ID je neprůhledné hodnoty a třeba ji ignorovat.  
  
## <a name="remarks"></a>Poznámky  
 `rootRefIds`, `rootKinds`, `rootFlags`, A `rootIds` pole jsou paralelní pole. To znamená `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, a `rootIds[i]` všechny týkají stejnou kořenovou.  
  
 Obě `RootReferences` a `RootReferences2` se nazývají oznámit profileru. Profilery bude obvykle implementovat jednu metodu nebo dalších, ale ne obojí, protože předaná informace `RootReferences2` je nadmnožinou, je předaná `RootReferences`.  
  
 Je možné pro položky v `rootRefIds` být nula, což znamená, že odkaz na odpovídající kořenové má hodnotu null a není odkaz na objekt v haldě spravované.  
  
 Vrácený objekt ID `RootReferences2` nejsou platné během zpětného volání sebe, protože kolekce paměti může být uprostřed přesun objektů z původní adresy na nové adresy. Proto profilery neměli zkontrolovat objekty během `RootReferences2` volání. Když [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána, všechny objekty byly přesunuty do nového umístění a může být prověřovány bezpečně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
