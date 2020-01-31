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
ms.openlocfilehash: 76cab0b8b5f16f24c62e31be2707c95c7e557034
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777642"
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next – metoda
Získá zadaný počet instancí [CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) , které mapují identifikátory GUID na informace typu.  
  
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
 mimo Pole ukazatelů, z nichž každý odkazuje na objekt [CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) , který MAPUJE prostředí Windows Runtime GUID na odpovídající objekt ICorDebugType.  
  
 `pceltFetched`  
 mimo Ukazatel na počet [CorDebugGuidToTypeMapping –ch](cordebugguidtotypemapping-structure.md) objektů, které jsou ve skutečnosti vráceny v `values`.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** prostředí Windows Runtime  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugGuidToTypeEnum – rozhraní](icordebugguidtotypeenum-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
