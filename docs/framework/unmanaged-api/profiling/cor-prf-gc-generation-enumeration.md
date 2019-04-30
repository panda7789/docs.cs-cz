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
ms.openlocfilehash: 0178e2a7877803644bb25e6700306d7ac2ef2d4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775073"
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION – výčet
Identifikuje uvolnění paměti generace.  
  
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
|`COR_PRF_GC_GEN_1`|Objekt se uloží jako 1. generace.|  
|`COR_PRF_GC_GEN_2`|Objekt se uloží jako 2. generace.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|Objekt se uloží ve velkých objektových haldách.|  
  
## <a name="remarks"></a>Poznámky  
 Systému uvolňování paměti zlepšuje výkon správy paměti dělicí objekty do generací podle věku. Uvolňování paměti aktuálně používá tři generace číslované 0, 1 a 2 plus zvláštní haldy segment, který se používá pro velké objekty. Objekty, jejichž velikost je větší než konkrétní hodnoty jsou uloženy v velkých objektových haldách. Další přidělené objekty se začínají patřící do 0. generace. Všechny objekty, které existují, jakmile dojde k uvolnění paměti generace 0 jsou povýšeny do generace 1. Objekty, které existují, jakmile dojde k uvolnění paměti v generaci 1 přesunout do 2. generace.  
  
 Použití generace znamená, že má systému uvolňování paměti pro práci s pouze podmnožinu přidělených objektů v daný okamžik.  
  
 `COR_PRF_GC_GENERATION` Výčet je používán [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
