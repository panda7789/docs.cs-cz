---
title: COR_PRF_GC_ROOT_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 0210aca5698cd9c86979c13afd1e622b50d194df
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867178"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS – výčet
Označuje vlastnost kořenu uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|Kořen zabraňuje uvolňování paměti v přesunutí objektu.|  
|`COR_PRF_GC_ROOT_WEAKREF`|Kořen nebrání v uvolňování paměti.|  
|`COR_PRF_GC_ROOT_INTERIOR`|Kořen odkazuje na pole objektu, nikoli na samotný objekt.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|Kořen zabraňuje uvolňování paměti, pokud je počet odkazů objektu určitou hodnotou.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_GC_ROOT_FLAGS` je Bitová maska, která poskytuje další informace o speciálních kořenech. Ale ne všechny kořeny jsou speciální. Například některé kořeny neobsahují slabé odkazy, vnitřní ukazatele, připnuté nebo odpočítané odkazy. Pro tyto kořeny neexistují žádné příznaky k vyjádření. Proto metody, které používají tento výčet, jako je například metoda [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) , odesílají 0 pro bitovou masku příznaků, což značí, že jsou všechny příznaky vypnuty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](profiling-enumerations.md)
