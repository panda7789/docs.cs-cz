---
title: 'ICorDebugSymbolProvider:: GetInstanceFieldSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 0ad8ddd78d963681c0b2f69bf0f211ad464dc7b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138873"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a>ICorDebugSymbolProvider:: GetInstanceFieldSymbols – metoda
Načte symboly pole instance, které odpovídají token TypeSpec podpisu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbSignature`  
 pro Počet bajtů v poli `typeSig`.  
  
 `typeSig`  
 pro Bajtové pole obsahující podpis `typespec`.  
  
 `cRequestedSymbols`  
 pro Počet požadovaných symbolů.  
  
 `pcFetchedSymbols`  
 mimo Ukazatel na počet symbolů načtených metodou.  
  
 `pSymbols`  
 mimo Ukazatel na pole [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) , které obsahuje symboly pole požadované instance.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetStaticFieldSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
