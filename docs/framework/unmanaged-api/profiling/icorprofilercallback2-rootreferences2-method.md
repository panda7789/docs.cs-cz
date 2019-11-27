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
ms.openlocfilehash: dffd4365669da61f7b321110ad663c131ce591e6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439680"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 – metoda
Oznamuje Profiler o kořenových odkazech poté, co došlo k uvolnění paměti. Tato metoda je rozšířením metody [ICorProfilerCallback:: RootReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cRootRefs`  
 pro Počet prvků v polích `rootRefIds`, `rootKinds`, `rootFlags`a `rootIds`.  
  
 `rootRefIds`  
 pro Pole identifikátorů objektů, z nichž každý odkazuje buď na statický objekt, nebo na objekt v zásobníku. Prvky v poli `rootKinds` poskytují informace pro klasifikaci odpovídajících prvků v poli `rootRefIds`.  
  
 `rootKinds`  
 pro Pole hodnot [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) , které určují typ kořenu uvolňování paměti.  
  
 `rootFlags`  
 pro Pole hodnot [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) , které popisují vlastnosti kořenu uvolňování paměti.  
  
 `rootIds`  
 pro Pole hodnot UINT_PTR, které odkazují na celé číslo, které obsahuje další informace o kořenu uvolňování paměti v závislosti na hodnotě `rootKinds` parametru.  
  
 Pokud je typ kořenového adresáře zásobník, je ID kořenového adresáře pro funkci, která obsahuje proměnnou. Pokud je toto kořenové ID 0, funkce je nepojmenovaná funkce, která je interní pro CLR. Pokud je typ kořene popisovač, ID kořenového adresáře je pro popisovač uvolňování paměti. U ostatních kořenových typů je ID neprůhledná hodnota a měla by být ignorována.  
  
## <a name="remarks"></a>Poznámky  
 Pole `rootRefIds`, `rootKinds`, `rootFlags`a `rootIds` jsou paralelní pole. To znamená, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`a `rootIds[i]` všechny se týkají stejného kořene.  
  
 Pro upozorňování profileru jsou volány `RootReferences` i `RootReferences2`. Profilery obvykle implementují jednu metodu nebo druhou, ale ne obojí, protože informace předané `RootReferences2` jsou nadmnožinou předané v `RootReferences`.  
  
 Je možné, že položky v `rootRefIds` mají hodnotu nula, což znamená, že odpovídající kořenový odkaz má hodnotu null a neodkazuje na objekt na spravované haldě.  
  
 ID objektů vrácená `RootReferences2` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů ze starých adres na nové adresy. Proto by se profilery neměly pokoušet prozkoumat objekty během volání `RootReferences2`. Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) , všechny objekty byly přesunuty do jejich nových umístění a lze je bezpečně zkontrolovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
