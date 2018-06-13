---
title: COR_PRF_GC_GENERATION – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8283139566050b1858a003316dc46581822a9bbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450151"
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION – výčet
Identifikuje generace kolekce paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|Objekt se uloží jako 0. generace.|  
|`COR_PRF_GC_GEN_1`|Objekt se uloží jako generace 1.|  
|`COR_PRF_GC_GEN_2`|Objekt se uloží jako generace 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|Objekt se uloží v haldě velkého objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Uvolňování paměti zlepšuje výkon správy paměti dělicí objekty do generace podle stáří. Garbage collector v současné době používá tři generace, číslované 0, 1 a 2 a speciální haldy segment, který se používá pro velké objekty. Objekty, jejichž velikost je větší než určitou hodnotu jsou uloženy v haldě velkého objektu. Další přidělené objekty spustí patřící do generace 0. Všechny objekty, které existují po dojde k uvolnění paměti v generaci 0 povýšené na 1. generace. Objekty, které existují po dojde k uvolnění paměti v generaci 1, přesuňte do 2. generace.  
  
 Použití generace znamená, že má kolekce uvolňování paměti pro práci s jenom podmnožinu přidělené objekty v daném okamžiku.  
  
 `COR_PRF_GC_GENERATION` Výčet je používán [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktura.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
