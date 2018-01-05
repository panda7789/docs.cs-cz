---
title: "CorGCReferenceType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGCReferenceType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorGCReferenceType
helpviewer_keywords: CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b314580f7628eca68a3996aaafb362081c6ed705
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType – výčet
Určuje zdroj objekt tak, aby se uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>Členové  
  
|Název členu|Popis|  
|-----------------|-----------------|  
|`CorHandleStrong`|Popisovač pro silné odkaz z tabulky popisovač objektu.|  
|`CorHandleStrongPinning`|Popisovač pro definovaného silné odkaz z tabulky popisovač objektu.|  
|`CorHandleWeakShort`|Popisovač pro slabé odkazy z tabulky popisovač objektu.|  
|`CorHandleWeakRefCount`|Popisovač pro slabé počítá odkaz na objekt z tabulky popisovač objektu.|  
|`CorHandleStrongRefCount`|Popisovač pro objekt počítá odkaz z tabulky popisovač objektu.|  
|`CorHandleStrongDependent`|Popisovač pro závislý objekt z tabulky popisovač objektu.|  
|`CorHandleStrongAsyncPinned`|Asynchronní objekt definovaného v tabulce popisovač objektu.|  
|`CorHandleStrongSizedByref`|Silné obslužná rutina, která zachová Přibližná velikost souhrnný uzavření všechny objekty a kořeny objektu v době kolekce paměti.|  
|`CorReferenceStack`|Odkaz ze spravovaných zásobníku.|  
|`CorReferenceFinalizer`|Odkaz z fronty finalizační metodu.|  
|CorHandleStrongOnly|Vrátí pouze silné odkazy z tabulky popisovače. Tato hodnota je používán [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metoda.|  
|`CorHandleWeakOnly`|Vrátí jenom slabé odkazy z tabulky popisovače. Tato hodnota je používán [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metoda.|  
|`CorHandleAll`|Vrátí všechny odkazy z tabulky popisovače. Tato hodnota je používán [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metoda.|  
  
## <a name="remarks"></a>Poznámky  
 `CorGCReferenceType` Výčet je používán následovně:  
  
-   Jako hodnotu `type` pole z [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) struktura, znamená to zdroj odkaz nebo popisovač.  
  
-   Jako `types` argument [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) metoda, určuje typy obslužných rutin, které chcete zahrnout do výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
