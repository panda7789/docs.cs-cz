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
ms.openlocfilehash: e22269b76c230f702f4712298fddcd0df1fde50d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179319"
---
# <a name="cor_gc_reference-structure"></a>COR_GC_REFERENCE – struktura
Obsahuje informace o objektu, který má být uvolněna.  
  
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
|`domain`|Ukazatel na doménu aplikace, do které patří popisovač nebo objekt. Jeho hodnota `null`může být .|  
|`location`|Buď ICorDebugValue nebo ICorDebugReferenceValue rozhraní, které odpovídá objektu, který má být uvolněna.|  
|`type`|Hodnota výčtu [CorGCReferenceType,](corgcreferencetype-enumeration.md) která označuje, odkud kořen pochází. Další informace naleznete v části Poznámky.|  
|`extraData`|Další data o objektu, který má být uvolněno. Tyto informace závisí na zdroji objektu, jak `type` je uvedeno v poli. Další informace naleznete v části Poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 Pole `type` je hodnota výčtu [CorGCReferenceType,](corgcreferencetype-enumeration.md) která označuje, odkud odkaz pochází. Určitá `COR_GC_REFERENCE` hodnota může odrážet některý z následujících druhů spravovaných objektů:  
  
- Objekty ze všech`CorGCReferenceType.CorReferenceStack`spravovaných hromádek ( ). To zahrnuje živé odkazy ve spravovaném kódu, stejně jako objekty vytvořené běžným jazykem runtime.  
  
- Objekty z tabulky`CorGCReferenceType.CorHandle*`úchytu ( ). To zahrnuje silné`HNDTYPE_STRONG` odkazy `HNDTYPE_REFCOUNT`( a ) a statické proměnné v modulu.  
  
- Objekty z fronty`CorGCReferenceType.CorReferenceFinalizer`finalizační metody ( ). Kořeny fronty finalizační metody, dokud není spuštěna finalizační metoda.  
  
 Pole `extraData` obsahuje další data v závislosti na zdroji (nebo typu) odkazu. Možné hodnoty:  
  
- `DependentSource`. Pokud `type` je `CorGCREferenceType.CorHandleStrongDependent`, toto pole je objekt, který, pokud je `COR_GC_REFERENCE.Location`naživu, kořeny objektu, který má být uvolněna na .  
  
- `RefCount`. Pokud `type` je `CorGCREferenceType.CorHandleStrongRefCount`, toto pole je referenční počet popisovače.  
  
- `Size`. Pokud `type` je `CorGCREferenceType.CorHandleStrongSizedByref`, toto pole je poslední velikost stromu objektů, pro které systém uvolňování paměti vypočítal kořeny objektu. Všimněte si, že tento výpočet není nutně aktuální.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro ladění](debugging-structures.md)
- [ladění](index.md)
