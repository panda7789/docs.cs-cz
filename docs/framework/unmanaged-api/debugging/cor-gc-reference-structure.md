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
ms.openlocfilehash: 0375fdd6f86ae89171545cfdcb44ac37074084e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718712"
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE – struktura
Obsahuje informace o objektu, který má být uvolněna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`domain`|Ukazatel na doménu aplikace, ke kterému patří popisovač nebo objekt. Jeho hodnota může být `null`.|  
|`location`|ICorDebugValue nebo icordebugreferencevalue – rozhraní, která odpovídá objekt, který má být uvolněna.|  
|`type`|A [corgcreferencetype –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnotu výčtu, která určuje, odkud pochází kořenový adresář. Další informace najdete v části poznámky.|  
|`extraData`|Údaje o objekt, který má být uvolněna. Tyto informace závisí na zdroji objektu, je určeno `type` pole. Další informace najdete v části poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `type` Je pole [corgcreferencetype –](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnotu výčtu, která určuje, odkud pochází odkaz. Konkrétní `COR_GC_REFERENCE` hodnotu můžete sledovat některé z následujících typů spravovaných objektů:  
  
-   Objekty z všechny spravované zásobníky (`CorGCReferenceType.CorReferenceStack`). To zahrnuje živé odkazy ve spravovaném kódu, jakož i objekty vytvořené modulem common language runtime.  
  
-   Objekty z tabulky popisovače (`CorGCReferenceType.CorHandle*`). Jedná se o silná odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.  
  
-   Objekty ve frontě finalizační metody (`CorGCReferenceType.CorReferenceFinalizer`). Fronta finalizační metody kořeny objekty, dokud finalizační metodu.  
  
 `extraData` Pole obsahuje doplňující data v závislosti na zdroj (nebo typ) odkaz. Možné hodnoty jsou:  
  
-   `DependentSource`. Pokud `type` je `CorGCREferenceType.CorHandleStrongDependent`, toto pole je objekt, který, pokud zachování připojení, kořenových adresářů objekt, který má být prováděno uvolnění paměti na `COR_GC_REFERENCE.Location`.  
  
-   `RefCount`. Pokud `type` je `CorGCREferenceType.CorHandleStrongRefCount`, toto pole je počet odkazů popisovače.  
  
-   `Size`. Pokud `type` je `CorGCREferenceType.CorHandleStrongSizedByref`, toto pole je poslední velikost stromu objektů, pro které systému uvolňování paměti počítá kořeny objektu. Všimněte si, že tento výpočet není nutně aktuální.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
