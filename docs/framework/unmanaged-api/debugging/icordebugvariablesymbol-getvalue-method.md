---
title: 'ICorDebugVariableSymbol:: GetValue – metoda'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: f217f7226d53a27363f66eb90a340fd3604a0217
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396521"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol:: GetValue – metoda
Získá hodnotu proměnné jako bajtové pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Počáteční posun v proměnné, ze které se má číst hodnota Tento parametr se používá při čtení polí členů v objektu.  
  
 `cbContext`  
 pro Velikost argumentu v bajtech `context`  
  
 `context`  
 pro Kontext vlákna použitý ke čtení hodnoty.  
  
 `cbValue`  
 pro Velikost vyrovnávací paměti v bajtech `pValue` .  
  
 `pcbValue`  
 mimo Počet bajtů, které jsou ve skutečnosti zapsány do `pValue` vyrovnávací paměti.  
  
 `pValue`  
 mimo Bajtové pole, které obsahuje hodnotu proměnné.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugVariableSymbol – rozhraní](icordebugvariablesymbol-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
