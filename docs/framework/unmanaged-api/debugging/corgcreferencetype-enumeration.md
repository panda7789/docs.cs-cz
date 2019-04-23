---
title: CorGCReferenceType – výčet
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a673c98b11fbca5f66e9e1ae61f224448c20797
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207146"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType – výčet
Identifikuje zdrojový objekt bude uvolněna.  
  
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
|`CorHandleStrong`|Popisovač silného odkazu z tabulky popisovač objektu.|  
|`CorHandleStrongPinning`|Popisovač připnuté silného odkazu z tabulky popisovač objektu.|  
|`CorHandleWeakShort`|Popisovač nestálý odkaz z tabulky popisovač objektu.|  
|`CorHandleWeakRefCount`|Popisovač pro objekt slabé počítáním referencí z tabulky popisovač objektu.|  
|`CorHandleStrongRefCount`|Popisovač pro objekt počítáním referencí z tabulky popisovač objektu.|  
|`CorHandleStrongDependent`|Popisovač pro závislý objekt z tabulky popisovač objektu.|  
|`CorHandleStrongAsyncPinned`|Asynchronní objekt připnuté z tabulky popisovač objektu.|  
|`CorHandleStrongSizedByref`|Silný popisovač, který udržuje přibližné velikosti kolektivní ukončení všech objektů a objektů kořeny během uvolňování paměti kolekce.|  
|`CorReferenceStack`|Odkaz ze spravované zásobníku.|  
|`CorReferenceFinalizer`|Odkaz z fronta finalizační metody.|  
|CorHandleStrongOnly|Vrátíte pouze silné odkazy z tabulky popisovače. Tato hodnota se používá [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metody.|  
|`CorHandleWeakOnly`|Vrátí jenom slabé odkazy z tabulky popisovače. Tato hodnota se používá [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metody.|  
|`CorHandleAll`|Vrátí všechny odkazy z tabulky popisovače. Tato hodnota se používá [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) pouze metody.|  
  
## <a name="remarks"></a>Poznámky  
 `CorGCReferenceType` Výčet je používán následujícím způsobem:  
  
-   Jako hodnotu `type` pole [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) strukturu, určuje zdroj odkazu nebo popisovač.  
  
-   Jako `types` argument [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) metody Určuje typy obslužné rutiny, které chcete zahrnout do výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
