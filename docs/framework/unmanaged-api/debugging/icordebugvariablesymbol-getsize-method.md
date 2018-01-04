---
title: "ICorDebugVariableSymbol::GetSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99cba63edd56e0d27d5f558a77ee54ebf2629446
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a>ICorDebugVariableSymbol::GetSize – metoda
Získá velikost proměnné v bajtech.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcbValue`  
 Ukazatel 32bitové celé číslo bez znaménka obsahující velikost proměnné.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugVariableSymbol – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
