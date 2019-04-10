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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263c22a07f363c2752afb50779515de043976e93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207705"
---
# <a name="corprfgcrootflags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS – výčet
Označuje vlastnost kořenové kolekce uvolnění paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`COR_PRF_GC_ROOT_PINNING`|Kořen brání uvolňování získat přechodem na objekt.|  
|`COR_PRF_GC_ROOT_WEAKREF`|Kořen nebrání uvolňování paměti.|  
|`COR_PRF_GC_ROOT_INTERIOR`|Kořenovém adresáři odkazuje na pole objektu, nikoli samotného objektu.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|Kořen zabrání uvolňování paměti, pokud je počet odkazů na objekt je určitou hodnotu.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_GC_ROOT_FLAGS` je bitová maska, která poskytuje další informace o speciální kořenové adresáře. Ale ne všechny kořeny jsou speciální. Například některé kořeny nejsou slabé odkazy, vnitřních ukazatelů, připnuté nebo referenčně započítaný. Pro takové kořeny nejsou žádné příznaky vyjádřit. Proto metody, které používají tento výčet, jako [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) metody send 0 bitové masky příznaky, která udává, že všechny příznaky jsou vypnuté.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Profilace výčtů](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
