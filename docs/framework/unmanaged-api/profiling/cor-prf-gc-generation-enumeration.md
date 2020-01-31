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
ms.openlocfilehash: 4eff8472e353c4e5fd2505b281cc9efc89f013fc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867206"
---
# <a name="cor_prf_gc_generation-enumeration"></a>COR_PRF_GC_GENERATION – výčet
Identifikuje generování kolekce uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`COR_PRF_GC_GEN_0`|Objekt je uložen jako generace 0.|  
|`COR_PRF_GC_GEN_1`|Objekt je uložen jako generace 1.|  
|`COR_PRF_GC_GEN_2`|Objekt je uložen jako generace 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|Objekt je uložen v haldě velkých objektů.|  
  
## <a name="remarks"></a>Poznámky  
 Systém uvolňování paměti vylepšuje výkon správy paměti vydělením objektů do generací na základě stáří. Systém uvolňování paměti aktuálně používá tři generace, očíslované 0, 1 a 2, a navíc speciální segment haldy, který se používá pro velké objekty. Objekty, jejichž velikost je větší než konkrétní hodnota, jsou uloženy v haldě velkých objektů. Ostatní přidělené objekty začínají mimo generaci 0. Všechny objekty, které existují po uvolnění paměti, jsou v generaci 0 povýšeny na generaci 1. Objekty, které existují po uvolnění paměti, dojde v 1. generaci do generace 2.  
  
 Použití generací znamená, že systém uvolňování paměti musí v jednom okamžiku pracovat pouze s podmnožinou přidělených objektů.  
  
 `COR_PRF_GC_GENERATION` výčet používá struktura [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](profiling-enumerations.md)
