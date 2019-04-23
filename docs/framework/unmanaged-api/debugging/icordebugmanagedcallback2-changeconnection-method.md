---
title: ICorDebugManagedCallback2::ChangeConnection – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4eeecc22db5786f66b3d484b521989e71817d8e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185039"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection – metoda
Upozorní ladicího programu, že se změnila sadu úkolů přidružených k zadané připojení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 [in] Ukazatel na objekt "ICorDebugProcess", který reprezentuje proces obsahující připojení, která se změnila.  
  
 `dwConnectionId`  
 [in] ID připojení, která se změnila.  
  
## <a name="remarks"></a>Poznámky  
 A `ChangeConnection` aktivuje zpětného volání v některém z následujících případech:  
  
-   Pokud ladicí program připojí k procesu, který obsahuje připojení. V takovém případě modul runtime bude generovat a odeslání [icordebugmanagedcallback2::createconnection –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) událostí a `ChangeConnection` události pro každé připojení v procesu. A `ChangeConnection` vygenerování události pro každé existující připojení, bez ohledu na to, zda toto připojení sady úloh změnila od jeho vytvoření.  
  
-   Když hostitel volá [iclrdebugmanager::setconnectiontasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) v [API pro hostování](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 Ladicí program byste nechat zkontrolovat všechna vlákna v procesu, aby se získaly nové změny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
