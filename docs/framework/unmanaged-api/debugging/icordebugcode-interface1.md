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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75cc8ea9d88dda42362f50b519864b1a78e1a64b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960791"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode – rozhraní

Představuje segment kódu jazyka MSIL nebo nativního kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Vytvoří zarážku v zadaném posunu.|  
|[GetAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Vrátí relativní virtuální adresu (RVA) segmentu kódu, který toto rozhraní `ICorDebugCode` představuje.|  
|[GetCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad. Tato metoda je zastaralá. místo toho použijte [ICorDebugCode2:: getcodechunks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) .|  
|[GetEnCRemapSequencePoints – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Není implementováno.|  
|[GetFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Načte "ICorDebugFunction" spojený s tímto `ICorDebugCode`.|  
|[GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunů MSIL na nativní posuny.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Vrátí velikost v bajtech binárního kódu představovaného tímto rozhraním `ICorDebugCode`.|  
|[GetVersionNumber – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Vrátí číslo založené na číslici jedna určující verzi kódu, kterou toto rozhraní `ICorDebugCode` představuje.|  
|[IsIL – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Vrátí hodnotu, která označuje, zda je toto rozhraní `ICorDebugCode` kompilováno do jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugCode` může představovat jazyk MSIL i nativní kód. Objekt "ICorDebugFunction", který představuje kód jazyka MSIL, může mít k němu `ICorDebugCode` přidružené buď nula, nebo jeden objekt. K objektu "ICorDebugFunction", který představuje nativní kód, může být přidružen `ICorDebugCode` libovolný počet objektů.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugCode3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
