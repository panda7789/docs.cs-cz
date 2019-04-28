---
title: ICorDebugManagedCallback2::DestroyConnection – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35ae3a9761798ed9ea42b984f2c6c2cad4e42777
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704099"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a>ICorDebugManagedCallback2::DestroyConnection – metoda
Upozorní ladicího programu, že zadané připojení se ukončilo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 [in] Ukazatel na objekt ICorDebugProcess, který reprezentuje proces obsahující připojení, které se zničil.  
  
 `dwConnectionId`  
 [in] ID připojení, které se zničil.  
  
## <a name="remarks"></a>Poznámky  
 A `DestroyConnection` zpětné volání bude vyvoláno, když volá hostitele [iclrdebugmanager::endconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md) v [API pro hostování](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
