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
ms.openlocfilehash: 4558074bc23334bd697461a00ccb31db3e3fe397
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130596"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection – metoda
Oznamuje ladicímu programu, že se změnila sada úloh přidružených k zadanému připojení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 pro Ukazatel na objekt "ICorDebugProcess", který představuje proces obsahující připojení, které bylo změněno.  
  
 `dwConnectionId`  
 pro ID připojení, které bylo změněno.  
  
## <a name="remarks"></a>Poznámky  
 Zpětné volání `ChangeConnection` se spustí v jednom z následujících případů:  
  
- Když se ladicí program připojí k procesu, který obsahuje připojení. V tomto případě modul runtime vygeneruje a odešle událost [ICorDebugManagedCallback2:: CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md) a událost `ChangeConnection` pro každé připojení v procesu. Událost `ChangeConnection` se vygeneruje pro každé existující připojení, bez ohledu na to, jestli se od jejího vytvoření změnila sada úkolů daného připojení.  
  
- Když hostitel volá [ICLRDebugManager:: SetConnectionTasks –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md) v [rozhraní API hostování](../../../../docs/framework/unmanaged-api/hosting/index.md).  
  
 Ladicí program by měl zkontrolovat všechny podprocesy v procesu a vybrat nové změny.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
