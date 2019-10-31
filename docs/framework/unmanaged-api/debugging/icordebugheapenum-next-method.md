---
title: ICorDebugHeapEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 1beb69bfaad9acb9c269ad8becb81bea64edb6a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138460"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next – metoda
Získá zadaný počet instancí [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , které obsahují informace o objektech na spravované haldě.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 celt  
 pro Počet objektů, které mají být načteny.  
  
 – objekty  
 mimo Pole ukazatelů, z nichž každý odkazuje na objekt [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , který poskytuje informace o objektu na spravované haldě.  
  
 pceltFetched  
 mimo Ukazatel na počet [COR_HEAPOBJECTch](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objektů, které jsou ve skutečnosti vráceny v `objects`. Tato hodnota může být `null`, pokud `celt` 1.  
  
## <a name="remarks"></a>Poznámky  
 Pole `COR_HEAPOBJECT.type` je identifikátor vnořeného rozhraní COM s vypočítaným odkazem. Tento odkaz musí být vydaný volajícím `ICorDebugHeapEnum::Next`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugHeapEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
