---
title: "ICorDebugDataTarget2::GetSymbolProviderForImage – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e802ad662130169d67227803eb017075c94f4361
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a>ICorDebugDataTarget2::GetSymbolProviderForImage – metoda
Vrátí symbol zprostředkovatele pro modul z bázové adresy tohoto modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `imageBaseAddress`  
 [v] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje základní adresu modulu.  
  
 `ppSymProvider`  
 [out] Ukazatel na adresu [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) objektu.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
