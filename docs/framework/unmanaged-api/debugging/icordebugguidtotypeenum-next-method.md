---
title: ICorDebugGuidToTypeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: f6f190cd5b2f208df5a4ed88b650af671f2e6c5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138517"
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next – metoda
Získá zadaný počet instancí [CorDebugGuidToTypeMapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , které mapují identifikátory GUID na informace typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet objektů mapování typu GUID na typ, které mají být načteny.  
  
 `values`  
 mimo Pole ukazatelů, z nichž každý odkazuje na objekt [CorDebugGuidToTypeMapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , který MAPUJE prostředí Windows Runtime GUID na odpovídající objekt ICorDebugType.  
  
 `pceltFetched`  
 mimo Ukazatel na počet [CorDebugGuidToTypeMapping –ch](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objektů, které jsou ve skutečnosti vráceny v `values`.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** prostředí Windows Runtime  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugGuidToTypeEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
