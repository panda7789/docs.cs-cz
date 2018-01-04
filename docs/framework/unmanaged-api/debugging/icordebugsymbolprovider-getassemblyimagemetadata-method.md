---
title: "ICorDebugSymbolProvider::GetAssemblyImageMetadata – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff6b26dd9a0ed56e5194dc997270cf9d2dbe42b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a>ICorDebugSymbolProvider::GetAssemblyImageMetadata – metoda
Vrátí metadata z sloučené sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppMemoryBuffer`  
 [out] Ukazatel na adresu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) objekt, který obsahuje informace o velikosti a adresu metadata sloučené sestavení.  
  
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
