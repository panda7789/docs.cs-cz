---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18bfab7a666a4c715b2236f5101bcceacb5b2fed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072685"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a>ICorDebugSymbolProvider::GetStaticFieldSymbols – metoda
Získá statické pole symboly, které odpovídají token typespec podpis.  
  
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
  
## <a name="parameters"></a>Parametry  
 `cbSignature`  
 [in] Počet bajtů `typeSig` pole.  
  
 `typeSig`  
 [in] Bajtové pole obsahující `typespec` podpis.  
  
 `cRequestedSymbols`  
 [in] Počet symbolů požadavku.  
  
 `pcFetchedSymbols`  
 [out] Ukazatel na počet symbolů načíst pomocí metody.  
  
 `pSymbols`  
 [out] Ukazatel [icordebugstaticfieldsymbol –](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) pole, které obsahuje symboly požadovaný statické pole.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetInstanceFieldSymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
