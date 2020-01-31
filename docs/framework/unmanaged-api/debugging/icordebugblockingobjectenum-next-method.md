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
ms.openlocfilehash: c25f26bb0f1f34e3799bab4bec7e697d393cccb4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784518"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next – metoda
Získá zadaný počet objektů [CorDebugBlockingObject –](cordebugblockingobject-structure.md) z výčtu počínaje aktuální pozicí.  
  
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
 mimo Pole ukazatelů na [CorDebugBlockingObject –](cordebugblockingobject-structure.md) objekty.  
  
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
> I když struktura [CorDebugBlockingObject –](cordebugblockingobject-structure.md) nemusí být uvolněna, je nutné uvolnit rozhraní "ICorDebugValue" uvnitř této struktury.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDataTarget – rozhraní](icordebugdatatarget-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
