---
title: 'ICorDebugVariableSymbol:: SetValue – metoda'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: fe6b63e4c0706dd69478753b3512f606e73bee7c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790858"
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

- [ICorDebugVariableSymbol – rozhraní](icordebugvariablesymbol-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
