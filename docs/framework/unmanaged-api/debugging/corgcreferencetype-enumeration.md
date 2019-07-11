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
ms.openlocfilehash: 3cbecd5be9b1ac7c08e6970933a48eeb95f01a22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739389"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType – výčet
Identifikuje zdrojový objekt bude uvolněna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
- Jako hodnotu `type` pole [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) strukturu, určuje zdroj odkazu nebo popisovač.  
  
- Jako `types` argument [icordebugprocess5::enumeratehandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) metody Určuje typy obslužné rutiny, které chcete zahrnout do výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
