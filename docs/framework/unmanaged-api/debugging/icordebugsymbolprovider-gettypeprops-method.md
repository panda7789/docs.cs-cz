---
title: ICorDebugSymbolProvider::GetTypeProps – metoda
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3398e01912309c057cd1e01e8fc0af6c62f976bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421597"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>ICorDebugSymbolProvider::GetTypeProps – metoda
Zadaný relativní virtuální adresy (RVA) v tabulce vtable vrací informace o vlastnosti typ, například počet podpis jeho obecné parametry.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `tableRva`  
 [v] Vytvoření relativní virtuální adresy (RVA) vtable.  
  
 `cbSignature`  
 [v] Velikost `signature` pole. Najdete v části poznámky.  
  
 `pcbSignature`  
 [out] [out] Ukazatel na velikost vrácený `signature` pole.  
  
 `signature`  
 [out] Vyrovnávací paměť, která obsahuje typ typespec signatur všechny obecné parametry.  
  
## <a name="remarks"></a>Poznámky  
 Získat požadovaná velikost typu `signature` pole, nastavte `cbSignature` argument na hodnotu 0 a `signature` k **null**. Po návratu metody `pcbSignature` bude obsahovat počet bajtů požadovaných pro `signature` pole.  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetMethodProps – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)  
 [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
