---
title: "ICorDebugSymbolProvider::GetTypeProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ba736caf8d8d823a4cb56c75aa2202ad616983fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Getmethodprops – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)  
 [ICorDebugSymbolProvider rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
