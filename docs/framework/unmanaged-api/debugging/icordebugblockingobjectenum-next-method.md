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
ms.openlocfilehash: 0ef49d2d833841eac62b2b964a0fdc902b4fb6a9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894775"
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
|S_FALSE|`pceltFetched`se nerovná `celt`.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda funguje jako typický enumerátor COM.  
  
 Hodnoty vstupního pole musí mít aspoň velikost `celt`. Pole bude vyplněno buď pomocí dalších `celt` hodnot ve výčtu, nebo se všemi zbývajícími hodnotami, pokud je méně než `celt` zbývá. Když se tato metoda vrátí `pceltFetched` , vyplní se počtem hodnot, které byly načteny. Pokud `values` obsahuje neplatné ukazatele nebo odkazuje na vyrovnávací paměť, která je menší než `celt`nebo pokud `pceltFetched` je neplatný ukazatel, výsledek není definován.  
  
> [!NOTE]
> I když struktura [CorDebugBlockingObject –](cordebugblockingobject-structure.md) nemusí být uvolněna, je nutné uvolnit rozhraní "ICorDebugValue" uvnitř této struktury.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugDataTarget – rozhraní](icordebugdatatarget-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
