---
title: COR_GC_REFERENCE – struktura
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc0b67621f77c0741e0b63b84ab1794530d6280b
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274228"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE – struktura
Obsahuje informace o objektu, který má být shromážděn z paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`domain`|Ukazatel na doménu aplikace, ke které patří popisovač nebo objekt. Jeho hodnota může být `null`.|  
|`location`|Rozhraní ICorDebugValue nebo ICorDebugReferenceValue, které odpovídá objektu, který má být uvolněn do paměti.|  
|`type`|Hodnota výčtu [CorGCReferenceType –](corgcreferencetype-enumeration.md) , která určuje, odkud kořen pochází. Další informace najdete v části poznámky.|  
|`extraData`|Další informace o objektu, který má být shromážděn do paměti. Tyto informace závisí na zdroji objektu, jak je uvedeno v `type` poli. Další informace najdete v části poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 Pole je hodnota výčtu CorGCReferenceType –, která určuje, odkud odkaz pochází. [](corgcreferencetype-enumeration.md) `type` Konkrétní `COR_GC_REFERENCE` hodnota může odrážet kterýkoli z následujících typů spravovaných objektů:  
  
- Objekty ze všech spravovaných zásobníků`CorGCReferenceType.CorReferenceStack`(). To zahrnuje živé odkazy ve spravovaném kódu a také objekty vytvořené modulem CLR (Common Language Runtime).  
  
- Objekty z tabulky Handles (`CorGCReferenceType.CorHandle*`). To zahrnuje silné odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.  
  
- Objekty z fronty finalizační metody (`CorGCReferenceType.CorReferenceFinalizer`). Objekty kořene fronty finalizační metody, dokud není spuštěn finalizační metoda.  
  
 `extraData` Pole obsahuje další data v závislosti na zdroji (nebo typu) odkazu. Možné hodnoty jsou:  
  
- `DependentSource`. Pokud je, `CorGCREferenceType.CorHandleStrongDependent`toto pole je objekt, který, pokud je aktivní, objekt, který má být uvolněn do paměti v `COR_GC_REFERENCE.Location`. `type`  
  
- `RefCount`. `type` Pokud je `CorGCREferenceType.CorHandleStrongRefCount`, toto pole je počet odkazů popisovače.  
  
- `Size`. `type` Pokud je `CorGCREferenceType.CorHandleStrongSizedByref`, toto pole je poslední velikost stromu objektu, pro který systém uvolňování paměti vypočítal kořeny objektů. Všimněte si, že tento výpočet není nutně aktuální.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
