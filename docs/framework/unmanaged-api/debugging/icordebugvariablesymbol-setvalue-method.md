---
title: ICorDebugVariableSymbol::SetValue – metoda
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b83efca5a8b175d5dc83c03de473262ca033354c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491305"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol::SetValue – metoda
Přiřadí hodnotu pole bajtů na proměnnou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `offset`  
 [in] Počáteční posun v proměnné, ve kterém se má nastavit hodnotu. Tento parametr se používá při zápisu do pole člena v objektu.  
  
 `threadID`  
 [in] Identifikátor vlákna, jehož kontext musí být aktualizovány tak, aby odrážely novou hodnotu.  
  
 `cbContext`  
 [in] Velikost v bajtech kontext vlákna.  
  
 `context`  
 [in] Kontext vlákna používá pro zápis hodnoty.  
  
 `cbValue`  
 [in] Velikost v bajtech `pValue` vyrovnávací paměti.  
  
 `pValue`  
 [in] Vyrovnávací paměť, která obsahuje hodnotu pro nastavení.  
  
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
