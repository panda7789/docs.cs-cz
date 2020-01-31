---
title: ICorDebugCode – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: 4b24b3dfe6a931866acd7eba966811071ff39ea5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788931"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode – rozhraní

Představuje segment kódu jazyka MSIL nebo nativního kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](icordebugcode-createbreakpoint-method.md)|Vytvoří zarážku v zadaném posunu.|  
|[GetAddress – metoda](icordebugcode-getaddress-method.md)|Vrátí relativní virtuální adresu (RVA) segmentu kódu, který toto rozhraní `ICorDebugCode` představuje.|  
|[GetCode – metoda](icordebugcode-getcode-method.md)|Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad. Tato metoda je zastaralá. místo toho použijte [ICorDebugCode2:: getcodechunks –](icordebugcode2-getcodechunks-method.md) .|  
|[GetEnCRemapSequencePoints – metoda](icordebugcode-getencremapsequencepoints-method.md)|Není implementováno.|  
|[GetFunction – metoda](icordebugcode-getfunction-method.md)|Získá "ICorDebugFunction" spojený s tímto `ICorDebugCode`.|  
|[GetILToNativeMapping – metoda](icordebugcode-getiltonativemapping-method.md)|Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunů MSIL na nativní posuny.|  
|[GetSize – metoda](icordebugcode-getsize-method.md)|Vrátí velikost v bajtech binárního kódu představovaného tímto rozhraním `ICorDebugCode`.|  
|[GetVersionNumber – metoda](icordebugcode-getversionnumber-method.md)|Vrátí číslo založené na číslici jedna určující verzi kódu, kterou toto rozhraní `ICorDebugCode` představuje.|  
|[IsIL – metoda](icordebugcode-isil-method.md)|Vrátí hodnotu, která označuje, zda je toto rozhraní `ICorDebugCode` kompilováno do jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugCode` může představovat jazyk MSIL i nativní kód. Objekt "ICorDebugFunction", který představuje kód jazyka MSIL, může mít k němu přidružené buď žádný, nebo jeden objekt `ICorDebugCode`. Objekt "ICorDebugFunction", který představuje nativní kód, může mít k sobě přidružen libovolný počet objektů `ICorDebugCode`.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugCode3 – rozhraní](icordebugcode3-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
