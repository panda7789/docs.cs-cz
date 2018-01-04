---
title: "ICorDebugSymbolProvider::GetCodeRange – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0bb2729ee5bc77842f658e38a2afbbb2b24da55
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a>ICorDebugSymbolProvider::GetCodeRange – metoda
Získá metoda počáteční adresy a velikost relativní virtuální adresy (RVA) v metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `codeRva`  
 [v] Relativní virtuální adresa (RVA) v metodě.  
  
 `pCodeStartAddress`  
 [out] Ukazatel na počáteční adresa metody.  
  
 `pCodeSize`  
 Ukazatel na velikosti kódu – metoda (počet bajtů metoda kódu).  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugSymbolProvider – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
