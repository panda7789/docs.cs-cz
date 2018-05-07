---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7d5195215762c25b2d7dc2b71fcd53959656303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a>ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda
Získá symboly statické pole, které odpovídají typ typespec podpis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cbSignature`  
 [v] Počet bajtů `typeSig` pole.  
  
 `typeSig`  
 [v] Bajtové pole obsahující `typespec` podpis.  
  
 `cRequestedSymbols`  
 [v] Počet symboly požadovaný.  
  
 `pcFetchedSymbols`  
 [out] Ukazatel na počet symboly načíst metodu.  
  
 `pSymbols`  
 [out] Ukazatel na [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) pole, která obsahuje požadovanou statické pole symboly.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetInstanceFieldSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)  
 [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
