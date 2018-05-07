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
ms.openlocfilehash: 2d5dcb089074b52fc87a0bb83c7e062e7ef07b46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="corprfgcrootflags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS – výčet
Určuje vlastnost kořenové kolekce paměti.  
  
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
|`COR_PRF_GC_ROOT_PINNING`|Kořenové zabraňuje uvolňování z přesunutí objektu.|  
|`COR_PRF_GC_ROOT_WEAKREF`|Kořenové nezabrání uvolňování paměti.|  
|`COR_PRF_GC_ROOT_INTERIOR`|Kořenové odkazuje na pole objektu, nikoli samotného objektu.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|Kořenové zabraňuje uvolňování paměti, pokud je tento počet odkaz objektu určitou hodnotu.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_GC_ROOT_FLAGS` je bitová maska, která poskytuje další informace o speciální kořenových certifikačních autorit. Ne všechny kořenové adresáře jsou ale zvláštní. Například některé kořeny nejsou slabé odkazy, vnitřních ukazatelů, definovaného a započítány odkaz. U takových kořenových certifikačních autorit neexistují žádné příznaky k předání informací o tom. Proto metody, které používají tento výčet, jako [icorprofilercallback2::rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) metoda, odeslání 0 bitové masky příznaky, která určuje, že všechny flags jsou vypnuté.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
