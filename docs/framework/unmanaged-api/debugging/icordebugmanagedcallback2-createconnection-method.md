---
title: "ICorDebugManagedCallback2::CreateConnection – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.CreateConnection
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 716321508c18a415dc8e5c1c3e7e350deaf00a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection – metoda
Upozorní ladicího programu vytvořený nové připojení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProcess`  
 [v] Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém byla vytvořena připojení  
  
 `dwConnectionId`  
 [v] ID nové připojení.  
  
 `pConnName`  
 [v] Ukazatel na název nového připojení.  
  
## <a name="remarks"></a>Poznámky  
 A `CreateConnection` zpětného volání nebudou vydány v některém z následujících případech:  
  
-   Když ladicí program připojí k procesu, který obsahuje připojení. V takovém případě bude modulu runtime generování a odesílání `CreateConnection` událostí a [icordebugmanagedcallback2::changeconnection –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) událost pro každé připojení v procesu.  
  
-   Když hostitel volá [iclrdebugmanager::beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) v [hostování rozhraní API](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback2 – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
