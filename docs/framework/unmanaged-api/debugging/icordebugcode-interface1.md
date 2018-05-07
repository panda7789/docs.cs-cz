---
title: ICorDebugCode Interface1
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
ms.openlocfilehash: 37917577c802514fcebc3ea0792cbce9bb8a7345
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcode-interface1"></a>ICorDebugCode Interface1
Představuje segment kódu jazyka MSIL nebo nativního kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Vytvoří zarážku v zadaném posunu.|  
|[GetAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Vrátí relativní virtuální adresu (RVA) segmentu kódu, který toto rozhraní `ICorDebugCode` představuje.|  
|[GetCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad. Tato metoda je zastaralá; použít [icordebugcode2::getcodechunks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) místo.|  
|[GetEnCRemapSequencePoints – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Není implementováno.|  
|[GetFunction – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Získá "ICorDebugFunction" přidružený k tomuto `ICorDebugCode`.|  
|[GetILToNativeMapping – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|Získá pole instancí "cor_debug_il_to_native_map –", která představuje mapování z MSIL posuny nativní posun.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Vrátí velikost v bajtech binárního kódu představovaného tímto rozhraním `ICorDebugCode`.|  
|[GetVersionNumber – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Vrátí číslo založené na číslici jedna určující verzi kódu, kterou toto rozhraní `ICorDebugCode` představuje.|  
|[IsIL – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Vrátí hodnotu, která označuje, zda je toto rozhraní `ICorDebugCode` kompilováno do jazyka MSIL.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorDebugCode` může představovat jazyk MSIL i nativní kód. Objekt "ICorDebugFunction", který představuje MSIL kód může mít nula nebo jedna `ICorDebugCode` objekty, které jsou s ním spojená. Objekt "ICorDebugFunction", který představuje nativního kódu může mít libovolný počet `ICorDebugCode` objekty, které jsou s ním spojená.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
    
 [ICorDebugCode3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
