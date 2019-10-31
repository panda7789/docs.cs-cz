---
title: 'ICorDebugSymbolProvider:: GetMethodParameterSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: 1f7da156e5a164dc753e2283bc7ab24d18983173
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138846"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a>ICorDebugSymbolProvider:: GetMethodParameterSymbols – metoda
Načte symboly parametrů metody vzhledem k relativní virtuální adrese (RVA) dané metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nativeRVA`  
 pro Nativní relativní virtuální adresa metody  
  
 `cRequestedSymbols`  
 pro Počet požadovaných místních symbolů.  
  
 `pcFetchedSymbols`  
 mimo Ukazatel na počet symbolů načtených metodou.  
  
 `pcFetchedSymbols`  
 mimo Ukazatel na pole [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) , které obsahuje místní symboly metody.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetMethodLocalSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
