---
title: ICorDebugBlockingObjectEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
ms.openlocfilehash: 3a1c4a931a61186c4737aada47ceb861e7848e7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122834"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next – metoda
Získá zadaný počet objektů [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) z výčtu počínaje aktuální pozicí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet objektů, které se mají načíst.  
  
 `values`  
 mimo Pole ukazatelů na [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objekty.  
  
 `pceltFetched`  
 mimo Ukazatel na počet objektů, které byly načteny.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|S_FALSE|`pceltFetched` se nerovná `celt`.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda funguje jako typický enumerátor COM.  
  
 Hodnoty vstupního pole musí mít velikost alespoň `celt`. Pole bude vyplněno buď další `celt` hodnoty ve výčtu, nebo všechny zbývající hodnoty, pokud méně než `celt` zůstane. Když se tato metoda vrátí, `pceltFetched` vyplní počet hodnot, které se načetly. Pokud `values` obsahuje neplatné ukazatele nebo odkazuje na vyrovnávací paměť, která je menší než `celt`, nebo pokud je `pceltFetched` neplatný ukazatel, výsledek není definován.  
  
> [!NOTE]
> I když struktura [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nemusí být uvolněna, je nutné uvolnit rozhraní "ICorDebugValue" uvnitř této struktury.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
