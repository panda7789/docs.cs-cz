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
ms.openlocfilehash: 2ce58113f40c8eb67a89b6ab6c9bb8f755975bd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499750"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 – metoda
Oznamuje Profiler o kořenových odkazech poté, co došlo k uvolnění paměti. Tato metoda je rozšířením metody [ICorProfilerCallback:: RootReferences –](icorprofilercallback-rootreferences-method.md) .  
  
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
 pro Počet prvků v `rootRefIds` polích,, a `rootKinds` `rootFlags` `rootIds` .  
  
 `rootRefIds`  
 pro Pole identifikátorů objektů, z nichž každý odkazuje buď na statický objekt, nebo na objekt v zásobníku. Prvky v `rootKinds` poli poskytují informace pro klasifikaci odpovídajících prvků v `rootRefIds` poli.  
  
 `rootKinds`  
 pro Pole hodnot [COR_PRF_GC_ROOT_KIND](cor-prf-gc-root-kind-enumeration.md) , které určují typ kořenu uvolňování paměti.  
  
 `rootFlags`  
 pro Pole hodnot [COR_PRF_GC_ROOT_FLAGS](cor-prf-gc-root-flags-enumeration.md) , které popisují vlastnosti kořenu uvolňování paměti.  
  
 `rootIds`  
 pro Pole hodnot UINT_PTR, které odkazují na celé číslo, které obsahuje další informace o kořenu uvolňování paměti v závislosti na hodnotě `rootKinds` parametru.  
  
 Pokud je typ kořenového adresáře zásobník, je ID kořenového adresáře pro funkci, která obsahuje proměnnou. Pokud je toto kořenové ID 0, funkce je nepojmenovaná funkce, která je interní pro CLR. Pokud je typ kořene popisovač, ID kořenového adresáře je pro popisovač uvolňování paměti. U ostatních kořenových typů je ID neprůhledná hodnota a měla by být ignorována.  
  
## <a name="remarks"></a>Poznámky  
 Pole `rootRefIds` , `rootKinds` , `rootFlags` a `rootIds` jsou paralelní pole. To znamená,,, `rootRefIds[i]` `rootKinds[i]` `rootFlags[i]` , a `rootIds[i]` všechny se týkají stejného kořene.  
  
 `RootReferences`A `RootReferences2` jsou volány pro upozorňování profileru. Profilery obvykle implementují jednu metodu nebo druhou, ale ne obojí, protože předané informace `RootReferences2` jsou nadmnožinou, kterou předává `RootReferences` .  
  
 Je možné `rootRefIds` , že položky mají hodnotu nula, což znamená, že odpovídající kořenový odkaz má hodnotu null a neodkazuje na objekt na spravované haldě.  
  
 ID objektů vrácená nástrojem `RootReferences2` nejsou během samotného zpětného volání platná, protože uvolňování paměti může být uprostřed přesunutí objektů ze starých adres na nové adresy. Proto by profilery neměly zkoušet při volání kontrolu objektů `RootReferences2` . Když je volána metoda [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) , všechny objekty byly přesunuty do jejich nových umístění a lze je bezpečně zkontrolovat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
