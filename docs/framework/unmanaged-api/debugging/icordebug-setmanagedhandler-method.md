---
title: "ICorDebug::SetManagedHandler – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.SetManagedHandler
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dde32b6a8251474c4254e35a3a1ba3ba3bafcb8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler – metoda
Určuje objekt obslužné rutiny události pro spravované události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [v] Ukazatel na [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) objekt, který je objekt obslužné rutiny událostí.  
  
## <a name="remarks"></a>Poznámky  
 `SetManagedHandler`musí být voláno v okamžiku vytvoření.  
  
 Pokud `ICorDebugManagedCallback` implementace neobsahuje dostatek rozhraní pro zpracování události ladění pro aplikace, která je probíhá ladění, `SetManagedHandler` vrátí HRESULT E_NOINTERFACE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
