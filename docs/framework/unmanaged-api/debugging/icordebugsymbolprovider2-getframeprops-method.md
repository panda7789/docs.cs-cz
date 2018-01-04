---
title: "ICorDebugSymbolProvider2::GetFrameProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f74ed8cdd7448d7ebeaa98108e84b42e86f428b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>ICorDebugSymbolProvider2::GetFrameProps – metoda
Vrátí metodu počáteční relativní virtuální adresa metodu a nadřazeného rámce zadaný relativní virtuální adresu kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `codeRva`  
 [v] Kód relativní virtuální adresu.  
  
 `pCodeStartRva`  
 [out] Ukazatel metoda počáteční relativní virtuální adresa.  
  
 `pParentFrameStartRva`  
 [out] Ukazatel na rámečku počáteční relativní virtuální adresa.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugSymbolProvider2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
