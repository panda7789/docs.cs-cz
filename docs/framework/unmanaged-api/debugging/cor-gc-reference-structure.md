---
title: "COR_GC_REFERENCE – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_REFERENCE
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_GC_REFERENCE
helpviewer_keywords: COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a86604febb7641eef147608e564a27883fdc4bec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE – struktura
Obsahuje informace o objekt, který má být uvolňování paměti.  
  
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
|`domain`|Ukazatel na doménu aplikace, do které patří popisovač nebo objekt. Jeho hodnota může být `null`.|  
|`location`|ICorDebugValue nebo ICorDebugReferenceValue rozhraní, které odpovídá objekt, který má být uvolňování paměti.|  
|`type`|A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnota výčtu, která určuje, odkud pochází kořenu. Další informace najdete v části poznámky.|  
|`extraData`|Další data o objekt, který má být uvolňování paměti. Tyto informace závisí na zdroji objektu, jak `type` pole. Další informace najdete v části poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `type` Pole [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) hodnotu výčtu, která určuje, odkud pochází odkaz na. Konkrétní `COR_GC_REFERENCE` hodnota může vyjadřovat některé z následujících druhy spravované objekty:  
  
-   Objekty z všechny spravované zásobníky (`CorGCReferenceType.CorReferenceStack`). To zahrnuje za provozu odkazy ve spravovaném kódu a také objekty vytvořené modul common language runtime.  
  
-   Objekty z tabulky popisovače (`CorGCReferenceType.CorHandle*`). To zahrnuje silné odkazy (`HNDTYPE_STRONG` a `HNDTYPE_REFCOUNT`) a statické proměnné v modulu.  
  
-   Objekty z fronty finalizační metodu (`CorGCReferenceType.CorReferenceFinalizer`). Fronty finalizační metodu kořeny objekty, dokud finalizační metodu byla spuštěna.  
  
 `extraData` Pole obsahuje doplňující data v závislosti na zdroj (nebo typu) odkaz. Možné hodnoty jsou:  
  
-   `DependentSource`. Pokud `type` je `CorGCREferenceType.CorHandleStrongDependent`, toto pole je objekt, který, pokud je aktivní, kořeny objekt, který má být uvolněna při `COR_GC_REFERENCE.Location`.  
  
-   `RefCount`. Pokud `type` je `CorGCREferenceType.CorHandleStrongRefCount`, toto pole je počet odkazů popisovač.  
  
-   `Size`. Pokud `type` je `CorGCREferenceType.CorHandleStrongSizedByref`, toto pole je poslední velikost stromu objektů, pro které má systém uvolňování vypočtena kořeny objektu. Všimněte si, že tento výpočet není nutně aktuální.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
