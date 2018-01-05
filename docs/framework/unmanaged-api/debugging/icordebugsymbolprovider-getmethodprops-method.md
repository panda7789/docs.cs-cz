---
title: "ICorDebugSymbolProvider::GetMethodProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf92727139dc912107484b1e13944c679c944726
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider::GetMethodProps – metoda
Zadaná relativní virtuální adresy (RVA) v dané metody vrací informace o vlastnosti metoda, například metadata token a informace o jeho obecné parametry metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `codeRVA`  
 [v] Relativní virtuální adresu v metodě o tom, které informace se mají být načteny.  
  
 `pMethodToken`  
 [out] Ukazatel na metodu na token metadat.  
  
 `pcGenericParams`  
 [out] Ukazatel na počet obecné parametry přidružený k této metodě.  
  
 `cbSignature`  
 [v] Velikost `signature` pole. Najdete v části poznámky.  
  
 `pcbSignature`  
 [out] Ukazatel na velikost vrácený `signature` pole.  
  
 `signature`  
 [out] Vyrovnávací paměť, která obsahuje typ typespec signatur všechny obecné parametry.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat požadovaná velikost metoda `signature` pole, nastavte `cbSignature` argument na hodnotu 0 a `signature` k **hodnotu null**. Po návratu metody `pcbSignature` bude obsahovat počet bajtů požadovaných pro `signature` pole.  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetTypeProps – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)  
 [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
