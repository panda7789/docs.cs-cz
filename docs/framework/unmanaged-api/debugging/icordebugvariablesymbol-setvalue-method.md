---
title: 'ICorDebugVariableSymbol:: SetValue – metoda'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: fbd3d617e3448730241ccfda7bd26b65d17b694d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121881"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol:: SetValue – metoda
Přiřadí hodnotu bajtového pole proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Počáteční posun v proměnné, při které má být nastavena hodnota. Tento parametr se používá při zápisu do polí členů v objektu.  
  
 `threadID`  
 pro Identifikátor vlákna vlákna, jehož kontext musí být aktualizován, aby odrážel novou hodnotu.  
  
 `cbContext`  
 pro Velikost v bajtech kontextu vlákna.  
  
 `context`  
 pro Kontext vlákna použitý k zápisu hodnoty.  
  
 `cbValue`  
 pro Velikost `pValue` vyrovnávací paměti v bajtech.  
  
 `pValue`  
 pro Vyrovnávací paměť obsahující hodnotu, kterou chcete nastavit.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugVariableSymbol – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
