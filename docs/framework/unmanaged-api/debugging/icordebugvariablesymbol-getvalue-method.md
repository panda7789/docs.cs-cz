---
title: ICorDebugVariableSymbol::GetValue – metoda
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c626d21f391899a15e5ea35c47d00f1f539fea4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488861"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol::GetValue – metoda
Získá hodnotu proměnné jako bajtové pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `offset`  
 [in] Počáteční posun v proměnné, ze kterého se má načíst hodnotu. Tento parametr se používá při čtení pole člena v objektu.  
  
 `cbContext`  
 [in] Velikost v bajtech `context` argument.  
  
 `context`  
 [in] Kontext vlákna použít ke čtení hodnoty.  
  
 `cbValue`  
 [in] Velikost v bajtech `pValue` vyrovnávací paměti.  
  
 `pcbValue`  
 [out] Počet bajtů zapsaný ve skutečnosti na `pValue` vyrovnávací paměti.  
  
 `pValue`  
 [out] Bajtové pole obsahující hodnotu proměnné.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugVariableSymbol – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
