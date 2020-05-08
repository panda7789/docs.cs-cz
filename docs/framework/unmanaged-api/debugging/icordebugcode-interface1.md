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
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893474"
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
|[GetFunction – metoda](icordebugcode-getfunction-method.md)|Načte "ICorDebugFunction" spojený s tímto `ICorDebugCode`.|  
|[GetILToNativeMapping – metoda](icordebugcode-getiltonativemapping-method.md)|Získá pole instancí "COR_DEBUG_IL_TO_NATIVE_MAP", které reprezentují mapování z posunů MSIL na nativní posuny.|  
|[GetSize – metoda](icordebugcode-getsize-method.md)|Vrátí velikost v bajtech binárního kódu představovaného tímto rozhraním `ICorDebugCode`.|  
|[GetVersionNumber – metoda](icordebugcode-getversionnumber-method.md)|Vrátí číslo založené na číslici jedna určující verzi kódu, kterou toto rozhraní `ICorDebugCode` představuje.|  
|[IsIL – metoda](icordebugcode-isil-method.md)|Vrátí hodnotu, která označuje, zda je toto rozhraní `ICorDebugCode` kompilováno do jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugCode` může představovat jazyk MSIL i nativní kód. Objekt "ICorDebugFunction", který představuje kód jazyka MSIL, může mít k němu `ICorDebugCode` přidružené buď nula, nebo jeden objekt. K objektu "ICorDebugFunction", který představuje nativní kód, může být přidružen `ICorDebugCode` libovolný počet objektů.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugCode3 – rozhraní](icordebugcode3-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
