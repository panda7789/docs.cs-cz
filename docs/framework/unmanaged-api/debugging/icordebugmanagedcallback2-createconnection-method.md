---
title: ICorDebugManagedCallback2::CreateConnection – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50e9f3b8271cb5e518b75ee129fe6ea2a1b7720d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512928"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection – metoda
Upozorní ladicího programu, že se vytvořila nová připojení.  
  
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
 [in] Ukazatel na objekt "ICorDebugProcess", který představuje proces, ve kterém byla vytvořena připojení  
  
 `dwConnectionId`  
 [in] ID připojení tímto novým připojením.  
  
 `pConnName`  
 [in] Ukazatel na název připojení tímto novým připojením.  
  
## <a name="remarks"></a>Poznámky  
 A `CreateConnection` aktivuje zpětného volání v některém z následujících případech:  
  
-   Pokud ladicí program připojí k procesu, který obsahuje připojení. V takovém případě modul runtime bude generovat a odeslání `CreateConnection` událostí a [icordebugmanagedcallback2::changeconnection –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md) události pro každé připojení v procesu.  
  
-   Když hostitel volá [iclrdebugmanager::beginconnection –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) v [API pro hostování](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
