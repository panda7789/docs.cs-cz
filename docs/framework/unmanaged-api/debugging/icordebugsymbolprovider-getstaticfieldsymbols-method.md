---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols – metoda'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 02cc62a421058f83e28ce945ae9e76745f768988
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791557"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a>ICorDebugSymbolProvider:: GetStaticFieldSymbols – metoda
Získá symboly statického pole, které odpovídají token TypeSpec podpisu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
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
 mimo Ukazatel na pole [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) , které obsahuje požadované symboly statických polí.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetInstanceFieldSymbols – metoda](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [ICorDebugSymbolProvider – rozhraní](icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
