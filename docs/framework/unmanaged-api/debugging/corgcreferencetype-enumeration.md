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
ms.openlocfilehash: eafae181c74d9f3842f7f0d547bcccbbb28c09e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132125"
---
# <a name="corgcreferencetype-enumeration"></a>CorGCReferenceType – výčet
Určuje zdroj objektu, který má být shromážděn do paměti.  
  
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
|`CorHandleStrong`|Popisovač na silný odkaz z tabulky popisovače objektu.|  
|`CorHandleStrongPinning`|Popisovač připnutého silného odkazu z tabulky popisovače objektu.|  
|`CorHandleWeakShort`|Popisovač na slabý odkaz z tabulky popisovače objektu.|  
|`CorHandleWeakRefCount`|Popisovač slabého objektu s vypočítaným odkazem z tabulky popisovače objektu.|  
|`CorHandleStrongRefCount`|Popisovač objektu počítaného odkazem z tabulky popisovače objektu.|  
|`CorHandleStrongDependent`|Popisovač závislého objektu z tabulky popisovače objektu.|  
|`CorHandleStrongAsyncPinned`|Asynchronní připnutý objekt z tabulky popisovače objektu.|  
|`CorHandleStrongSizedByref`|Silný popisovač, který při uvolňování paměti udržuje přibližnou velikost souhrnu všech objektů a kořenových objektů.|  
|`CorReferenceStack`|Odkaz ze spravovaného zásobníku.|  
|`CorReferenceFinalizer`|Odkaz z fronty finalizační metody.|  
|CorHandleStrongOnly|Vrátí pouze silné odkazy z tabulky popisovače. Tuto hodnotu používá pouze metoda [ICorDebugProcess5:: EnumerateHandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) .|  
|`CorHandleWeakOnly`|Vrátí pouze slabé odkazy z tabulky popisovačů. Tuto hodnotu používá pouze metoda [ICorDebugProcess5:: EnumerateHandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) .|  
|`CorHandleAll`|Vrátí všechny odkazy z tabulky popisovače. Tuto hodnotu používá pouze metoda [ICorDebugProcess5:: EnumerateHandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) .|  
  
## <a name="remarks"></a>Poznámky  
 `CorGCReferenceType` výčet se používá následujícím způsobem:  
  
- Jako hodnota pole `type` struktury [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) označuje zdroj odkazu nebo popisovače.  
  
- Jako argument `types` pro metodu [ICorDebugProcess5:: EnumerateHandles –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) určuje typy popisovačů, které mají být zahrnuty do výčtu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
